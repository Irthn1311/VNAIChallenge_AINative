# Codebase Context Workflow

This workflow connects Repomix, CodeGraph, GitNexus, and Markdown docs/context packs.

Current phase:

```text
Preparation/tooling/documentation only.
No Next.js scaffold.
No FastAPI scaffold.
No product implementation code.
No frontend/backend app dependencies.
```

## Tool Roles

| Tool | Role |
| --- | --- |
| Repomix | Package selected repo context for ChatGPT, Claude, Gemini, or another LLM |
| CodeGraph | Structured code relationships, symbol search, impact analysis, MCP support |
| GitNexus | Visual repo exploration, onboarding, and repo graph |
| Markdown docs/context packs | Source of truth for phase, rules, roles, contracts, and module boundaries |

## Preparation Phase Workflow

1. Read `README.md`.
2. Read `docs/team-onboarding-guide.md`.
3. Read `docs/definition-of-done.md`.
4. Read `ai-context/AGENTS.md`.
5. Read `ai-context/MODULE_MAP.md`.
6. Read `docs/api-contract.md` if an API topic is involved.
7. Use Repomix to pack `docs/**` and `ai-context/**` for AI review.
8. Use GitNexus for repo overview if useful.
9. Keep CodeGraph installed but avoid heavy indexing until app code exists.

Stop there during preparation phase.

## Implementation Phase Workflow

Only after the team explicitly moves into implementation:

1. Read the module contract and context pack.
2. Use GitNexus to understand the repo area.
3. Use CodeGraph to inspect code relationships and impact.
4. Use Repomix to package selected context if asking an LLM for help.
5. Prompt AI with exact file boundaries and do-not rules.
6. Test.
7. Update docs/context if a contract or module boundary changes.
8. Open PR.

## Recommended Commands

```powershell
repomix --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
repomix --style markdown --include "docs/**" --output repomix-docs-only.md
repomix --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
npx --yes gitnexus analyze
codegraph --help
```

Repomix fallback:

```powershell
npx repomix@latest --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
```

## Before Editing Code Checklist

```text
[ ] Team has confirmed implementation phase
[ ] Module owner is clear in ai-context/MODULE_MAP.md
[ ] Module contract exists or is explicitly scoped
[ ] Context pack has been read
[ ] API contract has been read if endpoint behavior is involved
[ ] Related files have been identified
[ ] Do-not rules are clear
[ ] Test or manual verification path is defined
```

## Anti-Patterns

- Asking AI to build a feature without the relevant docs/context pack.
- Sending the full repo to AI when one module context is enough.
- Treating GitNexus or CodeGraph output as source of truth over Markdown docs.
- Changing API behavior without updating `docs/api-contract.md`.
- Committing generated `.codegraph`, `.gitnexus`, or `repomix-*.md` outputs.
- Scaffolding app code during preparation phase.
