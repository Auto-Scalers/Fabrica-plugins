# Fabrica-plugins — Tasks

> Single source of truth for plugin marketplace work. The Roadmap (`.Fabrica-Board/Fabrica-Roadmap.md`) tracks cross-cutting status only — this file owns execution details.
>
> Schema compliance: `.Fabrica-board/Fabrica-Schema.md` (Fabrica Tracking Schema v1).

## High-Level Goals

> WHAT THIS PROJECT IS FOR — read this before any task:

1. **A trustworthy marketplace index.** The JSON registry the Fabrica app fetches at startup stays accurate, validated, and free of dead/malicious plugins.
2. **Zero-friction submissions.** Clear manifest schema, validation rules, review process, and kill-list management so third-party plugins are safe to install.
3. **Beta-launch ready.** Marketplace live and consumable by the app end-to-end (loader + updates verified in Fabrica-app) — gate for Roadmap Phase B.

---

## Rollup

| Metric | Value |
|---|---|
| Total tasks | 18 |
| ✅ DONE | 18 |
| 🔶 IN_PROGRESS | 0 |
| 👀 VERIFY | 0 |
| ⬜ TODO | 0 |
| 🚫 BLOCKED | 0 |
| ❌ CANCELLED | 0 |
| Completion | 100% |

_Last recount: 2026-08-31 (cleanup. Removed 5 unsupported plugins: midnight-theme, nord-theme, solarized-terminal, minimal-icons, workflow-skills. Deleted GitHub repos. Updated marketplace to 3 plugins.)_

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

---

## Group 1 — Orca Source Study

> WHAT THIS GROUP DOES:
> - Clone and study the original Orca plugin repos to understand structure before building Fabrica equivalents.
> WHAT THIS GROUP DOES NOT DO:
> - Build any Fabrica plugin code itself.

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P0a | Clone `stablyai/orca-plugins` into `_sources/orca-plugins/` | ✅ DONE | Cloned to `_sources/orca-plugins/` |
| PLG-P0b | Clone bundled plugin repos into `_sources/` | ✅ DONE | Cloned: `orca-portuguese`, `orca-navigation-shortcuts`, `orca-multipass-recipes` |
| PLG-P0c | Study marketplace index format from cloned repo | ✅ DONE | Schema documented in `.Fabrica-plugins-board/P0-source-study.md` |
| PLG-P0d | Study bundled plugin manifest format | ✅ DONE | `orca-plugin.json` format documented in `.Fabrica-plugins-board/P0-source-study.md` |
| PLG-P0e | Document rename strategy | ✅ DONE | Rename strategy documented in `.Fabrica-plugins-board/P0-source-study.md` |

---

## Group 2 — Marketplace Index

> WHAT THIS GROUP DOES:
> - Owns the marketplace index JSON that the Fabrica app fetches at startup.
> WHAT THIS GROUP DOES NOT DO:
> - Owns nothing related to plugin runtime loading (see Group 5).

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P1 | Initialize marketplace index JSON | ✅ DONE | `fabrica-marketplace.json` created with 3 bundled plugins (portuguese, multipass-recipes, navigation-shortcuts). |
| PLG-P2 | Add bundled plugins to index | ✅ DONE | All 3 bundled plugins verified present in `fabrica-marketplace.json`. |
| PLG-P3 | Plugin submission guidelines | ✅ DONE | Documented in `.Fabrica-plugins-board/P3-plugin-submission-guidelines.md`. |

---

## Group 3 — Plugin Schema

> WHAT THIS GROUP DOES:
> - Defines the plugin manifest format and validation rules for submitted plugins.
> WHAT THIS GROUP DOES NOT DO:
> - Implements validation tooling inside the app.

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P4 | Define plugin manifest schema | ✅ DONE | `fabrica-plugin.json` schema documented in `.Fabrica-plugins-board/P4-plugin-manifest-schema.md`. |
| PLG-P5 | Plugin validation rules | ✅ DONE | Documented in `.Fabrica-plugins-board/P5-plugin-validation-rules.md`. |

---

## Group 4 — Quality & Trust

> WHAT THIS GROUP DOES:
> - Review process, kill-list management, and plugin signing posture.
> WHAT THIS GROUP DOES NOT DO:
> - Runtime enforcement of signing (app-side concern).

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P6 | Plugin review process | ✅ DONE | Documented in `.Fabrica-plugins-board/P6-plugin-review-process.md`. |
| PLG-P7 | Kill-list management | ✅ DONE | Documented in `.Fabrica-plugins-board/P7-kill-list-management.md`. |
| PLG-P8 | Plugin signing (future) | ✅ DONE | Research complete. Orca never signed plugins (SHA-256 content hashing + GitHub provenance). Recommendation: zero-cost Tier-1 baseline (signed Git tags + GPG keys + SHA-256 in marketplace). Apple Dev Program ($99/yr) is hard blocker for macOS. Report: `.Fabrica-plugins-board/P8-plugin-signing-research.md` |

---

## Group 5 — App Integration

> WHAT THIS GROUP DOES:
> - Covers marketplace consumption by the Fabrica app: loader, updates.
> WHAT THIS GROUP DOES NOT DO:
> - Changes to app code itself live in the Fabrica-app tracking files.

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P9 | Plugin loader reads from marketplace | ✅ DONE | Already fully implemented — marketplace fetches via Git clone, caches snapshots, bundles bootstrap to filesystem, discovery finds them, IPC handlers registered, startup wires it all. Verified by audit in Fabrica-app. |
| PLG-P10 | Plugin update mechanism | ✅ DONE | Already fully wired — previewMarketplaceUpdate, "Check for update" button, installMarketplacePlugin IPC with rollback, seedOfficialSource on startup. Verified by audit. |

---

## Group 6 — Plugin Rebrand (Orca → Fabrica)

> WHAT THIS GROUP DOES:
> - Rebrand plugin submodule content from Orca to Fabrica: locale files, recipes.
> WHAT THIS GROUP DOES NOT DO:
> - App source code changes (handled by Fabrica-app tasks).

| # | Task | Status | Output/Notes |
|---|------|--------|--------------|
| PLG-P11 | Rebrand `fabrica-portuguese/locales/pt-BR.json` | ✅ DONE | 748 product-name occurrences replaced: Orca→Fabrica (634), ORCA→FABRICA (26), orca→fabrica (69), github.com/stablyai/orca→github.com/Auto-Scalers/Fabrica. Zero remaining in values. JSON validated. |
| PLG-P12 | Rebrand `fabrica-portuguese/README.md` | ✅ DONE | Title, URL, repo ref, all Orca references→Fabrica. Zero remaining. |
| PLG-P14 | Rebrand `fabrica-multipass-recipes/recipes/ubuntu-lts.json` | ✅ DONE | `$ORCA_VM_NAME`→`FABRICA_VM_NAME` (4 occurrences). Would have broken VM lifecycle commands. |

---

## Checkpoint (Current State)

| Field | Value |
|---|---|
| **Current Group** | None — all groups complete |
| **Current Task** | None — all 18 tasks are ✅ DONE |
| **Last Action** | Cleanup: removed 5 unsupported plugins (midnight-theme, nord-theme, solarized-terminal, minimal-icons, workflow-skills). Deleted GitHub repos. Updated marketplace to 3 plugins. |
| **Next Action** | No pending execution work; await new task assignments from the orchestrator |
| **Blockers** | None |
| **Last Checkpoint** | 2026-08-31 |

---

## Autonomous Work System

Resume rules for heartbeat kicks:

1. Read this file's **Checkpoint** table FIRST.
2. Read the group task tables next.
3. Continue from **Next Action** — never restart completed work.
4. On any status change, update the Rollup in the same edit (see Schema §4).

---

## Dependencies & Coordination Rules

- Only the main orchestrator creates sessions in this ledger
- Workers are released after review
- Worktrees are merged immediately after approval
- Never leave orphaned sessions

---

## Session Ledger

> Tracks orchestration sessions and workers for this task file. Updated when sessions are created, released, or worktrees merged. Canonical columns per Schema §6.

| Handle | Type | Task ID | Orchestration IDs | Status | Created | Branch | Merged |
|---|---|---|---|---|---|---|---|
| `term_24ff1a27-8b86-43f8-9206-73367917448f` | orchestrator | — | `term_24ff1a27-8b86-43f8-9206-73367917448f` | ✅ DONE | Aug 2026 | `main` (Fabrica-plugins/) | — |

---

_Created: Aug 2026_
_Last updated: 2026-08-31_
