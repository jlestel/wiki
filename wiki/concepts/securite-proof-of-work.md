---
type: concept
created: 2026-04-17
updated: 2026-04-17
tags: [cybersecurite, ia, tokens, economie]
sources: [2026-04-14-cybersecurity-proof-of-work]
---

# Sécurité comme proof-of-work

La cybersécurité à l'ère des LLM se réduit à une course aux tokens : pour hardener un système, il faut dépenser plus de tokens en défense que les attaquants n'en dépenseront en attaque.

## Mécanisme

- Les LLM de sécurité (Mythos d'[[anthropic]]) trouvent des exploits en brute-forçant les systèmes avec des millions de tokens
- Aucun rendement décroissant observé : plus de tokens = plus d'exploits trouvés
- Le coût de sécurisation est fixé par la **valeur marchande d'un exploit**, pas par l'effort de développement
- Analogie directe avec le proof-of-work crypto : on ne gagne pas en étant malin, on gagne en payant plus

## Cycle émergent de développement sécurisé

1. **Development** — itération rapide, limité par l'intuition humaine
2. **Review** — refactoring, documentation, bonnes pratiques (async)
3. **Hardening** — recherche autonome d'exploits, limité par le budget tokens

L'input humain est le facteur limitant de la phase 1. L'argent est le facteur limitant de la phase 3. — [[2026-04-14-cybersecurity-proof-of-work]]

## Implications

- Le code est cheap, **sauf s'il doit être sécurisé** — la sécurité réintroduit un coût structurel
- L'open source est renforcé : la loi de Linus ("enough eyeballs") s'étend aux tokens. Les libs OSS massivement auditées battent les réimplémentations solo — voir [[open-source-etat]]
- Les petits projets/individus sont structurellement désavantagés en sécurité — tension avec [[democratisation-ia]]

## Lien avec le wiki

- [[securite-infrastructure]] — la veille CVE devient un sous-ensemble du problème
- [[optimisation-couts-ia]] — les tokens de sécurité s'ajoutent aux tokens de dev et d'inférence
- [[rentabilite-ia]] — la sécurité comme coût caché des applications IA

> [!question] Si la sécurité est une course aux tokens, les startups et les projets open source communautaires peuvent-ils rester compétitifs face aux budgets des big tech ?
