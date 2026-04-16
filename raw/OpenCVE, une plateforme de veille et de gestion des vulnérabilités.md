---
title: "OpenCVE, une plateforme de veille et de gestion des vulnérabilités"
source: "https://domopi.eu/opencve-une-plateforme-de-veille-et-de-gestion-des-vulnerabilites/"
author:
  - "[[Guillaume]]"
published: 2026-03-30
created: 2026-04-16
description: "Des CVE publiées en permanence, impossible de toutes les suivre. OpenCVE filtre ce qui vous concerne et alerte dès qu'une faille touche vos logiciels ou équipements."
tags:
  - "clippings"
---
Nous utilisons tous au quotidien différents matériels, applications ou logiciels. Ces éléments peuvent faire l'objet de failles de sécurité et être potentiellement victimes de tentatives de piratage, que ça soit pour voler des données ou bien extorquer de l'argent. Les constructeurs et fournisseurs publient continuellement des correctifs, mais il est aujourd'hui impossible, sans un outil ou des filtres adaptés, de suivre et d'analyser toutes les vulnérabilités qui sortent chaque jour.

C'est là qu'intervient OpenCVE, une plateforme open-source conçue pour faciliter la gestion et la surveillance des vulnérabilités de sécurité. Cette solution permet à ceux qui le souhaitent, aussi bien aux professionnels de l'informatique qu'aux passionnés de sécurité, de rester informés des menaces potentielles pouvant affecter leurs systèmes.

---

### Mais déjà, qu'est-ce qu'une CVE?

Une CVE (Common Vulnerabilities and Exposures) est un identifiant unique attribué à une faille de sécurité connue. Le format est toujours le même: CVE-ANNÉE-NUMÉRO, par exemple CVE-2021-44228, la célèbre faille Log4Shell. Chaque CVE est accompagnée d'un score CVSS (de 0 à 10) qui évalue sa criticité (plus le score est élevé, plus la faille est dangereuse et potentiellement exploitable).

OpenCVE agrège les données de plusieurs sources pour maintenir à jour sa base locale de CVE, notamment la NVD (National Vulnerability Database), un service du gouvernement américain qui fait référence en matière de données sur les vulnérabilités.  
En France, le CERT-FR est le CERT (Computer Emergency Response Team) ou CSIRT (Computer Security Incident Response Team) Gouvernemental et National Français et traite, sur le plan technique, les incidents de cybersécurité. Le CERT-FR est porté par l'ANSSI.

---

### Comment fonctionne OpenCVE?

OpenCVE interroge régulièrement en arrière-plan ses sources (MITRE, NVD, RedHat…) via des tâches planifiées gérées par Apache Airflow. Quand une nouvelle CVE est publiée ou qu'une existante est mise à jour (score révisé, nouvelles versions affectées, correctif disponible), la base de données est mise à jour et les abonnés concernés sont notifiés, permettant ainsi une veille continue et efficace.

Au-delà de la simple consultation de CVE, OpenCVE propose un système d'abonnement par vendeur ou produit: vous vous abonnez à ce qui vous concerne (Synology, Docker, Nginx, Proxmox…) et vous recevez une alerte dès qu'une nouvelle vulnérabilité est publiée ou mise à jour sur ces éléments.

![](https://domopi.eu/content/images/size/w2400/2026/03/opencve1.webp)

Trois canaux de notification sont disponibles: e-mail, webhook et Slack. Le webhook est particulièrement utile si vous voulez pousser les alertes vers un outil externe (Gotify, Ntfy, ou n'importe quel système qui accepte un POST HTTP). Les filtres permettent d'affiner ce qui déclenche une alerte. On peut par exemple ne recevoir que les CVE avec un score CVSS supérieur à 7, ou uniquement celles qui figurent dans le catalogue KEV de la CISA (ce catalogue recense les vulnérabilités activement exploitées dans la nature, ce qui en fait un bon indicateur de priorité).

La version 2.x a introduit un système d'organisations et de projets. Le modèle est hiérarchique: une organisation contient un ou plusieurs projets, et c'est au niveau du projet que vous définissez vos abonnements et vos règles de notification. Concrètement, pour un homelab, un seul projet suffit. Mais si vous gérez plusieurs environnements distincts, un NAS, un serveur de VMs, un réseau UniFi, les projets permettent de cloisonner les alertes et de ne pas tout mélanger.

---

### Installation

Deux options s'offrent à vous:

- La version SaaS sur [opencve.io](https://www.opencve.io/?ref=domopi.eu), gratuite pour un usage basique, sans rien à installer
- L'auto-hébergement via Docker, pour garder la main sur vos données

Pour l'auto-hébergement, l'installation Docker inclut tout ce qu'il faut: le serveur web Django, Apache Airflow pour la synchronisation des données, Redis et PostgreSQL. Côté ressources, comptez au minimum 4 cœurs, 4 Go de RAM et environ 25-30 Go d'espace disque.

Clonez le dépôt et placez vous dans le répertoire créé:

```bash
git clone https://github.com/opencve/opencve.git && cd opencve/docker
```

Lancez le script d'installation:

```bash
./install.sh
```

Le script `install.sh` orchestre l'ensemble de la mise en place: création des conteneurs, initialisation de la base de données, import de la base de connaissances OpenCVE et création du premier compte administrateur.

![](https://domopi.eu/content/images/2026/03/opencve_install.webp)

Relancez le script d’installation afin de finaliser la mise en place et démarrer les conteneurs:

```bash
./install.sh start
```

Une fois l'installation terminée, l'interface web est accessible sur le port que vous avez défini dans le fichier. La première synchronisation avec les sources de données prend un certain temps (prévoir plusieurs dizaines de minutes selon votre connexion).

![](https://domopi.eu/content/images/2026/03/opencve_docker.webp)

---

### Configuration

La mise en place est rapide. Après la création de votre compte, vous devez créer une organisation, puis un ou plusieurs projets, c'est le prérequis pour pouvoir s'abonner à quoi que ce soit.

Ensuite, direction l'onglet " *Vendors & Products* ": vous recherchez les éditeurs ou logiciels qui vous concernent et vous vous abonnez. Quelques exemples utiles pour un homelab:

- `synology` → DSM et les packages associés
- `docker` → le moteur de conteneurs
- `proxmox` → PVE et PBS
- `nginx` → le reverse proxy
- `ubiquiti` → les équipements UniFi

Les alertes par e-mail sont configurables depuis les paramètres de votre compte. Vous pouvez choisir la fréquence (temps réel ou digest quotidien) et filtrer par niveau de criticité ( pas besoin de recevoir un mail pour chaque CVE de score 2/10).

---

### Conclusion

Honnêtement, j'aurais dû mettre cet article en ligne bien plus tôt, l'outil tourne chez moi depuis un moment et il fait exactement ce qu'il promet. Ce qui m'a le plus surpris, c'est la précision des abonnements: une fois les bons vendeurs configurés, on reçoit les alertes qui nous concernent, pas le flux entier de la NVD.

Pour un homelab, la version SaaS gratuite suffit largement. L'auto-hébergement a du sens si vous voulez tout garder local ou intégrer OpenCVE dans une stack de supervision plus complète via webhooks.

Le projet est actif, la v2 a apporté pas mal de choses utiles (Airflow, multi-sources, organisations), et l'interface s'est bien améliorée. À avoir dans sa boîte à outils si vous gérez une infra, même modeste.

Et vous, vous faites comment pour suivre les failles qui peuvent concerner les services que vous hébergez? Faites-le-nous savoir en commentaire ou venez en discuter sur le [groupe Telegram](https://t.me/domopi_community?ref=domopi.eu).