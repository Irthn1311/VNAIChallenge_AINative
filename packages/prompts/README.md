# Prompts Package

## Purpose

Future home for reusable prompt templates used by AI services.

## What belongs here

* RAG system prompts.
* Report generation prompts.
* OCR explanation prompts.
* Prompt version notes.

## What does not belong here

* API keys.
* Random one-off chat experiments.
* Business logic that should live in code.

## Future examples

```text
rag_system_prompt.md
report_generation_prompt.md
query_rewrite_prompt.md
cv_explanation_prompt.md
```

## Notes for AI coding

If a prompt changes the API output, update `docs/api-contract.md` or the related context pack.

