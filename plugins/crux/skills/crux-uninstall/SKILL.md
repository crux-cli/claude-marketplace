---
name: crux-uninstall
description: "Fully uninstall the crux CLI tool (installed via uv) and its data directory (~/.crux)."
---

# Uninstall Crux CLI

This skill removes the crux CLI tool and all crux-managed data (MCP registrations, skill configs, project metadata, and cached state stored in ~/.crux). Secrets stored in the OS keychain are not removed by this process.

## Important

The crux plugin's SessionStart hook will automatically reinstall crux-cli if the plugin is still active. You must remove the plugin first, then uninstall the CLI.

## Steps

1. First, confirm with the user that they want to proceed. Warn them that `~/.crux` contains configuration and project data that will be permanently deleted.

2. Remove the crux plugin from Claude Code:
```
/plugin uninstall crux @crux-marketplace
```

3. Then run the cleanup commands:
```bash
uv tool uninstall crux-cli || echo "crux-cli was not installed via uv"
if [ -d ~/.crux ]; then rm -rf ~/.crux && echo "Removed ~/.crux directory."; else echo "No ~/.crux directory found."; fi
```

After running these commands, confirm to the user that crux-cli has been fully removed.
