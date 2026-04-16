---
title: "Liens Tech - Avril 2026"
source: "https://domopi.eu/liens-tech-avril-2026/"
author:
  - "[[Guillaume]]"
published: 2026-04-15
created: 2026-04-16
description: "La sélection d'avril : notes Markdown, gestion Docker, Kanban, des sauvegardes Restic, LLM local et un éditeur visuel pour Home Assistant."
tags:
  - "clippings"
---
Liens Tech, c’est notre façon de partager ce qu'on découvre au fil de nos explorations: des outils, projets et ressources qui nous ont intrigué, simplifié la vie ou simplement donné envie d’expérimenter. Une veille sans prétention, juste le plaisir de chercher, tester et partager ce qui vaut le détour.  
Voici notre sélection du mois.

---

## Alexandrie

*Présentation*: Alexandrie est une application web open source de prise de notes en Markdown, pensée pour organiser une base de connaissances avec workspaces/catégories (et une syntaxe Markdown étendue), le tout avec une interface moderne. Elle est conçue pour être auto-hébergée facilement, notamment via Docker, pour garder la main sur ses données.

*Avis*: Je trouve Alexandrie super intéressant pour ceux qui cherchent un “Notion-like” plus léger et auto-hébergeable, avec un vrai focus sur l’écriture et la navigation rapide plutôt que sur le côté usine à gaz.

---

## Dockman

*Présentation*: Dockman est une interface web d’administration pour Docker, conçue pour piloter rapidement des conteneurs et services: démarrage/arrêt, redémarrage, consultation des logs, et suivi de l’état. L’outil met l’accent sur une approche légère et opérationnelle, avec une vue synthétique des ressources (CPU/RAM) et des principaux éléments d’exploitation (ports, volumes, variables d’environnement selon les vues proposées).

*Avis*: Dockman va à l’essentiel, sans la couche “tout-en-un” d’outils plus complets comme Portainer.

---

## Planka

*Présentation*: Planka est un outil de gestion de projets type Kanban, proche de Trello: projets/boards/listes/cartes, gestion multi-utilisateurs et collaboration en temps réel, descriptions en Markdown, catégories,....

*Avis*: Installé depuis peu pour nous aider dans la gestion du blog, Planka est devenu indispensable pour nous permettre de mettre en commun nos idées d'articles et d'en suivre l'avancement, ou encore de référencer la longue liste des outils qu'on souhaite partager dans les Liens Tech.

---

## Zerobyte

*Présentation*: Zerobyte est une couche d’automatisation de sauvegarde construite au-dessus de Restic, avec une interface web pour planifier, gérer et superviser des backups chiffrés vers différents backends. Son principal atout est de rendre Restic plus simple à piloter (jobs, suivi, monitoring) tout en conservant sa solidité.

*Avis*: Très pratique pour mettre en place des sauvegardes sans multiplier les scripts et les crons, ainsi que pour suivre facilement leur bonne exécution.

---

## Ollama

*Présentation*: Ollama est un outil qui permet d’exécuter facilement des modèles de langage en local, sur macOS, Linux ou Windows, tout en exposant une API très simple à intégrer dans ses propres scripts ou applications. Il prend en charge une large bibliothèque de modèles et facilite autant les usages “chat” que les intégrations plus poussées en Python, JavaScript ou via API REST locale. C’est typiquement le genre d’outil très pratique pour expérimenter avec l’IA chez soi, garder la main sur ses données, et construire des workflows sans dépendre uniquement d’un service cloud.

*Avis*: J’aime beaucoup l’approche d’Ollama, qui rend l’usage des LLM locaux beaucoup plus accessible qu’avant. Là où il est particulièrement intéressant, c’est qu’il ne se limite pas à “faire tourner un modèle”: il sert aussi de brique technique simple à brancher dans un homelab, un outil maison ou une automatisation plus large.

Et si vous l'avez loupé, n'hésitez pas à aller lire l'article dédié à son installation et utilisation.

---

## C.A.F.E. éditeur visuel pour automatisations de HA

C.A.F.E. (Complex Automation Flow Editor) ajoute dans Home Assistant un éditeur visuel “en flow” façon Node-RED, sans moteur externe: on construit les automatisations en blocs, et l’outil les compile en YAML 100% natif, enregistré directement dans HA. Il peut aussi ouvrir une automatisation YAML existante et la retransformer en diagramme, ce qui facilite la relecture et la maintenance des scénarios complexes. L’exécution reste déboguable avec les outils Home Assistant (notamment la Trace View), puisque le résultat final est une automatisation native.

---

Merci de votre lecture, n'hésitez pas à partager vos propres découvertes dans les commentaires ou nous rejoindre sur [la communauté Telegram](https://t.me/domopi_community?ref=domopi.eu) et à nous faire part de vos retours pour nous aider à améliorer cette rubrique au fil du temps.

Restez connectés et à très bientôt pour notre prochaine sélection de liens tech!