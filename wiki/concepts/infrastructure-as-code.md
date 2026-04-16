---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [devops, terraform, automatisation]
sources: [2026-04-15-terraform-gcp-scaling, 2026-04-15-telegram-bot-go-lambda-zero]
---

# Infrastructure as Code (IaC)

Définir l'infrastructure (réseau, compute, IAM) en fichiers versionnés plutôt que via console web.

## Bonnes pratiques (Terraform)

- Structure modulaire, séparation par environnement
- Modules réutilisables (VPC, IAM, GKE) — [[2026-04-15-terraform-gcp-scaling]]
- CI/CD pipeline : validate → plan → approval → apply
- State remote (GCS backend), locking, state séparé par env
- Least privilege IAM, pas de credentials hardcodés

## Cas minimaliste

- Bot Telegram en Terraform : Lambda + Function URL, zéro API Gateway — [[2026-04-15-telegram-bot-go-lambda-zero]]
- Code + infra versionnés ensemble

## Lien

- L'IA aide sur la review Terraform mais « understanding the infrastructure is still key » → [[ia-comme-levier]]
