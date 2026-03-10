# OpenCode Server Reference

> Full docs: https://opencode.ai/docs/server/

The server exposes a REST API for programmatic interaction with OpenCode. The TUI itself is a client of this server, enabling multiple clients and programmatic control.

## Starting

```bash
opencode serve --port 4096 --hostname 127.0.0.1
```

**Flags:**
- `--port <number>` (default: 4096)
- `--hostname <string>` (default: 127.0.0.1)
- `--mdns` – Enable mDNS discovery
- `--mdns-domain` – Custom domain (default: opencode.local)
- `--cors <origin>` – Allow CORS origin (repeatable)

## Authentication

```bash
OPENCODE_SERVER_PASSWORD=secret opencode serve
```

- `OPENCODE_SERVER_PASSWORD` – Enables HTTP Basic Auth
- `OPENCODE_SERVER_USERNAME` – Override default username `opencode`

## API

OpenAPI 3.1 spec available at `http://<host>:<port>/doc`.

### Endpoint Groups

| Group | Description |
|-------|-------------|
| Global | Health checks, event streaming |
| Projects | List current/all projects |
| Path & VCS | Repository information |
| Config | Manage settings and providers |
| Providers | Authentication and model configuration |
| Sessions | Create, manage, interact with conversations |
| Messages | Send prompts, retrieve responses, execute commands |
| Files | Search text/symbols, list directories, read files |
| Commands | List available slash commands |
| Tools | Experimental tool definitions with JSON schemas |
| LSP / Formatters / MCP | Status monitoring and dynamic configuration |
| Agents | List available agents |
| TUI Control | Drive the interface programmatically |
| Auth | Set provider credentials |
| Logging | Write application logs |
| Events | Server-sent events (SSE) for real-time updates |

## Key Features

- **Headless operation** – Run without UI
- **CORS support** – Enable browser clients
- **Event streaming** – SSE for real-time updates
- **Session management** – Fork sessions, share work, revert changes
- **IDE integration** – TUI endpoint enables IDE plugin functionality
- **SDK generation** – OpenAPI spec used to generate official SDKs
