# OpenCode Formatters Reference

> Full docs: https://opencode.ai/docs/formatters/

OpenCode auto-formats files after writing or editing using language-specific formatters, ensuring generated code follows project style standards.

## How It Works

1. Checks the file extension against all enabled formatters
2. Executes the appropriate formatter command
3. Applies changes automatically

## Built-in Formatters (25+)

| Language | Formatters |
|----------|-----------|
| JS/TS | Prettier, Biome, oxfmt (experimental) |
| Python | Ruff, uv |
| Go | gofmt |
| Rust | Rustfmt, cargofmt |
| PHP | Pint |
| Ruby | Rubocop, standardrb |
| HTML/CSS | Biome, clang-format, htmlbeautifier |
| Markdown/JSON/YAML | Prettier, Biome |
| Other | Dart, Kotlin, Clojure, Haskell, OCaml, Elixir, Terraform, Zig, Nim, D, Gleam, R |

Each formatter requires its tool to be installed and may need specific config files to activate.

## Configuration (`opencode.json`)

### Disable all formatters

```json
{
  "formatter": false
}
```

### Disable a specific formatter

```json
{
  "formatter": {
    "prettier": { "disabled": true }
  }
}
```

### Custom formatter

```json
{
  "formatter": {
    "my-formatter": {
      "command": ["my-formatter", "--fix", "$FILE"],
      "extensions": [".xyz", ".abc"],
      "environment": { "MY_VAR": "value" }
    }
  }
}
```

**Properties:**
- `command` (string[]) – Formatting command. `$FILE` is replaced with the target file path
- `extensions` (string[]) – File extensions to match
- `environment` (object) – Environment variables for the command
- `disabled` (boolean) – Deactivate the formatter
