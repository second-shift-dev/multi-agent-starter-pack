# The One Page Orchestration Checklist
*Second Shift Dev, from the free Multi Agent Starter Pack*

Run this before, during, and after any session where more than one agent touches your code. It takes two minutes. It saves hours. Ask me how I know.

## Before you delegate
- [ ] The task is written as a **packet**: goal in one sentence, full context, numbered steps, the exact output format, and how the result will be verified.
- [ ] The packet is **self contained**. A worker with zero memory of your conversation could pick it up and run it cold.
- [ ] **File ownership** is assigned. One writer per file, and shared contract files belong to the orchestrator alone.
- [ ] The **model is chosen by role, not prestige**. Cheapest capable model for bulk work. Premium only where judgment pays: design, hard bugs, final review.
- [ ] Anything **private** (code, data, names, credentials) is either stripped out of the packet, or the destination is one you've explicitly approved for that content.

## While agents work
- [ ] Parallel packets touch **disjoint files**. If two packets need the same file, they run one after the other. Always.
- [ ] A worker that finds out of scope work **reports it instead of doing it**. Scope creep from a helpful agent is still scope creep.
- [ ] You can point at a written list of who's doing what: every worker's packet and owned files, written down somewhere, not held in your head.

## Before you accept anything
- [ ] The worker's report lists **files changed, commands run with real output, and what was NOT verified**.
- [ ] You, or a reviewer agent, **re ran the tests and read the diff yourself**. A confident summary is not evidence.
- [ ] Reviewer findings got fixed, and then **re checked by the reviewer**. Not waved through on the author's word.
- [ ] You know what the session cost: what each task ran up, and whether the expensive model actually earned it.

## The four failure modes this prevents
1. **Collisions.** Two agents editing the same file into a merge mess.
2. **Drift.** A worker quietly expanding scope into a rewrite nobody asked for.
3. **Confident garbage.** Polished output that was never tested, merged on vibes.
4. **Token bonfires.** Premium models doing bulk work a cheap model does just as well.

---
*The full Multi Agent Coding Ops Kit (Second Shift Dev) takes this further: subagent configs, hook recipes, the cost routing playbook, and a verification checklist for each role.*
