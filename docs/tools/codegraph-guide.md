# CodeGraph Guide

CodeGraph supports structured code relationship analysis, symbol search, impact checks, and MCP usage for AI coding. It is installed now for readiness, but it will be more useful after the app scaffold and real source files exist.

## Status On This Machine

```text
Installed: yes, global npm package @colbymchenry/codegraph
Version: 0.9.9
Verification: codegraph --version, codegraph --help
```

The global binary is in `C:\Users\ADMIN\AppData\Roaming\npm`. Add that folder to PATH for direct use in new PowerShell sessions, or prefix the session:

```powershell
$env:PATH="$env:APPDATA\npm;$env:PATH"
```

## MCP Setup Note

`codegraph install --target codex --location local` prompted for PATH setup and did not complete non-interactively. No `.codegraph/` project index was created.

The safe printed Codex MCP snippet is:

```toml
[mcp_servers.codegraph]
command = "codegraph"
args = ["serve", "--mcp"]
```

Add it manually to Codex config only when the team wants CodeGraph MCP enabled.

## Recommended Commands

```powershell
codegraph --help
codegraph --version
codegraph install --print-config codex
```

After real app code exists:

```powershell
codegraph init
codegraph status
codegraph query "chat route"
codegraph impact "symbolName"
```

## When To Use

- After implementation phase begins.
- To inspect call relationships, symbol usage, and blast radius.
- To prepare AI prompts with concrete related files.
- To check whether a change crosses module boundaries.

## Do Not Use For

- Product decisions.
- Replacing `docs/api-contract.md`, `ai-context/MODULE_MAP.md`, or context packs.
- Justifying broad refactors near deadline.
- Creating implementation code during preparation phase.

## Current Phase Rule

During preparation phase, keep CodeGraph as installed tooling only. Do not run heavy indexing unless the team explicitly asks for it after app code exists.
