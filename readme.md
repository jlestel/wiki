# LLM Second Brain Agent

Mise en place d'un "second cerveau" piloté par un agent LLM, basé sur l'idée d'Andrej Karpathy.

## Source d'inspiration

Prompt original de Karpathy : https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Cf CLAUDE.md pour les règles détaillées du wiki.

## Utilisation

Avec Obsidian Web Clipper, j'ajoute depuis le browser des sources d'information dans `raw/`.
`/ingest` permet d'ingérer une source dans le wiki, en extrayant les points clés et en les classant dans la hiérarchie du wiki.
C'est ensuite requêtable via /query, et les réponses peuvent être classées comme pages de synthèse avec `/save`.

## Slash commands

Les commandes personnalisées se trouvent dans [`.claude/commands`](./.claude/commands) :

- `/ingest` — ingérer une source depuis `raw/` dans le wiki
- `/lint` — détecter contradictions, orphelins et lacunes
- `/query` — poser une question répondue depuis le wiki
- `/save` — classer la dernière réponse comme page de synthèse

### Autres commandes distinctes du wiki pour l'instant
- `/post <question>` — préparer un post LinkedIn à partir du contenu du wiki
- `/veille [nb_jours]` — lancer la veille tech (7 jours par défaut)
