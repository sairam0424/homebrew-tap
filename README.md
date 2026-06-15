# homebrew-tap

Homebrew tap for **Ag-Bash** and **MindForge**.

> ⚠️ **This is a scaffold to push to `github.com/sairam0424/homebrew-tap`.**
> A Homebrew tap repo MUST be named `homebrew-<name>` (the `homebrew-` prefix is mandatory;
> `brew tap sairam0424/tap` re-adds it automatically). Push the `Formula/` directory and the
> `.github/workflows/` to a repo named exactly `homebrew-tap` under your account.

## Install

```bash
brew tap sairam0424/tap
brew install ag-bash      # AI-native bash interpreter, shell, and MCP server
brew install mindforge    # Agentic-intelligence framework for Claude Code
```

Or one-shot without tapping first:

```bash
brew install sairam0424/tap/ag-bash
brew install sairam0424/tap/mindforge
```

## Formulae

| Formula | Wraps (npm) | Bins |
| --- | --- | --- |
| `ag-bash` | `@ag-bash/bash` + `@ag-bash/mcp-server` | `ag-bash`, `ag-shell`, `ag-bash-mcp` |
| `mindforge` | `mindforge-cc` | `mindforge` |

## Maintenance

On every npm release, bump each formula's `url` (new version) and recompute `sha256`.
The included GitHub Action (`.github/workflows/bump.yml`) automates this — it runs
`brew bump-formula-pr` against the formula when triggered with the new version. You can also
do it manually:

```bash
# download the new tarball (no pipe-to-shell) and hash it
curl -sL -o /tmp/pkg.tgz "https://registry.npmjs.org/@ag-bash/bash/-/bash-<NEW>.tgz"
shasum -a 256 /tmp/pkg.tgz
# then edit Formula/ag-bash.rb url + sha256, commit, push
```

## Notes

- **homebrew-core is NOT targeted.** Both projects currently fall below homebrew-core's
  self-submission notability bar (≥225 stars / ≥90 forks / ≥90 watchers) and a single-maintainer
  Node CLI with vendored WASM is a maintainability red flag for core. Revisit core once the repos
  have independent GitHub traction and a non-author maintainer can drive the PR.
- A custom tap has **zero organic discoverability** (`brew search` does not index third-party taps) —
  it is a `brew install` convenience/credibility signal, not a growth channel. npm + the MCP
  registries + the Claude plugin marketplace remain the primary distribution surfaces.
