# CLAUDE.md: General Repository Template
<!-- Copy to your repo root as CLAUDE.md. Replace every [BRACKET]. Keep it under ~120 lines. This file loads into every session, so every line costs context, and agents skim long files just like people do. -->

## Project
[Name], [one sentence on what it is and who it's for].
Stack: [languages, frameworks, package manager]. Repo layout: `[src/]` code, `[tests/]` tests, `[docs/]` docs.

## Commands (run these, not guesses)
- Install: `[command]`
- Build: `[command]`
- Test: `[command]` (full suite) · `[command]` (single file/pattern)
- Lint/format: `[command]`
- Run/dev: `[command]`

## Conventions that matter here
- [Naming: e.g. files snake_case, exported types PascalCase.]
- [Error handling pattern used in this repo, with a file to copy from.]
- [Logging: library, format, what never gets logged, secrets, tokens, personal data.]
- [Anything a newcomer always gets wrong on first try in this repo.]

## Boundaries
- Never edit: `[generated files, lockfiles, migrations, vendor/]`, say so if a task seems to require it.
- Never commit directly to `[main]`; work on a branch and summarize for review.
- No new dependencies without naming the package and why in your reply.
- Secrets live in [env vars / secret manager]; never print, log, or commit one, even partially.

## How to work
- Read before writing: open the files you'll touch and one test that covers them.
- Match the surrounding code's style over your own preference.
- Small, reviewable diffs. Split large changes and say how you split them.
- Verify before declaring done: run the tests and lint, and report the actual output summary, including failures.
- If you're blocked or two readings of the task are plausible, ask one specific question instead of guessing.

## Definition of done
Change + tests + verification summary: what you ran, what passed, what you did not check.
