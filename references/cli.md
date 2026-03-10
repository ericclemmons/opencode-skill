# OpenCode CLI Reference

> Full docs: https://opencode.ai/docs/cli/

## Core Commands

| Command | Description |
|---------|-------------|
| `opencode` | Start the TUI |
| `opencode run "prompt"` | Non-interactive single query |
| `opencode serve` | Headless HTTP API server |
| `opencode web` | HTTP server with web interface |
| `opencode attach <url>` | Connect TUI to remote backend |

## Common Flags

- `--continue / -c` – Resume last session
- `--session / -s <id>` – Continue specific session
- `--fork` – Fork session when continuing
- `--model / -m <provider/model>` – Specify model
- `--agent` – Select agent
- `--format json` – JSON output (for `run`)
- `--file / -f <path>` – Attach files
- `--share` – Share the session
- `--title` – Custom session title
- `--port`, `--hostname` – Server config

## Management Commands

| Command | Function |
|---------|----------|
| `agent [create\|list]` | Create/list agents |
| `auth [login\|list\|logout]` | Manage API credentials |
| `github [install\|run]` | GitHub integration setup |
| `mcp [add\|list\|auth\|logout\|debug]` | MCP server management |
| `models [provider]` | List available models (`--refresh`, `--verbose`) |
| `session list` | Show sessions (`-n` limit, `--format`) |
| `stats` | Token usage/costs (`--days`, `--tools`, `--models`) |
| `export [sessionID]` | Export session as JSON |
| `import <file>` | Import from JSON/URL |
| `acp` | Start Agent Client Protocol server |
| `uninstall` | Remove OpenCode (`--keep-config`, `--keep-data`) |
| `upgrade [version]` | Update to latest/specific version |

## Global Flags

`--help / -h`, `--version / -v`, `--print-logs`, `--log-level` (DEBUG/INFO/WARN/ERROR)

## Environment Variables

**Configuration:**
- `OPENCODE_CONFIG` – Config file path
- `OPENCODE_CONFIG_DIR` – Config directory path
- `OPENCODE_CONFIG_CONTENT` – Inline JSON config

**Features:**
- `OPENCODE_AUTO_SHARE` – Auto-share sessions
- `OPENCODE_DISABLE_AUTOUPDATE` – Skip update checks
- `OPENCODE_ENABLE_EXPERIMENTAL_MODELS` – Unlock experimental models
- `OPENCODE_ENABLE_EXA` – Enable web search tools

**Server:**
- `OPENCODE_SERVER_PASSWORD` – Enable HTTP basic auth
- `OPENCODE_SERVER_USERNAME` – Override username (default: `opencode`)
