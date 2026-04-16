---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [aws, serverless, optimisation, devops]
sources: [2026-04-15-telegram-bot-go-lambda-zero]
---

# Serverless à coût zéro

Pattern pour construire des applications permanentes à coût opérationnel nul.

## Ingrédients

- **AWS Lambda free tier permanent** : 1M invocations/mois, 400K GB-s — pas un trial
- **Webhook > polling** : ne consomme du compute que quand un message arrive
- **Go + arm64 (Graviton2)** : binaire 6-10 MB, cold starts <200ms
- **Lambda Function URL** : gratuit vs $1/M requêtes pour API Gateway
- **APIs tiers en free tier** (RapidAPI)

## Maths

- Bot à 1M messages/mois, 100ms/invocation : 51 200 GB-s << 400 000 GB-s
- Coût : $0.00/mois — [[2026-04-15-telegram-bot-go-lambda-zero]]

## Risque : Function URL public

- Sans authentification, flood possible sur l'URL
- Fix : HTTP API Gateway avec rate limit (throttle avant Lambda)
