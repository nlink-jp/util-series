# CLAUDE.md — util-series

**Organization rules (mandatory): https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md**

## Non-negotiable rules

- **Tests are mandatory** — write them with the implementation. A feature is not complete without tests.
- **Design for testability** — pure functions, injected dependencies, no untestable globals.
- **Never `go build` directly** — always use `make build` (outputs to `dist/`). `go build` without `-o dist/...` drops the binary in the project root, polluting the working tree.
- **Docs in sync** — update `README.md` and `README.ja.md` in the same commit as behaviour changes.
- **Small, typed commits** — `feat:`, `fix:`, `test:`, `chore:`, `docs:`, `refactor:`, `security:`

## This series

Pipe-friendly data transformation and processing CLI tools, plus MCP servers
and GUI apps. The catalog — one row per submodule — is
[README.md](README.md) (ADR-005); do not duplicate it here.

Per-tool build quirks:

- **CGO (cross-compile via Podman):** gem-query, json-to-sqlite;
  image-forge is CGO/Metal, darwin/arm64 only
- **Python/uv (no make):** gem-rag, gem-transcribe, pptx-to-markdown
- **Wails v2/React GUI:** shell-agent-v2
- **Swift GUI:** active-lens-gui, claude-usage-lens-gui, grid-edit,
  image-forge-gui, instant-translate, load-spinner, quick-translate,
  share-mounter, url-shelf
- **Tauri GUI:** mail-analyzer-gui
- **Bash (no build):** cclaude
- **Archived:** csv-editor (superseded by grid-edit), data-agent,
  shell-agent (superseded by shell-agent-v2)

## Release checklist

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` → tag → push
2. `gh release create` (no assets)
3. Build 5 platforms: `linux/amd64`, `linux/arm64`, `darwin/amd64`, `darwin/arm64`, `windows/amd64`
4. Zip each binary + `README.md` → upload one by one
5. Update umbrella submodule pointer in this repo
6. Update org profile: `nlink-jp/.github/profile/README.md`
