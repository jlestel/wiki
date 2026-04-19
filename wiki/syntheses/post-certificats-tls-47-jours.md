---
type: synthesis
created: 2026-04-19
updated: 2026-04-19
tags: [post-linkedin, securite, infrastructure, open-source, automatisation]
sources: [2026-03-30-opencve-veille-vulnerabilites, 2026-04-15-coolify-alternative-vercel, 2026-04-14-cybersecurity-proof-of-work]
---

# Post LinkedIn — En 2026, renouveler ses certificats TLS à la main, c'est terminé

Post sur le ballot SC-081 du CA/Browser Forum : réduction progressive de la durée de vie des certificats TLS de 398 à 47 jours d'ici 2029. Thèse : l'automatisation via ACME et les outils open source (Caddy, Traefik, Certbot) n'est plus optionnelle.

---

**En 2026, renouveler ses certificats TLS à la main, c'est terminé.**

Le 15 mars, le CA/Browser Forum a activé la première étape du ballot SC-081 : durée de vie maximale d'un certificat passée de 398 à 200 jours. Puis 100 jours en 2027. Et 47 jours en 2029. Renouvellement toutes les 6 semaines. Vote unanime des navigateurs : Apple, Google, Microsoft, Mozilla.

**Pourquoi ?** Un certificat longue durée, c'est une clé privée qui traîne. Plus elle traîne, plus la fenêtre d'exploitation est large. À 47 jours, on applique aux certificats la même hygiène qu'aux tokens API : rotation courte, exposition minimale.

**Le problème :** combien de DSI gèrent encore leurs certificats dans un tableur Excel, renouvelés manuellement 3 jours avant expiration ? À 398 jours, c'était pénible mais viable. Un parc de 200 certificats à 47 jours, c'est 1 500 renouvellements par an. Aucun humain ne tient ce rythme.

**La solution existe depuis 2015.** Le protocole ACME, conçu pour Let's Encrypt, automatise tout le cycle : émission, renouvellement, révocation. Zéro intervention humaine. Le CA/Browser Forum ne fait que généraliser ce que Let's Encrypt avait compris il y a 11 ans.

**Les outils open source sont matures.** Caddy active HTTPS par défaut — zéro config. Traefik intègre ACME nativement. Certbot reste fiable pour Nginx. Même Nginx supporte ACME depuis 2025. Tous gratuits, audités, battle-tested.

Un certificat géré par ACME sur un Caddy self-hosted à 5€/mois est plus résilient qu'un wildcard à 300€ renouvelé à la main.

**Par où commencer ?** Inventoriez vos certificats. Testez Caddy ou Traefik sur un env non-critique. Planifiez avant mars 2027. Ça semble loin. Ce n'est pas loin.

Le vrai risque en 2026, ce n'est pas l'automatisation. C'est de ne pas automatiser.

## References

- [[securite-infrastructure]]
- [[securite-proof-of-work]]
- [[self-hosting]]
- [[open-source-etat]]
- [[infrastructure-as-code]]
- [[souverainete-numerique]]
- [[coolify]]
- [[2026-04-15-coolify-alternative-vercel]]
- [[2026-03-30-opencve-veille-vulnerabilites]]
- [[2026-04-14-cybersecurity-proof-of-work]]
