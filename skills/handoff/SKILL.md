---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work.

If the current directory is inside a git repository, append a new dated section (newest on top) to `docs/handoff.md` at the repo root - create the file with a one-line "append-only, newest first" header comment if it doesn't exist yet, and never overwrite or delete earlier entries. This keeps the handoff log durable and versioned with the project instead of living only in Claude's app data, where it can be silently lost or overwritten by an unrelated later session.

If there is no git repository (e.g. exploring a bare directory), fall back to the temporary directory of the user's OS instead, and say so explicitly in your response.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
