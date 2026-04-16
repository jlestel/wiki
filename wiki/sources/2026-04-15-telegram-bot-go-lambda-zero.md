---
type: source
created: 2026-04-16
updated: 2026-04-16
tags: [go, aws, serverless, terraform, tutorial]
source-url: "https://medium.com/@n0paleon/i-built-a-multifunctional-telegram-bot-with-go-and-lambda-for-0-forever-28f17bd3ccd7"
author: Muhammad Naufal
published: 2026-04-15
---

# Bot Telegram Go + Lambda à 0$ pour toujours

## Résumé

Blueprint complet pour un bot Telegram gratuit en permanence : Go + AWS Lambda (free tier permanent) + Terraform IaC. Architecture webhook (pas polling) = zéro coût d'idle. Go arm64 (Graviton2) pour cold starts <200ms. Déploiement en une commande.

## Points clés

- Lambda free tier permanent : 1M invocations/mois, 400K GB-s
- Webhook vs polling : Telegram appelle Lambda uniquement quand message arrive
- Go arm64 : binaire 6-10 MB, 20% meilleur prix-perf que x86
- Lambda Function URL (gratuit) vs API Gateway ($1/M requêtes)
- Risque : Function URL publique → solution HTTP API Gateway avec rate limit
- Tout en Terraform, versionné avec le code

## Concepts

[[serverless-zero-cost]], [[infrastructure-as-code]]
