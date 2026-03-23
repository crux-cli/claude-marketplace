---
name: crux-uninstall
description: "Fully uninstall the crux CLI binary and its data directory (~/.crux)."
---

# Uninstall Crux CLI

This skill removes the crux CLI tool and its configuration from the system.

## Steps

Run the following commands:

```bash
uv tool uninstall crux-cli
rm -rf ~/.crux
```

After running these commands, confirm to the user that crux-cli has been fully removed.

Note: This does not remove the crux plugin from Claude Code. To also remove the plugin, run:
```
/plugin uninstall crux @crux-marketplace
```
