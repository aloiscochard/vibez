# Vibez Autonomous Loop Instructions

You are running in **Vibez mode**: autonomous, iterative development loop until the project in PRD.md is complete.

## Strict Core Rules – Violate none of these
1. **Always read full context first**
   Every iteration: Re-read
   - This "Vibez Autonomous Loop Instructions" (rules & response format)
   - `vibez/state/PRD.md` (goals, non-goals, success criteria, architecture hints)
   - `vibez/state/TASKS.md` (checkbox task list – current state)
   - `vibez/state/PROGRESS.md` (execution history & decisions)
   - Cargo.toml, src/*, tests/*, benches/*, any recent compile/test output
   - Recent git log if relevant

2. **One atomic task per turn**  
   - Select **exactly one** unchecked highest-priority / most logical next task from TASKS.md.
   - Do NOT combine tasks, invent extras, or do partial work on future tasks.
   - If a task blocks (e.g. design decision needed), note it clearly and ask for human input — do NOT guess.

3. **Think deeply & structured**
   Use <thinking> tags for ultra-detailed step-by-step reasoning before any code.

7. **Progress & loop termination**
   - On task completion:
     - Tick [x] the box in TASKS.md
     - Append 1–2 sentences PROGRESS.md (what done, key choices, issues overcome)
   - When **all** TASKS.md boxes are checked → output "MISSION COMPLETE" and cease suggesting work.

## Response Format – Exact & only this structure
<thinking>
Detailed reasoning:
- Current project state summary
- Why this task is next (dependencies, risk, priority)
- Domain-specific concerns (best practices for language and technologies in use)
- Test plan & expected failures
- Alternatives considered & why rejected
</thinking>

<plan>
- Bullet list of concrete steps you will take this turn
</plan>

<changes>
File: src/memtable.rs
```diff
- old line here
+ new safe & idiomatic line
```

One diff block per file.
</changes>

<commands>
cargo fmt && cargo clippy -- -D warnings && cargo test
git commit -m "feat: implement mutable memtable with tombstones" -m "Vibez: completed task '[exact task text]'"
</commands>

<next-task>
Exact text of the next unchecked TASKS.md item you plan (or "All tasks complete – await human review")
</next-task>

