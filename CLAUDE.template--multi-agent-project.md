# CLAUDE.md: Multi-Agent Project Template
<!-- For a repo where several agents (or agent tools) work in parallel: an orchestrator
     plus workers, subagents, or a second tool like Codex. Copy to the repo root.
     Yes, these rules sound strict. They're written in merge conflicts.
     Parallel agents fail in predictable ways: colliding edits, duplicated work,
     and confident reports that nobody verified. This file is the fix. -->

## Project
[Name], [one sentence]. Stack: [stack]. Commands (install / build / test / lint): [fill in, workers must run these, not invent their own].

## Roles (one writer per file at a time)
- **Orchestrator** (main session): owns the plan, splits work into packets, assigns file ownership, reviews every result, merges. The orchestrator does not write feature code itself unless a packet is tiny.
- **Workers / subagents**: execute exactly one packet each. A packet names: goal, context, files you own, files you must not touch, output format, and how the result will be verified.
- **Reviewer**: read-only. Checks diffs against the packet and this file. Writes no code.

## File ownership rules
- Before starting a packet, state the files you will modify. If two packets need the same file, they run in sequence, never in parallel.
- Shared contract files (schemas, interfaces, shared types, this file) are orchestrator-only edits.
- If you discover needed work outside your packet, report it, do not do it.

## The packet rule
No packet, no work. A request like "fix the auth thing" is not a packet. A packet is self-contained: a worker with no memory of this conversation could execute it from the text alone. If your packet is ambiguous, ask the orchestrator one specific question before starting.

## Verification (nothing is done because a worker says so)
- The worker's report is a claim, not evidence. The orchestrator re-runs tests and reads the diff before accepting.
- Workers: end every report with (1) files changed, (2) commands run with real output summaries, (3) what you did NOT verify.
- Reviewer findings are addressed by the original worker, then re-checked by the reviewer, not by the worker's assurance.

## Cost discipline
- Bulk work (summaries, extraction, boilerplate, first drafts) goes to the cheapest model that can do it; premium models are for design, hard debugging, and final review.
- One packet, one model decision, the orchestrator states which model and why in the packet.

## Boundaries
- No agent edits another agent's in-flight files, this file, CI, migrations, or lockfiles without the orchestrator saying so in the packet.
- No external service gets this repo's private code or data unless the packet explicitly authorizes that service for that content.
- Secrets: never in packets, prompts, logs, or commits.
