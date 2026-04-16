---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [ia, devops, automatisation]
sources: [2026-04-16-claude-code-routines]
---

# Automatisation par agents IA

Exécution autonome de tâches de développement par des agents IA, sur infrastructure cloud persistante.

## Exemples

- [[claude-code]] Routines : triage backlog, alert triage, code review sur PR, deploy verification — [[2026-04-16-claude-code-routines]]
- Triggers : scheduled, API (HTTP POST), GitHub events

## Implications

- Disparition de la distinction « humain qui code / humain qui reviewe » → l'agent fait les deux
- Nouveau vecteur de risque : l'agent a accès à la production via preferred branch pushes
- Extension logique de la thèse [[ia-comme-levier]] : un développeur orchestre N agents
