# LLM Second Brain Agent

Mise en place d'un "second cerveau" piloté par un agent LLM, basé sur l'idée d'Andrej Karpathy.

## Source d'inspiration

Prompt original de Karpathy : https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Cf CLAUDE.md pour les règles détaillées du wiki.

## Slash commands

Les commandes personnalisées se trouvent dans [`.claude/commands`](./.claude/commands) :

- `/ingest` — ingérer une source depuis `raw/` dans le wiki
- `/lint` — détecter contradictions, orphelins et lacunes
- `/post <question>` — préparer un post LinkedIn à partir du contenu du wiki
- `/query` — poser une question répondue depuis le wiki
- `/save` — classer la dernière réponse comme page de synthèse
- `/veille [nb_jours]` — lancer la veille tech (7 jours par défaut)
