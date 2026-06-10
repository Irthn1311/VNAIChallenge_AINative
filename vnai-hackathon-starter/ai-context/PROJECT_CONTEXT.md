# PROJECT_CONTEXT.md

## Project Name

VNAI Hackathon Starter

---

## Current Phase

Preparation phase.

The repository is being used to define documentation, workflow, module contracts, context packs, and planned API contracts before real coding starts.

Do not assume app code exists yet.

---

## Purpose

This repository prepares a flexible foundation for building AI-native MVPs during Vietnam AI Innovation Challenge 2026.

The goal is not to pre-build one fixed product. The goal is to help the team move quickly once the real problem statement is known.

---

## Product Patterns

The starter should support these likely hackathon patterns:

1. AI Knowledge Copilot
   * RAG over documents.
   * Answers with sources.
   * Checklist or summary generation.

2. AI Business Operation Copilot
   * Analyze business data.
   * Summarize customers, orders, operations, or cases.
   * Recommend next actions.

3. AI Document / OCR / CV Copilot
   * Upload image or document.
   * Extract text or structured fields.
   * Return explanation and confidence.

4. AI Report Assistant
   * Generate report from uploaded data.
   * Display dashboard or insight cards.
   * Export or present findings.

---

## Planned Architecture

```text
Next.js Frontend
  -> FastAPI Backend
  -> AI / RAG / CV Services
  -> Supabase PostgreSQL + pgvector + Storage
```

Frontend and backend must integrate through `docs/api-contract.md`.

---

## Main Folders

```text
apps/web       - planned Next.js frontend
apps/api       - planned FastAPI backend
packages       - future shared packages
docs           - human-readable team documentation
ai-context     - AI-readable project context
data           - demo/evaluation/seed data
scripts        - utility scripts
```

---

## Development Principle

AI coding is an accelerator, not a replacement for engineering judgment.

Every AI task should include:

* Related module.
* Related files.
* API contract.
* Context pack.
* Constraints.
* Testing checklist.

Demo stability is more important than perfect architecture.

