---
title: "I Built a Multifunctional Telegram Bot With Go and Lambda for $0 Forever"
source: "https://medium.com/@n0paleon/i-built-a-multifunctional-telegram-bot-with-go-and-lambda-for-0-forever-28f17bd3ccd7"
author:
  - "[[Muhammad Naufal]]"
published: 2026-04-15
created: 2026-04-16
description: "I got tired of paying for idle servers just to keep a Telegram bot alive. So I rebuilt it on AWS Lambda with Go and Terraform. It handles real commands, calls external APIs, deploys in one command, and the hosting bill is permanently zero."
tags:
  - "clippings"
---
![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*R7Y3s4W2Wyj-E-Y0v2wyHQ.png)

Webhook-first architecture, Go binaries on Graviton2, and Terraform IaC. Here is the exact blueprint for a bot that never generates a hosting bill.

## The Problem With “Always-On” Bots

Most Telegram bot tutorials teach you to spin up a VPS, run a polling loop, and leave it idling 24/7. That approach works until you check your cloud bill.

The bot sits there consuming CPU and RAM even when nobody is talking to it. You are paying for sleep. That never made sense to me, so I built **CettaTools Telebot**, a multifunctional Telegram bot powered by Go and AWS Lambda. It handles real user commands, calls external APIs, and scales automatically. Hosting cost: **$0. Permanently.**

## The $0 Math First

Before diving into code, let us establish exactly *why* this is free and not just marketing copy.

AWS Lambda’s free tier is **permanent** (not a 12-month trial):

```c
| Resource            | Free Tier Limit              | Typical Bot Usage      |
| ------------------- | ---------------------------- | ---------------------- |
| Lambda Invocations  | 1,000,000 / month            | ~10,000–50,000 / month |
| Lambda Compute      | 400,000 GB-seconds / month   | ~500–5,000 GB-seconds  |
| Lambda Function URL | Free (no API Gateway needed) | Free                   |
| CloudWatch Logs     | 5 GB / month ingestion       | < 1 MB / month         |
```

The key insight: **a Telegram bot is not a web server.** It does not need to run continuously. Most bots are idle 99% of the day. With Lambda, you only pay for the milliseconds it is actually executing.

Even at scale, if your bot processes 1 million messages a month (a very busy bot), with a 512 MB function finishing in ~100ms per invocation, your monthly compute bill is still **$0.00**. You would be consuming roughly 51,200 GB-seconds, well under the 400,000 GB-second threshold.

## Why Webhook Beats Polling (and Saves All the Money)

This is the single most important architectural decision:

- **Polling**: Your bot loops every few seconds asking Telegram “any new messages?” Running 24/7, consuming compute constantly, whether users are active or not.
- **Webhook**: Telegram calls *your endpoint* only when a real message arrives. Lambda wakes up, processes it, and sleeps. Zero idle cost.
```c
User -> Telegram -> Lambda Function URL -> Go Handler -> API Call -> Reply
```

There is no persistent process. No server to keep alive. Telegram sends an HTTP POST to your Lambda Function URL, and Lambda handles the rest. The entire round-trip completes in under 300ms.

This is why the $0 cost is real and sustainable, not a promotional gimmick.

## Why Go + arm64 Compounds the Savings

Go compiles to a single, self-contained binary. No runtime to install, no package manager, no virtual environment. The `bootstrap` binary is typically 6-10 MB after stripping debug symbols.

Combined with Lambda’s `arm64` architecture (AWS Graviton2):

- ~20% better price-performance compared to x86
- Cold starts under 200ms
- Lower memory footprint per invocation

Even if your bot somehow exceeds the free tier someday, Go on `arm64` is the cheapest possible compute profile on Lambda. The cost ceiling is very, very low.

## Project Structure

Here is the repository structure for the Telegram bot I created. The design is very simple but also highly modular, you can customize it however you like:

```c
cettatools-telebot/
├── cmd/
│   └── lambda/
│       └── main.go         # Lambda entrypoint
├── internal/
│   ├── apis/               # External API clients
│   └── handlers/
│       ├── whois_handler.go
│       ├── funfact_handler.go
│       ├── message_router.go
│       └── common_handler.go
├── pkg/
│   └── utils/
├── terraform/              # Infrastructure as Code
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
└── Makefile
```

The `internal/` packages are unexported, keeping business logic encapsulated. Terraform lives alongside the application code so infrastructure and app are versioned together.

## The Lambda Entrypoint

```c
var bot *telego.Bot

func init() {
    token := os.Getenv("TELEGRAM_BOT_TOKEN")
    bot, err = telego.NewBot(token, telego.WithDefaultDebugLogger())
}

func handler(ctx context.Context, request events.LambdaFunctionURLRequest) (events.LambdaFunctionURLResponse, error) {
    var update telego.Update
    if err := json.Unmarshal([]byte(request.Body), &update); err != nil {
        return events.LambdaFunctionURLResponse{StatusCode: 400}, nil
    }

    bh, _ := th.NewBotHandler(bot, nil)

    if update.Message != nil {
        var wg sync.WaitGroup
        wg.Go(func() { handlers.RouteMessage(bh) })
        wg.Wait()
    }

    bh.BaseGroup().HandleUpdate(ctx, bot, update)

    return events.LambdaFunctionURLResponse{
        Body: \`{"message":"OK!"}\`, StatusCode: 200,
    }, nil
}

func main() {
    lambda.Start(handler)
}
```

Two things here that directly support $0 operation:

1. `init()` **runs once per container lifecycle.** The bot client is initialized on cold start and reused across all warm invocations. No wasted initialization cost per request.
2. **Immediate** `200 OK` **response.** Telegram requires a fast acknowledgment. If your handler is too slow, Telegram retries, doubling your invocation count. Respond fast, do heavy work async if needed.

## The Features: Using Free APIs From RapidAPI

For the actual functionality, I needed external data sources. RapidAPI marketplace has a wide catalog of free-tier APIs, so I picked two that fit the use case.

### /whois <domain>

Queries a domain WHOIS API. Returns structured data: registrar, name servers, DNSSEC status, registration and expiry dates. The handler formats it as an HTML-parsed Telegram message, truncated to Telegram’s 4096-character limit.

![](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*yYyrk8zX077P2MPxocyb3A.png)

### /funfact

Calls a fun facts API that returns daily-updated, sourced facts with optional media attachments. The handler detects the media content type and sends it as a photo or video when available, falling back to a plain text message otherwise.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*vTKMWBXM4JtXdu3wR7GIMQ.png)

Both APIs have a free tier that is sufficient for personal and community bot usage. You can add other features to this bot, the code is very simple.

## Infrastructure: Terraform Deploys Everything

No clicking through the AWS console. The entire stack is defined in `terraform/main.tf`:

```c
resource "aws_lambda_function" "main" {
  function_name = var.project_name
  runtime       = "provided.al2023"   # Go custom runtime
  handler       = "bootstrap"
  role          = aws_iam_role.lambda_role.arn

  filename         = "../build/lambda.zip"
  source_code_hash = filebase64sha256("../build/lambda.zip")

  architectures = ["arm64"]           # Graviton2, faster and cheaper
  timeout       = var.lambda_timeout
  memory_size   = var.lambda_memory_size

  environment {
    variables = {
      TELEGRAM_BOT_TOKEN = var.telegram_bot_token
      RAPIDAPI_API_KEY   = var.rapidapi_api_key
    }
  }
}

# Direct HTTPS endpoint, no API Gateway, no extra cost
resource "aws_lambda_function_url" "main" {
  function_name      = aws_lambda_function.main.function_name
  authorization_type = "NONE"
}
```

**Lambda Function URL** is critical here. API Gateway costs at least $1 per million requests. Function URLs are free. For a Telegram webhook endpoint that only accepts bot traffic, Function URLs are clearly the better choice: one fewer service, one fewer cost factor.

That said, Function URL alone still has one open risk. Because the endpoint is publicly accessible with no authentication, anyone who discovers your URL can flood it with requests and spike your invocation count. For most bots this is not an issue in practice, but it is worth knowing the gap exists. I will cover how to close it in the optimization section at the end.

## Build and Deploy: One Command

```c
build: clean
    GOOS=linux GOARCH=arm64 go build \
        -tags lambda.norpc \
        -ldflags="-s -w" \
        -o bootstrap cmd/lambda/main.go
    zip -r build/lambda.zip bootstrap

deploy: build
    terraform -chdir=terraform plan
    terraform -chdir=terraform apply
```

`-ldflags="-s -w"` strips the symbol table and debug info, reducing binary size significantly. `-tags lambda.norpc` disables the RPC interface used for local Lambda testing, trimming more dead code. The result is a lean binary that starts fast and stays within Lambda's deployment limits.

> FYI: You can even reduce the size of the binary file by more than 30% using additional tools like [UPX](https://github.com/upx/upx)

## Deploy It Yourself in 5 Steps

1. **Clone** the repo: `git clone https://github.com/n0paleon/cettatools-telebot`
2. **Create a bot** via [@BotFather](https://t.me/botfather) on Telegram and get your token
3. **Get API keys** by subscribing to free-tier [WHOIS](https://rapidapi.com/cettalabs-technologies-cettalabs-technologies-default/api/whois-api-domain-whois-checker1) and [fun facts APIs](https://rapidapi.com/cettalabs-technologies-cettalabs-technologies-default/api/knowledger-daily-unique-fun-facts) on [rapidapi.com](https://rapidapi.com/)
4. **Configure** by copying `terraform/terraform.tfvars.example` to `terraform.tfvars` and filling in your tokens
5. **Deploy** with `make init && make deploy`, then register the webhook:
```c
curl "https://api.telegram.org/bot<TOKEN>/setWebhook?url=<LAMBDA_FUNCTION_URL>"
```

No server. No monthly invoice.

## Optimizations: Closing the Cost Gap

The setup above runs at $0 for virtually any normal bot workload. But there is one potential cost leak worth patching before you ship to production.

**The problem with a bare Function URL**

Since the Function URL has `authorization_type = "NONE"`, it is open to the public internet. A malicious actor who finds your URL can flood it with fake requests, burning through your free tier invocations and potentially generating real charges. Any rate limiting logic placed *inside* the Lambda handler does not help here, because the function is already executing and the invocation is already being counted by the time your code runs.

The fix needs to happen *before* Lambda is invoked.

**The solution: HTTP API Gateway with a global rate limit**

AWS HTTP API Gateway (not REST API Gateway) sits in front of your Lambda and can reject excess requests before they ever reach your function. It supports a global throttle configuration with two parameters:

```c
resource "aws_apigatewayv2_stage" "default" {
  api_id      = aws_apigatewayv2_api.main.id
  name        = "$default"
  auto_deploy = true

  default_route_settings {
    throttling_burst_limit = 10   # max concurrent spike
    throttling_rate_limit  = 5    # sustained requests per second
  }
}
```

Requests exceeding these limits receive a `429 Too Many Requests` response from API Gateway directly. Lambda is never invoked. No execution, no cost.

The trade-off is that HTTP API Gateway is no longer free. It costs $1.00 per million requests after the first 12 months (it is free during the AWS free tier period). For a Telegram bot, this is still extremely cheap since legitimate traffic volume is low, and you are paying only for real requests that pass the throttle.

Update your Terraform to replace the Function URL with HTTP API Gateway:

```c
# HTTP API Gateway
resource "aws_apigatewayv2_api" "main" {
  name          = "${var.project_name}-api"
  protocol_type = "HTTP"
}

# Lambda integration
resource "aws_apigatewayv2_integration" "lambda" {
  api_id                 = aws_apigatewayv2_api.main.id
  integration_type       = "AWS_PROXY"
  integration_uri        = aws_lambda_function.main.invoke_arn
  payload_format_version = "2.0"
}

# Webhook route
resource "aws_apigatewayv2_route" "webhook" {
  api_id    = aws_apigatewayv2_api.main.id
  route_key = "POST /webhook"
  target    = "integrations/${aws_apigatewayv2_integration.lambda.id}"
}

# Stage with global rate limit
resource "aws_apigatewayv2_stage" "default" {
  api_id      = aws_apigatewayv2_api.main.id
  name        = "$default"
  auto_deploy = true

  default_route_settings {
    throttling_burst_limit = 10
    throttling_rate_limit  = 5
  }
}

# Allow API Gateway to invoke Lambda
resource "aws_lambda_permission" "apigw" {
  statement_id  = "AllowAPIGatewayInvoke"
  action        = "lambda:InvokeFunction"
  function_name = aws_lambda_function.main.function_name
  principal     = "apigateway.amazonaws.com"
  source_arn    = "${aws_apigatewayv2_api.main.execution_arn}/*/*"
}
```

The Telegram webhook URL changes from the Function URL to the API Gateway endpoint:

```c
curl "https://api.telegram.org/bot<TOKEN>/setWebhook\
  ?url=https://<API_GATEWAY_ID>.execute-api.<REGION>.amazonaws.com/webhook"
```

This architecture gives you a real shield against abuse at the infrastructure level, not application level. The $0 bill stays $0 for legitimate usage, and runaway costs from a flooded endpoint are structurally prevented.

## The Architecture Is the Product

The real value here is not the specific commands. It is the pattern. This same architecture works for any Telegram bot use case: notification bots, lookup tools, admin bots, game bots. The template is:

- **Go binary** for fast cold starts and minimal memory
- **Lambda Function URL** as the webhook receiver, no API Gateway
- **arm64 / Graviton2** for the best price-performance on Lambda
- **Terraform** to version-control the infrastructure
- **Free-tier APIs** from RapidAPI for external data

Every piece of this stack is either free by default or optimized to stay within free tier limits. The $0 claim is not an asterisk. It is the design goal from the start.

Check out my Telegram bot: [https://t.me/cettatools\_bot](https://t.me/cettatools_bot)  
Full source code: [https://github.com/n0paleon/cettatools-telebot](https://github.com/n0paleon/cettatools-telebot)