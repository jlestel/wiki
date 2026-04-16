---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [infrastructure, open-source, devops]
sources: [2026-04-15-liens-tech-avril-2026, 2026-04-15-coolify-alternative-vercel, 2026-03-30-opencve-veille-vulnerabilites]
---

# Self-hosting

Héberger soi-même ses services plutôt que louer une plateforme SaaS.

## Motivations

- Contrôle des données
- Coût : un VPS $5/mois vs $20-500/mois par SaaS
- Zéro vendor lock-in
- Auditabilité

## Stack exemple (avril 2026)

| Besoin | Outil self-hosted |
|--------|-------------------|
| Déploiement | [[coolify]] |
| Notes Markdown | Alexandrie |
| Admin Docker | Dockman |
| Kanban | Planka |
| Backups | Zerobyte (Restic) |
| LLMs | [[ollama]] |
| Veille CVE | OpenCVE |
| Domotique | Home Assistant + C.A.F.E. |

## Lien

- Matériel de [[souverainete-numerique]] à l'échelle individuelle
- S'oppose à la logique de [[delegation-risque-big-tech]]
