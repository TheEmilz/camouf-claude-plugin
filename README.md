# Camouf — Claude Code Plugin

> **Catches the mistakes AI coding assistants make** — broken contracts, phantom imports, signature drift, and architectural violations that traditional linters miss entirely.

## Install

```bash
# Add the marketplace
claude plugin marketplace add TheEmilz/camouf-claude-plugin

# Install the plugin
claude plugin install camouf@camouf-marketplace

# Initialize camouf in your project
npx camouf init
```

## What it does

Camouf detects the specific class of bugs that AI coding assistants create due to limited context windows:

| Error Type | Example |
|------------|--------|
| Function name drift | `getUser()` vs `getUserById()` |
| Phantom imports | `import { x } from './nonexistent'` |
| Field mismatch | `user.userEmail` vs `user.email` |
| Missing parameters | `cancelOrder(id)` vs `cancelOrder(id, reason)` |
| Context drift | Same concept named differently across files |
| Layer violations | Frontend importing from backend |

## Plugin components

- **3 Skills**: validate, fix-mismatches, analyze-architecture
- **1 Agent**: mismatch-detector (5-phase validate→fix→revalidate workflow)
- **2 Hooks**: PostToolUse (auto-validate after edits) + Stop (final validation reminder)
- **MCP Server**: 3 tools (`camouf_validate`, `camouf_analyze`, `camouf_suggest_fix`)

## Links

- [Main Repository](https://github.com/TheEmilz/camouf)
- [Documentation](https://github.com/TheEmilz/camouf#readme)
- [Plugin details](plugins/camouf/README.md)
