# Run Eval

## Purpose

Future scripts for running RAG, API, or demo flow evaluation checks.

## What belongs here

* RAG eval runner.
* API smoke test runner.
* Demo test case runner.
* Simple result reports.

## What does not belong here

* Production load tests.
* Private datasets.
* Hard-coded provider keys.

## Future examples

```text
run-rag-eval.py
run-api-smoke-test.py
run-demo-checklist.py
```

## Notes for AI coding

Evaluation should focus on demo stability: correct answer, safe refusal, source display, and acceptable latency.

