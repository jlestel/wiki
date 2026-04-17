---
type: concept
created: 2026-04-16
updated: 2026-04-16
tags: [securite, devops, veille]
sources: [2026-03-30-opencve-veille-vulnerabilites]
---

# Sécurité d'infrastructure — veille CVE

## Concepts de base

- **CVE** (Common Vulnerabilities and Exposures) : identifiant unique par faille, format `CVE-ANNÉE-NUMÉRO`
- **CVSS** : score 0-10 de criticité
- **KEV** (CISA) : catalogue des vulnérabilités activement exploitées dans la nature
- **NVD** : National Vulnerability Database (gouv. US)
- **CERT-FR** : porté par l'[[anssi]]

## OpenCVE

Plateforme open source pour s'abonner à des vendeurs/produits spécifiques et recevoir des alertes filtrées par score ou catalogue KEV — [[2026-03-30-opencve-veille-vulnerabilites]]

## Sécurité à l'ère LLM

- La cybersécurité devient une course aux tokens : pour hardener un système, il faut dépenser plus de tokens que l'attaquant — voir [[securite-proof-of-work]]
- Mythos ([[anthropic]]) trouve des 0-days de manière autonome, validé par l'AISI — [[2026-04-14-cybersecurity-proof-of-work]]
- La veille CVE traditionnelle devient un sous-ensemble du problème : le hardening automatisé par LLM couvre un spectre plus large

## Lien

- S'inscrit dans [[self-hosting]] et [[souverainete-numerique]] (infrastructure maîtrisée = sécurité maîtrisée)
- Voir aussi [[securite-proof-of-work]] pour la dimension économique (tokens comme coût de sécurité)
