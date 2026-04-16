---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [ia, methodologie, specification, documentation, llm]
sources: [2026-04-16-saying-goodbye-to-agile]
---

# Spec-Driven Development

Retour à la discipline documentaire comme **pilote** du développement logiciel, accéléré par les LLM. Inverse le slogan Agile *« Working software over comprehensive documentation »* en *« Comprehensive documentation creates working software »* ([[lewis-campbell]] — [[2026-04-16-saying-goodbye-to-agile]]).

## Thèse

- Les LLM tolèrent mal l'ambiguïté ; bien spécifier un problème est le levier le plus court vers du code correct
- Ce qui est redécouvert ici est ancien : [[winston-royce]] 1970 disait déjà que documentation, spécification et design sont la **même chose** tant que le code n'a pas commencé
- La doc n'est pas un livrable postérieur au code — elle *est* le design

> Until coding begins these three nouns (documentation, specification, design) denote a single thing. If the documentation is bad the design is bad.
> — Royce 1970

## Pourquoi maintenant

- Les LLM ont rendu le coût marginal du code proche de zéro ; le goulet se déplace en amont
- Écrire une spec claire demande la compétence qui distingue « utiliser l'IA » de « construire avec »
- La spec devient le nouvel artefact de valeur — les lignes de code en sont la compilation

## Connexions au wiki

- [[critique-agile]] : la suite logique, une fois Agile remisé
- [[winston-royce]] : la doctrine d'origine
- [[ia-comme-levier]] : la spec *est* le levier — la force amplifiée est la capacité à spécifier, pas à coder
- [[asymetrie-pensee-ia]] : Dave Rupert — le LLM produit plus vite que la pensée. La spec est la discipline qui rééquilibre cette asymétrie
- [[excellence-artisanale]] : la spec est le dos de la commode du #7 de Jobs — ce qu'on ne voit pas à l'usage mais qui tient la pièce
- [[fondamentaux-cs]] : bien spécifier suppose de connaître data structures / algorithmes / systèmes ; sans ce vocabulaire, la spec reste floue et le LLM produit du bruit

## Tensions productives

> [!question] Tension avec [[automatisation-ia]] (Claude Code Routines, agents autonomes). Un agent qui itère sans spec humaine formelle — auto-prompting, générer ses propres specs — est-ce encore du spec-driven ou un retour masqué à l'ambiguïté ? Le *vibe coding* agentique pourrait être le nouveau Waterfall déguisé.

> [!question] Le risque symétrique : la sur-spécification. Royce prévient déjà qu'une documentation abondante mais fausse est pire qu'absente. Comment calibrer le bon niveau de détail à l'ère LLM ?
