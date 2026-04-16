---
type: source
created: 2026-04-16
updated: 2026-04-16
tags: [ia, devops, automatisation, claude]
source-url: "https://code.claude.com/docs/en/routines"
published: 2026-04-16
---

# Claude Code Routines — automatisation cloud

## Résumé

Documentation officielle des Routines [[claude-code]] : configurations sauvegardées (prompt + repos + connecteurs) qui s'exécutent automatiquement sur l'infra cloud d'[[anthropic]]. Trois types de triggers : scheduled, API, GitHub events. Fonctionne quand le laptop est fermé.

## Cas d'usage

- Maintenance backlog (triage issues nuit)
- Triage d'alertes (stack trace → PR corrective)
- Code review sur mesure (PR opened → checklist)
- Vérification post-deploy (smoke tests)
- Détection de docs obsolètes (weekly scan)
- Port de bibliothèque entre SDKs

## Points techniques

- Exécution autonome sans prompt d'approbation
- Triggers combinables sur une même routine
- Création via web, CLI (`/schedule`), ou Desktop
- Plans Pro, Max, Team, Enterprise
- Branches limitées à `claude/` par défaut

## Entités

[[anthropic]], [[claude-code]]

## Concepts

[[automatisation-ia]], [[devops-ia]]
