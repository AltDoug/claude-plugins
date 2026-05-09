# altdoug-plugins

Personal aggregator marketplace for Claude Code plugins built by [AltDoug](https://github.com/AltDoug).

## Install

```
/plugin marketplace add AltDoug/claude-plugins
```

Then install any plugin from the catalog:

```
/plugin install <plugin-name>@altdoug-plugins
/reload-plugins
```

**Naming heads-up**: the marketplace is added with `AltDoug/claude-plugins`
(the GitHub `org/repo` path) but referenced as `altdoug-plugins` in
plugin-install commands and `/plugin marketplace remove` (the manifest
`name` field in `marketplace.json`). Claude Code uses the repo path for
fetching and the manifest name for identifying the marketplace afterwards.
Both are stable.

## Catalog

| Plugin | What it does | Source |
|---|---|---|
| `found-issues` | Markdown-based issue tracker. Claude logs out-of-scope issues; entries auto-flip to fixed on PR merge or commit-fix. | [AltDoug/found-issues](https://github.com/AltDoug/found-issues) |

## How this is structured

This repo is an **aggregator marketplace** — it contains only `marketplace.json` and pointers to other repos where the actual plugin code lives. Each plugin is its own standalone repo, versioned and shipped independently.

This pattern lets you install one marketplace and pick the tools you want, without coupling unrelated projects to a single release cycle.

## Adding a plugin

When a new plugin ships, add it to `marketplace.json`'s `plugins` array:

```json
{
  "name": "your-plugin",
  "description": "...",
  "version": "0.1.0",
  "source": {
    "source": "github",
    "repo": "AltDoug/your-plugin"
  }
}
```

Bump `version` on each release of the source plugin to trigger `/plugin update` for installed users.

## License

MIT — see [LICENSE](LICENSE). Each plugin in the catalog has its own license; check the source repo.
