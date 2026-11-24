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
- **CGO + macOS frameworks, darwin/arm64 only:** report-studio-mcp — Core Text
  and Core Graphics through cgo; `MACOSX_DEPLOYMENT_TARGET` pins macOS 26
- **Python/uv (make for test / vuln, no build; release has no assets):** gem-rag, pptx-to-markdown
- **Wails v2/React GUI:** shell-agent-v2
- **Swift GUI:** any submodule with a `Package.swift` — `ls */Package.swift`.
  Not listed by name: the list that stood here had four apps missing, one of
  them added the same week another was.
- **Bash (no build):** cclaude
- **Go, darwin/arm64 release only:** agent-report — it reads gem-agent and
  lagent transcripts, which exist only on macOS (its RFP §7)
- **Archived:** moved to
  [archive-series](https://github.com/nlink-jp/archive-series) under `util/`

## Release checklist

The steps are [CONVENTIONS.md §Release Checklist](https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md#release-checklist) —
open it for each release. This is its outline, not a substitute.

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` (do not push yet)
2. `make vuln` (Go: `govulncheck`; Python: `uv audit --frozen`). A finding
   stops the release before the version is spent: `git reset --soft HEAD~1`,
   fix it in its own commit, commit the release again
3. Tag → push (the build reads its version from the tag)
4. `make clean && make package` — builds every platform, notarizes darwin/arm64
5. `make verify-release`
6. `gh release create` (no assets) — only after step 5 passes
7. Upload each archive one by one (`gh release upload`)
8. `make brew` for tap-eligible tools
9. Update umbrella submodule pointer in this repo
10. Update `nlink-jp/.github/profile/README.md` if new tool
11. Feed new knowledge back to `nlink-jp/knowledge` if any arose
12. Run `check-org.sh` to verify all green
