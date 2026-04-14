# CLAUDE.md — util-series

**Organization rules (mandatory): https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md**

## Non-negotiable rules

- **Tests are mandatory** — write them with the implementation. A feature is not complete without tests.
- **Design for testability** — pure functions, injected dependencies, no untestable globals.
- **Never `go build` directly** — always use `make build` (outputs to `dist/`). `go build` without `-o dist/...` drops the binary in the project root, polluting the working tree.
- **Docs in sync** — update `README.md` and `README.ja.md` in the same commit as behaviour changes.
- **Small, typed commits** — `feat:`, `fix:`, `test:`, `chore:`, `docs:`, `refactor:`, `security:`

## This series

Pipe-friendly data transformation and processing CLI tools.

```
util-series/
├── csv-to-json/       github.com/nlink-jp/csv-to-json
├── eml-to-jsonl/      github.com/nlink-jp/eml-to-jsonl
├── msg-to-jsonl/      github.com/nlink-jp/msg-to-jsonl
├── gem-query/         github.com/nlink-jp/gem-query  (CGO — cross-compile via Podman)
├── json-filter/       github.com/nlink-jp/json-filter
├── json-to-sqlite/    github.com/nlink-jp/json-to-sqlite  (CGO — cross-compile via Podman)
├── json-to-table/     github.com/nlink-jp/json-to-table
├── jstats/            github.com/nlink-jp/jstats
├── jviz/              github.com/nlink-jp/jviz
├── lookup/            github.com/nlink-jp/lookup
├── markdown-viewer/   github.com/nlink-jp/markdown-viewer
├── pptx-to-markdown/  github.com/nlink-jp/pptx-to-markdown  (Python/uv)
├── mcp-guardian/       github.com/nlink-jp/mcp-guardian
├── rex/               github.com/nlink-jp/rex
└── sdate/             github.com/nlink-jp/sdate
```

## Release checklist

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` → tag → push
2. `gh release create` (no assets)
3. Build 5 platforms: `linux/amd64`, `linux/arm64`, `darwin/amd64`, `darwin/arm64`, `windows/amd64`
4. Zip each binary + `README.md` → upload one by one
5. Update umbrella submodule pointer in this repo
6. Update org profile: `nlink-jp/.github/profile/README.md`
