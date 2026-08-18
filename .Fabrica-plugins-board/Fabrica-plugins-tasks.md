# Fabrica-plugins — Tasks

> Single source of truth for plugin marketplace work. The Roadmap (`.Fabrica-Board/Fabrica-Roadmap.md`) tracks cross-cutting status only — this file owns execution details.

---

## Status Legend

- **DONE** — implemented and verified
- **VERIFY** — implemented, needs verification
- **PARTIAL** — partially implemented
- **TODO** — planned, not started
- **BLOCKED** — waiting on dependency

---

## Orca Source Study

> Clone and study the original Orca plugin repos to understand structure before building Fabrica equivalents.

| # | Task | Status | Notes |
|---|------|--------|-------|
| P0a | Clone `stablyai/orca-plugins` into `_sources/orca-plugins/` | **DONE** | Cloned to `_sources/orca-plugins/` |
| P0b | Clone bundled plugin repos into `_sources/` | **DONE** | Cloned: `orca-portuguese`, `orca-navigation-shortcuts`, `orca-multipass-recipes` |
| P0c | Clone theme/skill plugin repos into `_sources/` | **DONE** | Cloned: `orca-solarized-terminal`, `orca-minimal-icons`, `orca-nord-theme`, `orca-midnight-theme`, `orca-workflow-skills` |
| P0d | Study marketplace index format from cloned repo | **DONE** | Schema documented in `.Fabrica-plugins-board/P0-source-study.md` |
| P0e | Study bundled plugin manifest format | **DONE** | `orca-plugin.json` format documented in `.Fabrica-plugins-board/P0-source-study.md` |
| P0f | Document rename strategy | **DONE** | Rename strategy documented in `.Fabrica-plugins-board/P0-source-study.md` |

---

## Marketplace Index

| # | Task | Status | Notes |
|---|------|--------|-------|
| P1 | Initialize marketplace index JSON | **DONE** | `marketplace-index.json` created with 8 bundled plugins, following `stablyai`→`autoscalers` rename strategy. |
| P2 | Add bundled plugins to index | **DONE** | All 8 bundled plugins verified present in `marketplace-index.json`. |
| P3 | Plugin submission guidelines | **DONE** | Documented in `.Fabrica-plugins-board/P3-plugin-submission-guidelines.md`. |

---

## Plugin Schema

| # | Task | Status | Notes |
|---|------|--------|-------|
| P4 | Define plugin manifest schema | **DONE** | `fabrica-plugin.json` schema documented in `.Fabrica-plugins-board/P4-plugin-manifest-schema.md`. |
| P5 | Plugin validation rules | **DONE** | Documented in `.Fabrica-plugins-board/P5-plugin-validation-rules.md`. |

---

## Quality & Trust

| # | Task | Status | Notes |
|---|------|--------|-------|
| P6 | Plugin review process | **TODO** | Manual review before listing |
| P7 | Kill-list management | **TODO** | Block malicious/broken plugins |
| P8 | Plugin signing (future) | **TODO** | Verify plugin authenticity |

---

## App Integration

| # | Task | Status | Notes |
|---|------|--------|-------|
| P9 | Plugin loader reads from marketplace | **TODO** | `Fabrica-plugins` repo → desktop app |
| P10 | Plugin update mechanism | **TODO** | Check for new versions |

---

## What Needs Verification

- [~] GitHub repo created (`Auto-Scalers/Fabrica-plugins`)

---

_Created: Aug 2026_
