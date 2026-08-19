# Fabrica-plugins — Worker Instructions (AGENTS.md)

## What This Folder Is

This is the **Fabrica plugin marketplace** — a JSON registry of available plugins for the Fabrica desktop app. You are a worker dispatched by the top-level orchestrator to complete a task in this repo.

## What You Should Know

- Plugin repos live under `Auto-Scalers/` GitHub org
- Each plugin is a standalone GitHub repo, added as a submodule here
- Marketplace index: `fabrica-marketplace.json` (app fetches this at startup)
- Kill list: managed by the app, this repo provides the JSON format

## Plugin Manifest Format

Each plugin has a `fabrica-plugin.json` (was `orca-plugin.json`) with:
- `id`, `name`, `version`, `description`
- `engines: { fabrica: ">=1.0.0" }` (was `engines.orca`)
- `publisher: { name: "autoscalers" }` (was `stablyai`)

## What You Do NOT Do

- **Do NOT edit** `.backup/` or `_sources/` — frozen reference copies
- **Do NOT commit or push** — make changes only, orchestrator handles git
- **Do NOT modify plugin submodule contents** — only the marketplace index and docs

## Key Files

```
fabrica-marketplace.json    — Main marketplace index (JSON)
.gitmodules                 — Submodule references to plugin repos
.Fabrica-plugins-board/     — Task file and planning docs
fabrica-*/                  — Plugin repos (submodules)
```

## Task File

Your task file is `.Fabrica-plugins-board/Fabrica-plugins-tasks.md` — the single source of truth for all plugin work.

## How to Send Results

When your task is complete, send `worker_done`:

```bash
orca orchestration send --type worker_done --subject "Task complete" --body "Summary of what was done" --task-id <task_id> --dispatch-id <dispatch_id> --outcome succeeded --files-modified "path/a,path/b" --json
```

If blocked:
```bash
orca orchestration send --type escalation --subject "Blocked" --body "What happened and what's needed" --task-id <task_id> --dispatch-id <dispatch_id> --json
```
