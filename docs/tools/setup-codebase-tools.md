# Codebase Context Tools Setup

This setup is for preparation/tooling/documentation only. It does not scaffold app code and does not install frontend/backend app dependencies.

## Environment Detected

```text
Current directory: D:\SGU\Challenge\Team_VNAIChallenge_DN2026\vnai-hackathon-starter
Node: v22.20.0
npm: 11.16.0
Git: git version 2.49.0.windows.1
Python: Python 3.13.9
Repomix: 1.14.1 via npx/global package; direct PATH command was not visible until npm global bin was added to PATH for the session
CodeGraph: 0.9.9 via global package; direct PATH command needs C:\Users\ADMIN\AppData\Roaming\npm on PATH
GitNexus: 1.6.7 via npx
```

Detected executable locations:

```text
node: C:\Program Files\nodejs\node.exe
npm: C:\Program Files\nodejs\npm, C:\Program Files\nodejs\npm.cmd
git: C:\Program Files\Git\bin\git.exe, C:\Program Files\Git\cmd\git.exe
npm global prefix: C:\Users\ADMIN\AppData\Roaming\npm
```

## Installation Result

| Tool | Result | Verification | Notes |
| --- | --- | --- | --- |
| Repomix | Installed globally with `npm install -g repomix`; `npx repomix@latest` also works | `npx repomix@latest --version` returned `1.14.1`; session PATH-adjusted `repomix --version` returned `1.14.1` | Current PowerShell process did not initially include npm global bin, so use `npx repomix@latest` or add `C:\Users\ADMIN\AppData\Roaming\npm` to PATH. |
| CodeGraph | Installed globally with `npm install -g @colbymchenry/codegraph` | session PATH-adjusted `codegraph --version` returned `0.9.9`; `codegraph --help` works | `codegraph install --target codex --location local` prompted for PATH setup and did not complete non-interactively. `codegraph install --print-config codex` printed the Codex MCP snippet only. |
| GitNexus | Used through `npx --yes gitnexus` | `npx --yes gitnexus --help` works; npm package metadata shows `gitnexus` version `1.6.7` | `npx --yes gitnexus analyze` completed and indexed the Git root `D:\SGU\Challenge\Team_VNAIChallenge_DN2026`, not only this subfolder. It created Git-root `.gitnexus/`, `.claude/`, `AGENTS.md`, and `CLAUDE.md`. |

## Commands Run Successfully

```powershell
pwd
node -v
npm -v
git --version
python --version
where.exe node
where.exe npm
where.exe git
npm install -g repomix
npx repomix@latest --version
npm view @colbymchenry/codegraph version
npm install -g @colbymchenry/codegraph
codegraph --version
codegraph --help
codegraph install --print-config codex
npm view gitnexus version description bin
npx --yes gitnexus --help
npx --yes gitnexus analyze
```

For direct global CLIs in this shell, this session-local PATH prefix was used:

```powershell
$env:PATH="$env:APPDATA\npm;$env:PATH"
```

## Commands Failed Or Skipped

```powershell
repomix --version
codegraph --version
npx gitnexus --help
```

Initial direct `repomix` and `codegraph` checks failed because npm global bin was not on PATH in the current shell. Initial `npx gitnexus --help` failed in sandbox/offline cache mode, then timed out once without `--yes`; `npx --yes gitnexus --help` succeeded.

```powershell
codegraph install --target codex --location local
```

This command prompted for PATH installation and did not complete a visible project-local config write. To avoid silent global or editor config changes, only the printed Codex config snippet was captured:

```toml
[mcp_servers.codegraph]
command = "codegraph"
args = ["serve", "--mcp"]
```

## Usage Rules

- Repomix is safe to use now because the repo already has `docs/` and `ai-context/`.
- CodeGraph is installed now, but it will be more useful after real app code exists.
- GitNexus can be used for visual repo exploration and onboarding.
- Markdown docs and context packs remain the source of truth.
- Do not commit generated `.codegraph`, `.gitnexus`, or `repomix-*.md` outputs.
- Do not treat GitNexus/CodeGraph output as a replacement for `docs/`, `ai-context/`, code review, or explicit team decisions.

## Recommended Commands

Use global commands after adding npm global bin to PATH, or use the `npx` Repomix fallback.

```powershell
repomix --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
repomix --style markdown --include "docs/**" --output repomix-docs-only.md
repomix --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
npx --yes gitnexus analyze
codegraph --help
```

Fallback Repomix commands:

```powershell
npx repomix@latest --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
npx repomix@latest --style markdown --include "docs/**" --output repomix-docs-only.md
npx repomix@latest --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
```

## Manual Actions Required

1. Decide whether to keep GitNexus-generated Git-root files: `.gitnexus/`, `.claude/`, `AGENTS.md`, `CLAUDE.md`.
2. If direct global CLIs should work in new PowerShell sessions, add `C:\Users\ADMIN\AppData\Roaming\npm` to the user PATH.
3. If CodeGraph MCP should be enabled for Codex, add the printed snippet to `C:\Users\ADMIN\.codex\config.toml` or rerun the installer intentionally with the desired location and target.
