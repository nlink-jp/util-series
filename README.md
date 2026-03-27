# util-series

A collection of general-purpose data transformation and processing CLI utilities maintained under the [nlink-jp](https://github.com/nlink-jp) organisation.

Each tool is a standalone project with its own repository, release cycle, and documentation.
This umbrella repository tracks them together as git submodules and hosts shared conventions.

## Tools

| Tool | Language | Description |
|------|----------|-------------|
| [json-to-table](https://github.com/nlink-jp/json-to-table) | Go | Format a JSON array into text, Markdown, HTML, CSV, PNG, or Slack Block Kit tables |
| [rex](https://github.com/nlink-jp/rex) | Go | Extract fields from text using named regex capture groups — outputs JSON |
| [sdate](https://github.com/nlink-jp/sdate) | Go | Calculate timestamps using Splunk-like relative time modifiers (e.g., `-1d@d`) |
| [csv-to-json](https://github.com/nlink-jp/csv-to-json) | Go | Convert CSV data to a JSON array |
| [json-to-sqlite](https://github.com/nlink-jp/json-to-sqlite) | Go | Load JSON data into SQLite with automatic schema inference and evolution |
| [lookup](https://github.com/nlink-jp/lookup) | Go | Enrich JSON/JSONL streams by matching fields against CSV/JSON data sources |
| [pptx-to-markdown](https://github.com/nlink-jp/pptx-to-markdown) | Python | Convert `.pptx` presentations to structured Markdown for LLM analysis |

## Design Philosophy

- **Pipe-friendly**: stdout is data, stderr is diagnostics. Every tool reads from stdin and writes to stdout.
- **Unix composable**: output in plain text or JSON; designed to work with `jq`, `grep`, `xargs`, and each other.
- **Single binary**: no runtime dependencies; download and run.
- **Minimal surface**: each tool does one thing well.

## Build

All tools use a unified `Makefile` with consistent targets:

```sh
make build      # Build for the current platform → dist/<binary>
make build-all  # Cross-compile for all platforms → dist/<binary>-<goos>-<goarch>[.exe]
make package    # Build and create .zip archives → dist/<binary>-<version>-<goos>-<goarch>.zip
make test       # Run the test suite
make clean      # Remove dist/
```

Target platforms: `linux/amd64`, `linux/arm64`, `darwin/amd64`, `darwin/arm64`, `windows/amd64`.

> **Note for `json-to-sqlite`**: this tool depends on `go-sqlite3` (CGO). Linux and Windows cross-compilation uses Podman (or Docker) containers.
>
> **Note for `pptx-to-markdown`**: this is a Python project managed with `uv`. It does not use `make`; use `uv sync` to install dependencies and `uv run pytest` to run tests.

## Shared Conventions

See [CONVENTIONS.md](CONVENTIONS.md) for coding, documentation, and release standards that apply across all tools in this series.

## Adding a New Tool

1. Create the repository under `nlink-jp/`.
2. Follow [CONVENTIONS.md](CONVENTIONS.md) from the start.
3. Add it as a submodule here: `git submodule add git@github.com:nlink-jp/<tool>.git`
4. Add a row to the table above.
