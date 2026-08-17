# Fabrica-plugins — Tasks

> Single source of truth for plugin marketplace work. The Roadmap (`.Fabrica-Board/Fabrica-Roadmap.md`) tracks cross-cutting status only — this file owns execution details.

---

## Status Legend

- **DONE** — implemented and verified
- **PARTIAL** — partially implemented
- **TODO** — planned, not started
- **BLOCKED** — waiting on dependency

---

## Marketplace Index

| # | Task | Status | Notes |
|---|------|--------|-------|
| P1 | Initialize marketplace index JSON | **TODO** | Schema: plugin ID, name, description, author, version, download URL, compatibility |
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

## What's Already Done

- [x] GitHub repo created (`Auto-Scalers/Fabrica-plugins`)

---

_Created: Aug 2026_
