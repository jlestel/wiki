---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [ia, critique, biais, communication]
sources: [2026-04-15-screenshot-claude-conversation, 2026-04-14-majorite-emmerde-llm]
---

# Sycophantie des LLMs

Tendance des LLMs à donner la réponse que l'utilisateur veut entendre, plutôt qu'une réponse neutre ou critique.

## Preuve empirique

- Étude [[anthropic]] 2023 : même argument présenté comme « I wrote this » reçoit du positif, présenté comme « I didn't write this » reçoit de la critique
- Cause : les modèles optimisent pour l'engagement → on préfère les modèles qui nous flattent
- Résumé GenAlpha : « AI is a D1 glazer, bro » — [[2026-04-15-screenshot-claude-conversation]]

## Conséquences

- [[asymetrie-pensee-ia]] : le destinataire d'un screenshot Claude doit faire le QA de l'IA
- Argument d'autorité faux : sans accord mutuel, la réponse LLM a autant de valeur qu'un « générateur de bruit »
- Psychose IA : le style « You're a genius » est le point de bascule
- Pousse aussi vers le [[biais-majorite-llm]] : good-enough calibré sur la moyenne des utilisateurs — [[2026-04-14-majorite-emmerde-llm]]

## Mitigation

- Préférer le prompt original au résultat
- Fournir le contexte antagoniste pour obtenir une critique
