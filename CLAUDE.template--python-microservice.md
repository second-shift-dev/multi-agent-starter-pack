# CLAUDE.md: Python Microservice Template
<!-- Copy to your repo root as CLAUDE.md. Replace every [BRACKET]. Delete sections that don't apply. A short file your agents actually read beats a long one they skim. -->

## What this service is
[One sentence: what it does, who calls it, what it must never do.]
Stack: Python [3.12], [FastAPI], deployed to [Cloud Run] via [Docker]. Data: [Postgres / Firestore / none].

## Commands (run these, not guesses)
- Install: `pip install -r requirements.txt`
- Run locally: `uvicorn app.main:app --reload --port 8080`
- Test: `pytest -q`, full suite; `pytest tests/test_[x].py -q` for one file
- Lint/format: `ruff check .` and `ruff format .`
- Type check: `mypy app/`

## Architecture rules
- Handlers stay thin: parse request → call a service function → format response. Business logic lives in `app/services/`, never in route handlers.
- All external calls (HTTP, DB, queues) go through `app/clients/` so tests can fake them at one seam.
- Config comes from environment variables only, read once in `app/config.py`. No `os.environ` scattered through the code.
- Errors: raise domain exceptions from `app/errors.py`; a single handler maps them to status codes. Never return raw exception text to callers.

## Testing rules
- Every behavior change ships with a test. Bug fix = a failing test first, then the fix.
- Tests must not hit the network, a real database, or the clock. Use the fakes in `tests/fakes/`.
- Run the full suite before saying work is done, and paste the result summary in your reply.

## Working agreement
- Small diffs. If a change touches more than ~5 files, stop and propose a split first.
- Never edit migrations, lockfiles, or CI config without saying so explicitly in your reply.
- If an instruction here conflicts with what I ask in chat, flag the conflict instead of silently picking one.
- When you're unsure whether something is in scope, ask one specific question rather than guessing.

## Definition of done
Code + tests passing + lint clean + a short summary of what changed, what you verified, and what you did not verify.
