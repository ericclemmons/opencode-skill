# OpenCode SDK Reference

> Full docs: https://opencode.ai/docs/sdk/

Type-safe JavaScript/TypeScript client generated from the server's OpenAPI spec.

## Install

```bash
npm install @opencode-ai/sdk
```

## Usage

```typescript
import { createOpencode } from "@opencode-ai/sdk"

// Starts server + client
const { client } = await createOpencode()
```

**Configuration options:** `hostname` (default: 127.0.0.1), `port` (4096), `timeout` (5000ms), custom config objects.

### Client-only mode (connect to existing server)

```typescript
import { createOpencodeClient } from "@opencode-ai/sdk"
const client = createOpencodeClient({ baseUrl: "http://localhost:4096" })
```

## Core API

| Category | Methods |
|----------|---------|
| **Sessions** | Create, delete, prompt, run commands, share, revert/restore messages |
| **Files** | Text search, symbol search, list directories, read files |
| **Events** | SSE stream for real-time updates |
| **Auth** | Set provider credentials |
| **TUI** | Programmatic control (submit prompts, change model/theme, toasts) |
| **App** | Logging, agent listing |
| **Project** | List and retrieve current projects |

## Structured Output

```typescript
const result = await client.session.prompt({
  path: { id: sessionId },
  body: {
    parts: [{ type: "text", text: "Research Anthropic..." }],
    format: {
      type: "json_schema",
      schema: {
        type: "object",
        properties: {
          summary: { type: "string" },
          points: { type: "array", items: { type: "string" } }
        },
        required: ["summary", "points"]
      }
    }
  }
})
```

Output formats: `text` (default), `json_schema`. Catch `StructuredOutputError` when validation fails.

## Key Session Methods

- **Prompt** – Send message and get AI response
- **Inject context** – Add context without triggering a reply (useful for plugins)
- **Shell commands** – Execute commands in the session
- **Revert/Restore** – Undo and redo message changes
- **Permissions** – Handle permission requests programmatically
