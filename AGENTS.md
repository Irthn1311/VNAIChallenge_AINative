# AGENTS.md — VNAI Hackathon Starter

> **Current phase: Preparation and documentation only.**
> No real app code exists yet. Do not scaffold Next.js, FastAPI, Supabase, or any application code until the team explicitly switches to implementation phase.

---

## What This Repo Is

A preparation kit for **Vietnam AI Innovation Challenge 2026** — a 4-person student hackathon team.

The repo contains documentation, API contracts, module contracts, and AI context packs. It is **not a scaffolded application**.

- `apps/web/` — placeholder directory for a planned Next.js frontend; contains only a README, no app code
- `apps/api/` — placeholder directory for a planned FastAPI backend; contains only a README, no app code

---

## Planned Stack (not yet implemented)

| Layer | Technology |
|---|---|
| Frontend | Next.js + Tailwind CSS + shadcn/ui |
| Backend | FastAPI (Python) |
| Database | Supabase PostgreSQL + pgvector |
| Deploy | Vercel (frontend), Railway or Render (backend) |

---

## High-Value Sources of Truth

Read these first before making any changes:

| File | Purpose |
|---|---|
| `README.md` | Repo overview, rules, onboarding order |
| `CLAUDE.md` | Claude-specific agent rules and GitNexus guidance |
| `ai-context/PROJECT_CONTEXT.md` | Current phase, product patterns, architecture intent |
| `ai-context/MODULE_MAP.md` | Module owners, paths, integration points |
| `ai-context/CODING_RULES.md` | Rules for preparation and implementation phases |
| `ai-context/AGENTS.md` | Detailed agent rules (before/after editing checklists) |
| `docs/architecture.md` | Planned system architecture |
| `docs/api-contract.md` | All planned API endpoints with request/response schemas |
| `docs/team-workflow.md` | Branch, PR, and review process |
| `docs/tool-stack-decision.md` | Rationale for tech choices |

Context packs per module: `ai-context/context-packs/`

---

## Planned API Endpoints (all status: Planned — no backend code exists)

| Endpoint | Purpose |
|---|---|
| `GET /health` | Liveness check |
| `POST /api/chat` | Chat with RAG, returns answer + sources |
| `POST /api/upload` | Upload document for RAG |
| `POST /api/report` | Generate summary/report from uploaded data |
| `POST /api/analyze-image` | OCR/CV analysis (optional module) |

Full schemas in `docs/api-contract.md`. Do not deviate from documented schemas.

---

## Module Owners

| Module | Owner | Context Pack |
|---|---|---|
| Frontend UI (`apps/web`) | Nguyễn Tuấn Tài | `ai-context/context-packs/frontend-ui.md` |
| Backend API (`apps/api`) | Nguyễn Tuấn Tài | `ai-context/context-packs/backend-api.md` |
| Chat RAG | Lư Hồng Phúc | `ai-context/context-packs/chat-rag.md` |
| Upload Document | Nguyễn Tuấn Tài | `ai-context/context-packs/upload-document.md` |
| CV / OCR | Lư Hồng Phúc | `ai-context/context-packs/cv-ocr.md` |
| Report / Demo Flow | Lê Thanh Phát | `ai-context/context-packs/demo-flow.md` |

Technical Lead / Integration: Nguyễn Hữu Tri

---

## AI Coding Workflow Tools (verified in repo)

- **Repomix** — packages codebase as context for AI tools. Config: `repomix.config.json`. Output: `repomix-output.md`.
- **GitNexus** — code intelligence, call graph, impact analysis. Index: `.gitnexus/`. Refreshing: `node .gitnexus/run.cjs analyze` or `npx gitnexus analyze`.
- **CodeGraph** — structural code understanding. Guide: `docs/tools/codegraph-guide.md`.

Workflow guide: `docs/tools/codebase-context-workflow.md`

---

## Core Rules for AI Sessions

1. Check the current phase first (`ai-context/PROJECT_CONTEXT.md`).
2. Identify the affected module and its owner (`ai-context/MODULE_MAP.md`).
3. Read the relevant context pack before making changes.
4. Do not deviate from `docs/api-contract.md` without updating it.
5. Do not install packages, scaffold apps, or create routes during preparation phase.
6. Do not hard-code secrets, tokens, or API keys.
7. Do not break demo-critical flows.
8. After editing: report changed files, summary, how to review, and any risks.

---

## Priorities (hackathon order)

1. Working demo
2. Stable frontend ↔ backend integration
3. Clear user flow
4. Simple code
5. Documentation accuracy

Do not over-engineer.

---

<!-- gitnexus:start -->
# GitNexus — Code Intelligence

This project is indexed by GitNexus as **VNAIChallenge_AINative** (532 symbols, 550 relationships, 0 execution flows). Use the GitNexus MCP tools to understand code, assess impact, and navigate safely.

> Index stale? Run `node .gitnexus/run.cjs analyze` from the project root — it auto-selects an available runner. No `.gitnexus/run.cjs` yet? `npx gitnexus analyze` (npm 11 crash → `npm i -g gitnexus`; #1939).

## Always Do

- **MUST run impact analysis before editing any symbol.** Before modifying a function, class, or method, run `impact({target: "symbolName", direction: "upstream"})` and report the blast radius (direct callers, affected processes, risk level) to the user.
- **MUST run `detect_changes()` before committing** to verify your changes only affect expected symbols and execution flows. For regression review, compare against the default branch: `detect_changes({scope: "compare", base_ref: "main"})`.
- **MUST warn the user** if impact analysis returns HIGH or CRITICAL risk before proceeding with edits.
- When exploring unfamiliar code, use `query({query: "concept"})` to find execution flows instead of grepping. It returns process-grouped results ranked by relevance.
- When you need full context on a specific symbol — callers, callees, which execution flows it participates in — use `context({name: "symbolName"})`.

## Never Do

- NEVER edit a function, class, or method without first running `impact` on it.
- NEVER ignore HIGH or CRITICAL risk warnings from impact analysis.
- NEVER rename symbols with find-and-replace — use `rename` which understands the call graph.
- NEVER commit changes without running `detect_changes()` to check affected scope.

## Resources

| Resource | Use for |
|----------|---------| 
| `gitnexus://repo/VNAIChallenge_AINative/context` | Codebase overview, check index freshness |
| `gitnexus://repo/VNAIChallenge_AINative/clusters` | All functional areas |
| `gitnexus://repo/VNAIChallenge_AINative/processes` | All execution flows |
| `gitnexus://repo/VNAIChallenge_AINative/process/{name}` | Step-by-step execution trace |

## CLI

| Task | Read this skill file |
|------|---------------------|
| Understand architecture / "How does X work?" | `.claude/skills/gitnexus/gitnexus-exploring/SKILL.md` |
| Blast radius / "What breaks if I change X?" | `.claude/skills/gitnexus/gitnexus-impact-analysis/SKILL.md` |
| Trace bugs / "Why is X failing?" | `.claude/skills/gitnexus/gitnexus-debugging/SKILL.md` |
| Rename / extract / split / refactor | `.claude/skills/gitnexus/gitnexus-refactoring/SKILL.md` |
| Tools, resources, schema reference | `.claude/skills/gitnexus/gitnexus-guide/SKILL.md` |
| Index, status, clean, wiki CLI commands | `.claude/skills/gitnexus/gitnexus-cli/SKILL.md` |

<!-- gitnexus:end -->
