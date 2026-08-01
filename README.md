# util-series

A collection of general-purpose data transformation and processing CLI utilities maintained under the [nlink-jp](https://github.com/nlink-jp) organisation.

Each tool is a standalone project with its own repository, release cycle, and documentation.
This umbrella repository tracks them together as git submodules and hosts shared conventions.

## Tools

| Tool | Language | Description |
|------|----------|-------------|
| [active-lens](https://github.com/nlink-jp/active-lens) | Go | Content-free Mac activity tracker — classifies operating/present/away and derives a per-day work log. darwin/arm64 |
| [active-lens-gui](https://github.com/nlink-jp/active-lens-gui) | Swift | macOS menu-bar front-end over active-lens — current session state and a calendar-style work timeline |
| [ask-gemini-mcp](https://github.com/nlink-jp/ask-gemini-mcp) | Go | MCP server exposing `ask_gemini(prompt)` — second-opinion consultations via Vertex AI Gemini |
| [ask-llm-mcp](https://github.com/nlink-jp/ask-llm-mcp) | Go | MCP server exposing `ask_llm(prompt)` — second opinions via an OpenAI-compatible endpoint (e.g. LM Studio) |
| [cclaude](https://github.com/nlink-jp/cclaude) | Bash | Containerized Claude Code — run Claude Code in an isolated container with project isolation |
| [chrome-pilot-mcp](https://github.com/nlink-jp/chrome-pilot-mcp) | Go | Zero-dependency browser-automation MCP — 27 tools speaking the Chrome DevTools Protocol directly |
| [claude-usage-lens](https://github.com/nlink-jp/claude-usage-lens) | Go | Token usage & cost analysis for Claude Code — parses local session logs into a durable SQLite store |
| [claude-usage-lens-gui](https://github.com/nlink-jp/claude-usage-lens-gui) | Swift | macOS menu-bar app showing today's Claude usage cost, with Swift Charts analysis |
| [csv-editor](https://github.com/nlink-jp/csv-editor) | Go + React (Wails) | **(archived)** CSV/TSV viewer & editor GUI — superseded by grid-edit |
| [csv-to-json](https://github.com/nlink-jp/csv-to-json) | Go | Convert CSV data to a JSON array |
| [data-agent](https://github.com/nlink-jp/data-agent) | Go + React (Wails) | **(archived)** Data-analysis desktop GUI — superseded by shell-agent-v2 |
| [data-analyzer](https://github.com/nlink-jp/data-analyzer) | Go | Large-scale JSON/JSONL analysis using local LLMs — sliding window + progressive summarization |
| [data-toolbox-mcp](https://github.com/nlink-jp/data-toolbox-mcp) | Go | MCP server exposing DuckDB analysis and containerized Python execution — workspace-scoped |
| [eml-to-jsonl](https://github.com/nlink-jp/eml-to-jsonl) | Go | Parse .eml files and output structured JSONL — headers, body, attachments |
| [gem-image](https://github.com/nlink-jp/gem-image) | Go | Image generation and editing CLI via Vertex AI Gemini |
| [gem-query](https://github.com/nlink-jp/gem-query) | Go | Natural language data analysis CLI — SQL generation for DuckDB/SQLite via Vertex AI Gemini |
| [gem-rag](https://github.com/nlink-jp/gem-rag) | Python | Gemini-powered RAG CLI for Markdown documents — Vertex AI embeddings + DuckDB |
| [gem-search](https://github.com/nlink-jp/gem-search) | Go | Agentic web search via Vertex AI Gemini with Google Search Grounding |
| [gem-summary](https://github.com/nlink-jp/gem-summary) | Go | Text summarisation CLI via Vertex AI Gemini — chunked/parallel fallback for long inputs |
| [gem-transcribe](https://github.com/nlink-jp/gem-transcribe) | Python | Audio transcription CLI on Vertex AI Gemini — speaker inference, structured JSON |
| [grid-edit](https://github.com/nlink-jp/grid-edit) | Swift | Native macOS CSV/TSV editor (AppKit) — csv-editor's successor; Japanese-encoding & delimiter auto-detection, IME-safe editing |
| [image-forge](https://github.com/nlink-jp/image-forge) | Go | Local diffusion image-generation engine + model manager for Apple Silicon (stable-diffusion.cpp, CLI + MCP) |
| [image-forge-gui](https://github.com/nlink-jp/image-forge-gui) | Swift | Native macOS front-end for image-forge — composer, batch generation, gallery |
| [instant-translate](https://github.com/nlink-jp/instant-translate) | Swift | macOS menu-bar translator on the on-device Translation framework — no LLM, no network. darwin/arm64 |
| [json-filter](https://github.com/nlink-jp/json-filter) | Go | Extract, validate, prettify, and repair JSON from arbitrary text streams |
| [json-to-sqlite](https://github.com/nlink-jp/json-to-sqlite) | Go | Load JSON data into SQLite with automatic schema inference and evolution |
| [json-to-table](https://github.com/nlink-jp/json-to-table) | Go | Format a JSON array into text, Markdown, HTML, CSV, PNG, or Slack Block Kit tables |
| [jstats](https://github.com/nlink-jp/jstats) | Go | SPL-style stats aggregations for JSON streams — count, avg, p95, stdev, values, and more |
| [jviz](https://github.com/nlink-jp/jviz) | Go | Visualize JSON arrays as interactive charts in the browser — bar, line, pie, table with live SSE updates |
| [load-spinner](https://github.com/nlink-jp/load-spinner) | Swift | macOS menu-bar CPU/GPU load indicator — spinner speed proportional to load. darwin/arm64 |
| [lookup](https://github.com/nlink-jp/lookup) | Go | Enrich JSON/JSONL streams by matching fields against CSV/JSON data sources |
| [mail-analyzer](https://github.com/nlink-jp/mail-analyzer) | Go | Suspicious email analyzer — rule-based indicators + Gemini content analysis for .eml/.msg |
| [mail-analyzer-gui](https://github.com/nlink-jp/mail-analyzer-gui) | Rust + Svelte (Tauri) | macOS desktop GUI for mail-analyzer — drag & drop email analysis |
| [mail-analyzer-local](https://github.com/nlink-jp/mail-analyzer-local) | Go | Local LLM version of mail-analyzer — via OpenAI-compatible API (LM Studio, Ollama) |
| [markdown-viewer](https://github.com/nlink-jp/markdown-viewer) | Go | Single-binary local Markdown viewer — renders GFM, Mermaid, and syntax-highlighted code in the browser |
| [mcp-guardian](https://github.com/nlink-jp/mcp-guardian) | Go | MCP governance proxy — zero-dependency single binary for tool call auditing, constraint learning, and loop detection |
| [msg-to-jsonl](https://github.com/nlink-jp/msg-to-jsonl) | Go | Parse Outlook .msg files and output structured JSONL — same schema as eml-to-jsonl |
| [pptx-to-markdown](https://github.com/nlink-jp/pptx-to-markdown) | Python | Convert `.pptx` presentations to structured Markdown for LLM analysis |
| [quick-translate](https://github.com/nlink-jp/quick-translate) | Swift | macOS menu-bar translation via a local LLM (OpenAI-compatible API) |
| [rex](https://github.com/nlink-jp/rex) | Go | Extract fields from text using named regex capture groups — outputs JSON |
| [sdate](https://github.com/nlink-jp/sdate) | Go | Calculate timestamps using Splunk-like relative time modifiers (e.g., `-1d@d`) |
| [share-mounter](https://github.com/nlink-jp/share-mounter) | Swift | macOS menu-bar app that auto-mounts SMB shares at login without opening a Finder window (NetFS) |
| [shell-agent](https://github.com/nlink-jp/shell-agent) | Go + Swift | **(archived)** macOS LLM chat & agent — superseded by shell-agent-v2 |
| [shell-agent-v2](https://github.com/nlink-jp/shell-agent-v2) | Go + React (Wails) | Desktop app for interactive data analysis — session DuckDB, hybrid LLM, container sandbox |
| [splunk-mcp](https://github.com/nlink-jp/splunk-mcp) | Go | MCP server for Splunk search over the REST API — async job pattern, exact result counts |
| [url-shelf](https://github.com/nlink-jp/url-shelf) | Swift | macOS menu-bar shelf of URL notes kept as plain `.webloc` files — per-entry private-window opening. darwin/arm64 |
| [video-studio-mcp](https://github.com/nlink-jp/video-studio-mcp) | Go | MCP server assembling narrated presentation MP4s from image + audio page manifests (ffmpeg) |
| [voice-studio-mcp](https://github.com/nlink-jp/voice-studio-mcp) | Go | MCP server for local multi-speaker Japanese speech synthesis (AivisSpeech Engine) |
| [webhook-relay](https://github.com/nlink-jp/webhook-relay) | Go | Authenticated webhook receiver — writes payloads to GCS via Cloud Run Service |
| [zip-porter](https://github.com/nlink-jp/zip-porter) | Swift | Windows-safe ZIP creation/extraction GUI+CLI — junk-free, NFC/CP932 names, AES-256/ZipCrypto passwords. darwin/arm64 |

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

1. Develop in the workspace root `_wip/` following the org
   [CONVENTIONS.md](https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md)
   (Starting a New Project), then create the repository under `nlink-jp/`.
2. Add it as a submodule here: `git submodule add https://github.com/nlink-jp/<tool>.git`
3. Add a row to the table above (`check-org.sh` fails otherwise).
