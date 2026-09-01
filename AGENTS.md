# Fabrica-plugins — Worker Instructions (AGENTS.md)

## What This Folder Is

This is the **Fabrica plugin marketplace** — a JSON registry of available plugins for the Fabrica desktop app. You are a worker dispatched by the top-level orchestrator to complete a task in this repo.

## What You Should Know

- Plugin repos live under `Auto-Scalers/` GitHub org
- Each plugin is a standalone GitHub repo, added as a submodule here
- Marketplace index: `fabrica-marketplace.json` (app fetches this at startup)
- Kill list: managed by the app, this repo provides the JSON format

## Current Plugins

| Plugin | Category | Bundled |
|--------|----------|---------|
| `fabrica-portuguese` | languages | No |
| `fabrica-multipass-recipes` | vm-recipes | No |
| `fabrica-navigation-shortcuts` | keybindings | Yes |

## Tech Stack

- Plain JSON (`fabrica-marketplace.json`, kill-list format) — no build step
- Git submodules for plugin repos
- Markdown docs in `.Fabrica-plugins-board/`

## Commands

No build or test tooling. Before claiming DONE:

- Validate `fabrica-marketplace.json` parses as JSON (e.g. `node -e "JSON.parse(require('fs').readFileSync('fabrica-marketplace.json','utf8'))"`).
- Confirm no `orca`/`stablyai` leftovers outside `_sources/` and historical notes.
- Confirm every marketplace entry matches the manifest schema documented in the board.

## Plugin Manifest Format

Each plugin has a `fabrica-plugin.json` with:
- `id`, `name`, `version`, `description`
- `engines: { fabrica: ">=1.0.0" }`
- `publisher: { name: "autoscalers" }`

## Definition of Done

A task is DONE only when ALL of these hold:

1. **JSON valid:** `fabrica-marketplace.json` (or the kill-list format) parses cleanly and follows the documented schema.
2. **No Orca/Stably leftovers** outside `_sources/` and historical notes.
3. **Tracking files updated in the same edit:** task status + Rollup recount in `.Fabrica-plugins-board/Fabrica-plugins-tasks.md`, Checkpoint table, Session Ledger row.

## What You Do NOT Do

- **Do NOT edit** `.backup/` or `_sources/` — frozen reference copies
- **Do NOT commit or push** — make changes only, orchestrator handles git
- **Do NOT modify plugin submodule contents** — only the marketplace index and docs

## Key Files

```
fabrica-marketplace.json          — Main marketplace index (JSON)
.gitmodules                       — Submodule references to plugin repos
.Fabrica-plugins-board/           — Task file and planning docs
fabrica-portuguese/               — Portuguese language plugin
fabrica-multipass-recipes/        — Multipass recipes plugin
fabrica-navigation-shortcuts/     — Navigation shortcuts plugin (bundled)
```

## Parallelism & Anti-Overlap Policy

> This project runs REAL 24/7 multi-terminal orchestration. Parallelism is the
> default: unlimited tokens, multi-terminal app, massive project, close deadline.

- **Minimum fleet:** the orchestrator keeps AT LEAST 3 active worker terminals at
  all times. Fewer than 3 on resume or cycle end => launching more comes FIRST,
  chosen from the highest-priority TODO/VERIFY tasks in this file, focused on
  high-level goals and principles, not micro-edits.
- **One task = one worker:** claim a task by setting its status IN_PROGRESS and
  recording your terminal handle in the Session Ledger BEFORE starting. Claimed
  tasks are forbidden to everyone else.
- **One folder = one orchestrator:** never work another slot's folder.
- **One file = one writer:** two live workers never edit the same file; such tasks
  run sequentially.
- **Claim-before-work:** confirm your Task ID is still unclaimed before executing;
  if done or claimed, stop and report instead of duplicating.
- **Cross-project dependencies:** record them as notes in the OTHER project's task
  file; never edit another project directly.
- **Quality bar unchanged under deadline pressure:** no DONE without verified
  evidence; status change and Rollup update happen in the same edit.

## Task File

Your task file is `.Fabrica-plugins-board/Fabrica-plugins-tasks.md` — the single source of truth for all plugin work. Schema for all tracking edits: `.Fabrica-board/Fabrica-Schema.md` (Tracking Schema v1 — status enum, Rollup, Checkpoint, Session Ledger).

## Resume Protocol

On heartbeat kick or session resume:

1. Read your task file's **Checkpoint (Current State)** table FIRST.
2. Continue from the **Next Action** cell — never restart completed work; check Status + Notes before dispatching.
3. Any status change updates the Rollup in the same edit.

## How to Send Results

When your task is complete, send `worker_done`:

```bash
orca orchestration send --type worker_done --subject "Task complete" --body "Summary of what was done" --task-id <task_id> --dispatch-id <dispatch_id> --outcome succeeded --files-modified "path/a,path/b" --json
```

If blocked:
```bash
orca orchestration send --type escalation --subject "Blocked" --body "What happened and what's needed" --task-id <task_id> --dispatch-id <dispatch_id> --json
```

## Orchestration IDs

Your task file's Session Ledger tracks these IDs for every worker session:

| ID | Format | When You Get It | How to Use It |
|----|--------|-----------------|---------------|
| `task_xxx` | `task_` + hex | `task-create --json` → `result.task.id` | Resume a stuck worker: `worker-start --task <task_id> --retry-of <dispatch_id>` |
| `ctx_xxx` | `ctx_` + hex | `worker-start --json` → `result.dispatchId` | Read worker output: `worker-read --dispatch <ctx_xxx>`. Resume: `--retry-of <ctx_xxx>` |
| `term_xxx` | `term_` + uuid | `worker-start --json` → `effects[terminal].id` | Send message to worker: `terminal send --terminal <term_xxx>`. Read output: `terminal read --terminal <term_xxx>` |
