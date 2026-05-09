# Contributing to altdoug-plugins

This repo is an **aggregator marketplace** — it contains only
`marketplace.json` and pointers to plugin source repos. Each plugin
lives in its own standalone repo with its own tests, CI, releases, and
issue tracker.

## What PRs against this repo do

- **Bump a plugin's `version`** in `.claude-plugin/marketplace.json`
  after a new release ships in the plugin's source repo. Users with
  the plugin installed get prompted to `/plugin update` once the bump
  is merged.
- **Add a new plugin** to the catalog by appending an entry to the
  `plugins` array. The plugin's source repo must already be public on
  GitHub.
- **Remove a plugin** that's been deprecated upstream.

## What does NOT happen here

- Plugin code, tests, or behavior changes. Those go in the plugin's
  own repo.
- Plugin issues / bug reports. Open those against the plugin's source
  repo (the `repo` field in its catalog entry tells you where).

## Adding a plugin

1. Confirm the plugin's source repo is **public** on GitHub. Private
   repos are not installable via `/plugin marketplace add`.
2. Confirm the plugin has a valid `.claude-plugin/plugin.json` and
   passes `/plugin install` end-to-end from your local machine.
3. Append to `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "your-plugin",
     "description": "One-line description, ~120 chars max",
     "version": "0.1.0",
     "source": {
       "source": "github",
       "repo": "OrgOrUser/your-plugin"
     }
   }
   ```
4. Update `README.md`'s "Catalog" table with the same plugin.
5. Open a PR against `main`. The maintainer will validate and merge.

## Bumping a version

After a plugin ships a new release in its source repo:

1. Update `version` in the matching `marketplace.json` entry.
2. Open a PR. Title: `Bump <plugin> to <version>`.
3. Body: link to the source repo's CHANGELOG entry for that version.

## Style

- Commit messages: imperative mood (`Bump found-issues to 1.0.1`, not
  `Bumped`).
- Keep PRs scoped to a single plugin / single concern. Don't bundle
  multiple plugin bumps unless they're a coordinated release.

## License

By contributing, you agree your changes are under the [MIT
License](LICENSE) used by this repo.
