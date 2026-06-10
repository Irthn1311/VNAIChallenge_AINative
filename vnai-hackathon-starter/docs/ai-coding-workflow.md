# AI Coding Workflow

AI coding giúp team nhanh hơn, nhưng nếu thiếu kiểm soát sẽ tạo sai architecture, sai API contract và khó demo.

---

## 1. Why AI coding needs control

AI tools có thể:

* Tạo file không cần thiết.
* Bịa route hoặc schema.
* Sửa lan sang module khác.
* Hard-code demo logic.
* Làm code chạy được một phần nhưng phá integration.

Vì vậy team dùng context packs và contracts trước khi prompt.

---

## 2. Required context before prompting AI

Trước khi dùng AI cho task không nhỏ, chuẩn bị:

* Task rõ ràng.
* Module liên quan.
* Related files.
* API contract.
* Context pack.
* Constraints.
* Testing checklist.

---

## 3. Standard AI coding prompt

```text
You are working inside our VNAI hackathon starter repo.
Read ai-context/AGENTS.md, PROJECT_CONTEXT.md, MODULE_MAP.md, and the related context pack first.

Task:
[task]

Module:
[module]

Related files:
[files]

API contract:
[endpoint or none]

Constraints:
- Do not change unrelated files.
- Follow docs/api-contract.md.
- Keep the implementation minimal.
- Do not invent new architecture.

Testing:
[steps]
```

---

## 4. Debug prompt

```text
Debug this issue with the smallest safe fix.

Expected:
[expected]

Actual:
[actual]

Logs:
[logs]

Relevant files:
[files]

Constraints:
- Do not refactor unrelated code.
- Do not change API response format unless necessary.
- Explain how to verify the fix.
```

---

## 5. Code review prompt

```text
Review this diff for bugs, API mismatch, module boundary issues, demo risk, and missing tests.

Related module:
[module]

API contract:
[contract]

Diff:
[diff]
```

---

## 6. Refactor prompt

```text
Refactor this code without changing behavior.

Goal:
[goal]

Files:
[files]

Constraints:
- Keep public API stable.
- Keep UI behavior stable.
- Do not move logic across modules unless necessary.
- Explain risks.
```

---

## 7. API contract checking prompt

```text
Compare implementation with docs/api-contract.md.

Endpoint:
[endpoint]

Files:
[files]

Return:
- Request mismatch.
- Response mismatch.
- Error handling mismatch.
- Docs/context pack updates needed.
```

---

## 8. Context pack generation prompt

Use the template in `ai-context/PROMPT_LIBRARY.md` or ask AI to fill the 12 required sections.

---

## 9. Tool-specific rules

## ChatGPT Plus

Use for:

* Planning.
* Prompt design.
* Review.
* Explaining architecture.

Do not use for:

* Blind large code generation without repo context.

## Codex

Use for:

* Repo-aware edits.
* Implementation.
* Test fixes.
* Documentation updates.

Do not use for:

* Broad scaffolding unless the team explicitly enters implementation phase.

## Gemini / Antigravity

Use for:

* Quick coding alternatives.
* UI/code suggestions.
* Cross-checking ideas.

Do not use for:

* Unreviewed direct merges.

## Claude

Use for:

* Long reasoning.
* Refactor review.
* Risk analysis.
* Writing clearer docs.

Do not use for:

* Replacing source-of-truth docs in this repo.

## GitNexus, CodeGraph, Repomix

Use for:

* Understanding codebase structure.
* Finding dependencies.
* Creating compact context for AI.
* Reviewing module boundaries.

Do not use for:

* Storing secrets.
* Replacing manual review.

---

## 10. What AI must not do

* Do not invent architecture.
* Do not change unrelated files.
* Do not hard-code secrets.
* Do not silently change API contracts.
* Do not remove fallback/demo safety.
* Do not claim features are implemented when they are only planned.

