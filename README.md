# Fabrica-plugins

The Fabrica plugin marketplace index — a JSON registry of available plugins that the Fabrica desktop app fetches at startup.

## What This Is

- `fabrica-marketplace.json` — the main marketplace index (app consumes this)
- Kill-list JSON format — managed by the app; this repo defines the format
- Plugin repos live under the `Auto-Scalers/` GitHub org, each added here as a git submodule

## Structure

```
fabrica-marketplace.json    # Main marketplace index (JSON)
.gitmodules                 # Submodule references to plugin repos
fabrica-*/                  # Plugin repos (submodules)
.Fabrica-plugins-board/     # Task file, schemas, guidelines, planning docs
```

## Plugin Manifest Format

Each plugin ships a `fabrica-plugin.json` (was `orca-plugin.json`) with:

- `id`, `name`, `version`, `description`
- `engines: { fabrica: ">=1.0.0" }` (was `engines.orca`)
- `publisher: { name: "autoscalers" }` (was `stablyai`)

Full schema, validation rules, submission guidelines, review process, and kill-list management are documented in `.Fabrica-plugins-board/`.

## Related

- Consumed by `Fabrica-app/` (plugin loader + update mechanism — verified wired)
- Roadmap status: `.Fabrica-board/Fabrica-Roadmap.md`
