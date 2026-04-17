---
type: source
created: 2026-04-17
updated: 2026-04-17
tags: [cybersecurite, ia, open-source, tokens, proof-of-work]
source-url: "https://www.dbreunig.com/2026/04/14/cybersecurity-is-proof-of-work-now.html"
author: "@DrewBreunig"
published: 2026-04-14
---

# Cybersecurity Looks Like Proof of Work Now

## Résumé

Drew Breunig analyse les implications de Mythos, le LLM de sécurité d'[[anthropic]] non publié, capable de trouver des 0-days à grande échelle. Thèse centrale : la cybersécurité devient une course aux tokens — pour hardener un système, il faut dépenser plus de tokens à trouver des exploits que les attaquants n'en dépenseront pour les exploiter. C'est du proof-of-work appliqué à la sécurité.

## Affirmations clés

- **Mythos** est "strikingly capable at computer security tasks" — confirmé par l'évaluation indépendante de l'AI Security Institute (AISI)
- Mythos complète "The Last Ones" (simulation d'attaque réseau corporate en 32 étapes, 20h pour un humain) dans 3 tentatives sur 10
- Budget : 100M tokens par tentative = $12 500/tentative, $125K pour 10 runs
- **Aucun signe de rendements décroissants** — les modèles continuent à progresser avec plus de budget tokens
- La sécurité se réduit à une équation brutale : dépenser plus de tokens en défense que l'attaquant en attaque
- **L'open source reste critique** : la loi de Linus ("given enough eyeballs, all bugs are shallow") s'étend aux tokens. Les corporations qui investissent pour sécuriser les libs OSS produisent plus de sécurité que ce que ton budget individuel permet
- Contre Karpathy qui propose de "yoink" les dépendances via LLM (réimplémenter plutôt que dépendre) : une implémentation solo sera moins sécurisée qu'une lib OSS massivement auditée
- **Nouveau cycle de dev émergent** : 1) Development (limité par l'humain), 2) Review (async, best practices), 3) Hardening (autonome, limité par le budget tokens)
- "Code remains cheap, unless it needs to be secure"
- Le coût de la sécurité est fixé par la valeur marchande d'un exploit, pas par l'effort de dev

## Entités mentionnées

[[anthropic]], [[drew-breunig]]

## Concepts

[[securite-proof-of-work]], [[securite-infrastructure]], [[open-source-etat]], [[optimisation-couts-ia]]

## Citations notables

> To harden a system we need to spend more tokens discovering exploits than attackers spend exploiting them.

> Code remains cheap, unless it needs to be secure.

> Linus's law that, "given enough eyeballs, all bugs are shallow," expands to include tokens.
