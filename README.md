# Fabrica-plugins

The Fabrica plugin marketplace index — a JSON registry of available plugins that the Fabrica desktop app fetches at startup.

## What This Is

- `fabrica-marketplace.json` — the main marketplace index (app consumes this)
- Kill-list JSON format — managed by the app; this repo defines the format
- Plugin repos live under the `Auto-Scalers/` GitHub org, each added here as a git submodule

## Current Plugins

| Plugin | Category | Description |
|--------|----------|-------------|
| `fabrica-portuguese` | languages | Brazilian Portuguese translations |
| `fabrica-multipass-recipes` | vm-recipes | Multipass workspace lifecycle recipes |
| `fabrica-navigation-shortcuts` | keybindings | Command aliases for frequent Fabrica views |

## Structure

```
fabrica-marketplace.json          # Main marketplace index (JSON)
.gitmodules                       # Submodule references to plugin repos
fabrica-portuguese/               # Portuguese language plugin (submodule)
fabrica-multipass-recipes/        # Multipass recipes plugin (submodule)
fabrica-navigation-shortcuts/     # Navigation shortcuts plugin (submodule, bundled)
.Fabrica-plugins-board/           # Task file, schemas, guidelines, planning docs
```

## Plugin Manifest Format

Each plugin ships a `fabrica-plugin.json` with:

- `id`, `name`, `version`, `description`
- `engines: { fabrica: ">=1.0.0" }`
- `publisher: { name: "autoscalers" }`

Full schema, validation rules, submission guidelines, review process, and kill-list management are documented in `.Fabrica-plugins-board/`.

## Related

- Consumed by `Fabrica-app/` (plugin loader + update mechanism — verified wired)
- Roadmap status: `.Fabrica-board/Fabrica-Roadmap.md`
