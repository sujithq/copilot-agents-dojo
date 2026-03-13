# Core Skills for Copilot Agents

## 1. Plan Node Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions).
- If something goes sideways, STOP and re-plan immediately – don't keep pushing.
- Use plan mode for verification steps, not just building.
- Write detailed specs upfront to reduce ambiguity.
- Write the plan to `tasks/todo.md` with checkable items before writing any code.

## 2. Subagent Strategy
- Use subagents liberally to keep main context window clean.
- Offload research, exploration, and parallel analysis to subagents.
- For complex problems, throw more compute at it via subagents.
- **One task per subagent** for focused execution.

### Subagent Roles (Examples)
| Role | Purpose | When to Deploy |
|------|---------|----------------|
| **Research Subagent** | Search docs, APIs, dependencies, or codebase patterns | Before implementing unfamiliar features |
| **Analysis Subagent** | Analyze error logs, stack traces, performance profiles | During debugging or optimization |
| **Refactor Subagent** | Explore alternative implementations, identify code smells | When "Demand Elegance" triggers |
| **Test Subagent** | Write and run test suites in parallel | During verification phase |
| **Review Subagent** | Audit changes against plan, check for regressions | Before marking task complete |

### Multi-Agent Coordination
- Subagents report back to the main agent context.
- If subagents return conflicting results, re-run with more specific instructions or resolve via majority consensus.
- Never let subagent conflicts silently pass — log discrepancies in `tasks/lessons.md`.

## 3. Self-Improvement Loop
- **Session start**: Review `tasks/lessons.md` for entries relevant to the current project/task before doing anything else.
- After ANY correction from the user: update `tasks/lessons.md` with the pattern.
- Write rules for yourself that prevent the same mistake.
- Ruthlessly iterate on these lessons until mistake rate drops.
- Tag lessons with metadata (error type, file, discipline) for queryability.
- Track metrics: count occurrences, record pre/post-fix results, note amendment success rate.
- If a pattern appears 3+ times, propose a rule update to `skills.md` or `copilot-instructions.md`.

### Lesson Entry Format
```yaml
- date: YYYY-MM-DD
  error_type: <category>       # e.g., type-error, logic-bug, test-gap, over-engineering
  trigger: <what happened>
  root_cause: <why it happened>
  fix: <what was done>
  rule: <prevention rule>
  occurrences: <count>
  status: active | resolved | amended-to-skill
```

## 4. Verification Before Done
- Never mark a task complete without proving it works.
- Diff behavior between main and your changes when relevant.
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness.
- Use `scripts/verify.sh` when available to automate pre-PR checks.

## 5. Demand Elegance (Balanced)
- For non-trivial changes: pause and ask "Is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution."
- **Skip this for simple, obvious fixes — don't over-engineer.** A one-line bug fix doesn't need an abstraction layer.
- Challenge your own work before presenting it.
- When in doubt, choose the solution with fewer moving parts.

## 6. Autonomous Bug Fixing
- When given a bug report: just fix it. Don't ask for hand-holding.
- Point at logs, errors, failing tests — then resolve them.
- **No context switching required from the user.** The user should not need to explain how to read logs, run tests, or navigate the codebase.
- Go fix failing CI tests without being told how.
- Reproduce → diagnose → fix → verify. Full cycle, zero questions.

### Rollback Strategy
- If verification fails after a fix, **immediately rollback** the changes.
- Log the failed attempt in `tasks/lessons.md` with root cause analysis.
- Re-plan with a different approach before trying again.
- Never push broken code hoping it will be caught later.

---

## Core Principles
- **Simplicity First**: Make every change as simple as possible. Impact minimal code. Fewer lines > more lines.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards. Every shortcut is technical debt.
- **Zero Hand-Holding**: The user provides intent; the agent handles execution. No asking "which file?", "what command?", or "how do I run tests?" — figure it out.
- **Continuous Evolution**: The dojo is not static. Lessons feed back into skills. Skills get sharper over time. Measure improvement or it didn't happen.
