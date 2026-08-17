# Fabrica-plugins — Tasks

> Single source of truth for plugin marketplace work. The Roadmap (`.Fabrica-Board/Fabrica-Roadmap.md`) tracks cross-cutting status only — this file owns execution details.

---

## Status Legend

- **VERIFY** — implemented, needs verification
- **VERIFY** — implemented and verified
- **PARTIAL** — partially implemented
- **TODO** — planned, not started
- **BLOCKED** — waiting on dependency

---

## Orca Source Study

> Clone and study the original Orca plugin repos to understand structure before building Fabrica equivalents.

| # | Task | Status | Notes |
|---|------|--------|-------|
| P0a | Clone `stablyai/orca-plugins` into `_sources/orca-plugins/` | **TODO** | Marketplace index — the core reference for schema and format |
| P0b | Clone bundled plugin repos into `_sources/` | **TODO** | `orca-portuguese`, `orca-navigation-shortcuts`, `orca-multipass-recipes` |
| P0c | Clone theme/skill plugin repos into `_sources/` | **TODO** | `orca-solarized-terminal`, `orca-minimal-icons`, `orca-nord-theme`, `orca-midnight-theme`, `orca-workflow-skills` |
| P0d | Study marketplace index format from cloned repo | **TODO** | Document schema, fields, validation rules, git source format |
| P0e | Study bundled plugin manifest format | **TODO** | `orca-plugin.json` → `fabrica-plugin.json`, `engines.orca` → `engines.fabrica`, publisher rename |
| P0f | Document rename strategy | **TODO** | `stablyai` → `autoscalers`, `orca-*` → `fabrica-*`, URLs, repo references |

---

## Marketplace Index

| # | Task | Status | Notes |
|---|------|--------|-------|
| P1 | Initialize marketplace index JSON | **TODO** | Schema: plugin ID, name, description, author, version, download URL, compatibility. Build from cloned `stablyai/orca-plugins` reference. |
| P2 | Add bundled plugins to index | **TODO** | `fabrica-portuguese`, `fabrica-multipass-recipes`, `fabrica-navigation-shortcuts` |
| P3 | Plugin submission guidelines | **TODO** | How third-party devs submit plugins |

---

## Plugin Schema

| # | Task | Status | Notes |
|---|------|--------|-------|
| P4 | Define plugin manifest schema | **TODO** | `engines.fabrica` field, version constraints |
| P5 | Plugin validation rules | **TODO** | Required fields, version format, URL validation |

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
