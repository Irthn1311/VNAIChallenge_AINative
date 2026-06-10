# PROMPT_LIBRARY.md

Reusable prompts for AI coding, documentation, review, debugging, refactor, API checking, and context-pack generation.

---

## 1. Standard AI Coding Prompt

```text
You are working inside our VNAI hackathon starter repo.

Before editing:
1. Read ai-context/AGENTS.md.
2. Read ai-context/PROJECT_CONTEXT.md.
3. Read ai-context/MODULE_MAP.md.
4. Read the related context pack.
5. Read docs/api-contract.md if this task touches frontend/backend integration.

Task:
[task]

Related module:
[module]

Relevant files:
[files]

Expected behavior:
[expected behavior]

Constraints:
- Do not change unrelated files.
- Do not invent new architecture.
- Follow the API contract.
- Keep the change small enough to review.

After editing:
- List changed files.
- Explain how to test.
- Mention API/demo risk.
```

---

## 2. Debug Prompt

```text
Help debug this issue in our codebase.

Context:
[feature/module]

Expected behavior:
[expected]

Actual behavior:
[actual]

Error logs:
[logs]

Relevant files:
[files]

Constraints:
- Suggest the smallest safe fix.
- Do not rewrite unrelated modules.
- Do not change API response format unless necessary.
- Explain how to reproduce and verify the fix.
```

---

## 3. Code Review Prompt

```text
Review this change for our VNAI hackathon repo.

Check:
1. Does it follow the API contract?
2. Does it match the related context pack?
3. Does it duplicate existing logic?
4. Does it break module boundaries?
5. Is it safe for demo?
6. Are error/loading/empty states handled?
7. Are docs or context files outdated?

Changed files:
[files]

Diff or code:
[code]

Return:
- Findings first.
- Risk level.
- Required fixes before merge.
```

---

## 4. Refactor Prompt

```text
Refactor this module without changing behavior.

Module:
[module]

Files:
[files]

Reason for refactor:
[reason]

Constraints:
- Preserve public API behavior.
- Preserve UI behavior.
- Do not rename exported functions unless necessary.
- Do not move logic across module boundaries without explaining why.
- Keep diff small.

Testing:
[manual or automated checks]
```

---

## 5. API Contract Checking Prompt

```text
Compare this implementation against docs/api-contract.md.

Endpoint:
[endpoint]

Implementation files:
[files]

Check:
- Request fields.
- Response fields.
- Error response.
- Status codes if defined.
- Frontend assumptions.
- Context pack consistency.

Return mismatches and exact files to update.
```

---

## 6. Context Pack Generation Prompt

```text
Create or update a context pack for this module.

Module name:
[name]

Purpose:
[purpose]

Owner:
[owner or TBD]

Related files:
[existing and expected future files]

API/integration:
[endpoint or integration point]

Required sections:
1. Purpose
2. Owner
3. Related Files
4. Data Flow
5. Input / Output
6. API or Integration Contract
7. Dependencies
8. Do Not Rules
9. Common Tasks
10. Testing Checklist
11. Demo Relevance
12. AI Coding Instruction

Keep it concise and useful for future AI coding.
```

---

## 7. Documentation Update Prompt

```text
Update documentation for this preparation-phase repo.

Goal:
[goal]

Files:
[files]

Constraints:
- Markdown only.
- Preserve useful existing content.
- Do not imply code is already implemented.
- Vietnamese for team-facing docs is preferred.
- English technical terms are fine.
```

