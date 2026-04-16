# Tuto Obsidian — LLM Wiki Agent

Mise en place d'un "second cerveau" piloté par un agent LLM, basé sur l'idée d'Andrej Karpathy.

## Source d'inspiration

Prompt original de Karpathy : https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

## Prompt de démarrage

À coller dans Claude Code pour initialiser le wiki :

> You are now my LLM Wiki agent. Implement this exact idea file as my complete second brain. Guide me step-by-step: create the CLAUDE.md schema file with full rules, set up index.md and log.md, define folder conventions, and show me the first ingest example.
>
> From now on, every interaction follows the schema.

## Slash commands

Les commandes personnalisées se trouvent dans [`.claude/commands`](./.claude/commands) :

- `/ingest` — ingérer une source depuis `raw/` dans le wiki
- `/lint` — détecter contradictions, orphelins et lacunes
- `/query` — poser une question répondue depuis le wiki
- `/save` — classer la dernière réponse comme page de synthèse
