# gws-multi-account

Multi-account management for the Google Workspace CLI (`gws`). Ships an opencode plugin (published to npm as `opencode-gws-multi-account`) and a Claude Code plugin (installed via the bundled `.claude-plugin` marketplace).

## Release

Use the **Release** GitHub Actions workflow (`workflow_dispatch`). It lints, format-checks, typechecks, tests, bumps version in `package.json` / `.claude-plugin/plugin.json`, rebuilds `hooks/hook.js` so the committed artifact matches, commits, tags, publishes to npm, and creates a GitHub Release. Tags have no `v` prefix.

### Version Decision

- If the user specifies an exact version (e.g., `1.5.0`), use it as-is.
  Otherwise, the agent decides the bump level based on the changes since the last release (never bump major unless user explicitly asks):
  - **minor** — New features, new hook behaviors, new platform support, breaking changes
  - **patch** — Bug fixes, refactors, docs, dependency updates, minor improvements
- Never ask the user which version to bump. Decide and proceed.
