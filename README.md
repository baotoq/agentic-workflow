# Agent Skills

A personal [Claude Code](https://code.claude.com/docs/en/plugins) marketplace. Its `essentials` plugin has no components of its own: installing it pulls in the plugins I use on every machine.

## Included plugins

| Plugin | Marketplace |
| --- | --- |
| `code-review` | `claude-plugins-official` |
| `github` | `claude-plugins-official` |
| `chrome-devtools-mcp` | `claude-plugins-official` |
| `commit-commands` | `claude-plugins-official` |
| `andrej-karpathy-skills` | `karpathy-skills` |

## Install

Claude Code only installs a dependency from a marketplace you've already added. It adds `claude-plugins-official` on the first interactive start, but you must add `karpathy-skills` yourself.

### With settings

Add this to `~/.claude/settings.json`, then start `claude`. Claude Code adds both marketplaces and installs `essentials` with its dependencies.

```json
{
  "extraKnownMarketplaces": {
    "baotoq": {
      "source": { "source": "github", "repo": "baotoq/agent-skills" }
    },
    "karpathy-skills": {
      "source": { "source": "github", "repo": "forrestchang/andrej-karpathy-skills" }
    }
  },
  "enabledPlugins": {
    "essentials@baotoq": true
  }
}
```

### With commands

Start `claude` once first, or run `claude plugin marketplace add anthropics/claude-plugins-official`.

```sh
claude plugin marketplace add forrestchang/andrej-karpathy-skills
claude plugin marketplace add baotoq/agent-skills
claude plugin install essentials@baotoq
```

### Update

```sh
claude plugin marketplace update baotoq
claude plugin update essentials@baotoq
```

## Add a dependency

1. Add `name@marketplace` to `dependencies` in [`plugins/essentials/.claude-plugin/plugin.json`](./plugins/essentials/.claude-plugin/plugin.json).
2. If the marketplace is new, add its name to `allowCrossMarketplaceDependenciesOn` in [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json). Without it, Claude Code skips the dependency. Also add the marketplace to the install steps above.
3. Bump `version` in `plugin.json`, so installed copies pick up the change.
4. Run `claude plugin validate .` and `claude plugin validate plugins/essentials`.
