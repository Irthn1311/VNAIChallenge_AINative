# GitNexus Guide

GitNexus is for visual repo exploration, onboarding, and graph-powered understanding. In this project it should support navigation and review, not replace the Markdown docs.

## Status On This Machine

```text
Install method: npx --yes gitnexus
Package version: 1.6.7
Help verification: npx --yes gitnexus --help
Analyze verification: npx --yes gitnexus analyze
```

`npx --yes gitnexus analyze` completed successfully:

```text
Repository indexed successfully
539 nodes | 564 edges | 0 clusters | 0 flows
Indexed path: D:\SGU\Challenge\Team_VNAIChallenge_DN2026
```

Important: GitNexus detected and indexed the Git root, not only `vnai-hackathon-starter`.

## Generated Files Observed

GitNexus generated these untracked Git-root files:

```text
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\.gitnexus\
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\.claude\
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\AGENTS.md
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\CLAUDE.md
```

The Git-root `.gitignore` already ignores `.gitnexus/`. Review whether the team wants to keep or remove the generated `.claude/`, `AGENTS.md`, and `CLAUDE.md` files.

## Recommended Commands

```powershell
npx --yes gitnexus --help
npx --yes gitnexus status
npx --yes gitnexus analyze
npx --yes gitnexus list
npx --yes gitnexus serve
```

Use from the Git root if you want full-repo analysis:

```powershell
cd D:\SGU\Challenge\Team_VNAIChallenge_DN2026
npx --yes gitnexus analyze
```

Use from this project folder only when you are comfortable with GitNexus still resolving the parent Git root.

## When To Use

- Onboarding a new member.
- Explaining repo structure during team planning.
- Visualizing what a PR touches.
- Helping reviewers find relevant docs and modules.

## Do Not Use For

- Deciding API shape instead of `docs/api-contract.md`.
- Replacing code review or source-of-truth docs.
- Storing secrets or private data.
- Generating app implementation during preparation phase.

## Tool Comparison

| Tool | Best for |
| --- | --- |
| GitNexus | Visual repo exploration, onboarding, repo graph |
| CodeGraph | Structured code relationships and MCP support |
| Repomix | Packaging selected repo context for LLMs |
| Markdown docs | Source of truth for phase, contracts, rules, and roles |
