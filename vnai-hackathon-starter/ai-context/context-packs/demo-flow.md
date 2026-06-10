# Context Pack: Demo Flow

## 1. Purpose

Demo Flow defines how the team presents the product, data, AI result, trust signal, and fallback.

It is a product/demo module, not only a slide task.

## 2. Owner

Owner: TBD

Support: All members

## 3. Related Files

Existing files:

```text
docs/demo-script.md
docs/demo-safety-checklist.md
docs/pitch-template.md
data/samples/README.md
data/eval/README.md
```

Expected future files:

```text
data/samples/sample_questions.md
data/samples/sample_outputs.md
data/eval/demo_test_cases.md
docs/final-demo-script.md
```

## 4. Data Flow

```text
Problem statement
  -> Sample input
  -> Product action
  -> AI output
  -> Trust signal
  -> Impact statement
  -> Fallback if live demo fails
```

## 5. Input / Output

Input:

* Problem statement.
* Demo data.
* Sample questions.
* User story.

Output:

* Demo script.
* Pitch outline.
* Sample output.
* Fallback screenshot/video.
* Final checklist.

## 6. API or Integration Contract

Demo flow depends on:

```text
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Only include endpoints that are stable enough for the final demo.

## 7. Dependencies

* Frontend UI.
* Backend API.
* Sample data.
* AI/RAG/CV module if used.
* Canva pitch deck.
* Deployment status.

## 8. Do Not Rules

* Do not change demo flow in the final hour.
* Do not use random untested data.
* Do not claim unsupported accuracy.
* Do not rely only on live network/API without fallback.
* Do not let every member edit the pitch at the last minute.

## 9. Common Tasks

* Write demo script.
* Prepare sample questions.
* Prepare fallback screenshots.
* Run demo rehearsal.
* Freeze pitch.
* Record risks after mock tasks.

## 10. Testing Checklist

```text
[ ] Demo flow runs end to end
[ ] Sample questions are known
[ ] Unsupported case is safe
[ ] Screenshot/video fallback exists
[ ] Pitch fits time limit
[ ] API health check passes
```

## 11. Demo Relevance

This is the highest-priority module near deadline.

If a feature is not stable, remove it from live demo or show fallback only.

## 12. AI Coding Instruction

When asking AI to help with demo flow:

```text
Provide product idea, target user, available features, demo time limit, and known risks.
Ask for a short script, fallback plan, and sample questions.
Do not let AI invent implemented features.
```

