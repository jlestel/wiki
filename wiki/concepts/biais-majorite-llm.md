---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [ia, critique, qualite-donnees]
sources: [2026-04-14-majorite-emmerde-llm]
---

# Biais de la majorité dans les LLMs

Les LLMs produisent du « good-enough » calibré sur les pratiques majoritaires, au détriment des approches minoritaires — même quand celles-ci sont meilleures.

## Mécanisme

- Les LLMs prédisent statistiquement le prochain token
- Les données d'entraînement surreprésentent le contenu mainstream (cloud-native, JavaScript, React…)
- Le contenu expert (articles scientifiques, blogs techniques) est noyé dans le good-enough
- 90% des utilisateurs veulent du good-enough → les 10% restants se battent contre les biais — [[2026-04-14-majorite-emmerde-llm]]

## Exemple

- Un adminsys « une machine = une mission » est une **curiosité** pour ChatGPT
- Demande « installer un service sans l'exposer » → ChatGPT comprend « localhost » car 90% de ses utilisateurs sont cloud-natives
- Les instructions correctrices (AGENTS.md) brûlent des tokens pour rétablir la vérité

## Conséquence systémique

- Les pratiques minoritaires (Merise, UML, adminsys classique) risquent l'**extinction dans les modèles**
- Plus ces pratiques sont diluées, moins elles sont économiquement rentables à conserver
- Boucle d'appauvrissement : l'intelligence globale se nivelle par le bas

## Lien

- Forme systémique de la [[sycophantie-llm]]
- Argument pour maîtriser les [[fondamentaux-cs]] plutôt que subir les suggestions IA
- Rejoint la critique [[ia-comme-levier]] : sans expertise pour corriger, le levier amplifie les biais
