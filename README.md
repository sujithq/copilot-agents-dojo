# Copilot Agent Governance

**Stop letting your AI agents freestyle. Start governing them.**

Most teams using GitHub Copilot agents treat them like magic autocomplete. Drop a prompt, hope for the best, clean up the mess. That's not engineering — that's gambling with your codebase.

This repo contains two files that change the game:

## The Two Files That Matter

### [`skills.md`](skills.md) — Agent Behavioral Skills
The auto-discovered governance layer. Copilot agents pick this up automatically and follow these behavioral rules:

- **Plan before coding** — No more cowboy commits. Agents plan multi-step work before touching code.
- **Use subagents** — Keep context windows clean. Offload research and parallel analysis.
- **Self-improve** — After every correction, agents capture the lesson and never repeat the mistake.
- **Verify before done** — No task is complete without proof it works. Tests, logs, diffs.
- **Demand elegance** — Challenge hacky solutions on non-trivial changes.
- **Fix bugs autonomously** — Reproduce, diagnose, fix, verify. Zero hand-holding.

### [`.github/copilot-instructions.md`](/.github/copilot-instructions.md) — Project Instructions
The project-level configuration that ties it all together:

- Code standards (TypeScript strict, Tailwind, Vitest)
- Agent behavioral governance summary with link to skills.md
- Task management workflow (plan → track → verify → capture lessons)

## Why This Matters

Without governance, AI agents:
- Skip planning and jump to implementation
- Never learn from mistakes
- Produce hacky fixes instead of root-cause solutions
- Mark tasks "done" without verification
- Pollute context windows with everything at once

With governance, they behave like **senior engineers** — plan first, verify always, learn constantly.

## How to Use This

1. **Copy `skills.md`** to your repo root — Copilot agents auto-discover it
2. **Copy `.github/copilot-instructions.md`** to your `.github/` folder — customize the Code Standards section for your stack
3. **Create `tasks/todo.md`** and `tasks/lessons.md` — agents will use these for planning and learning
4. **Watch your agents level up** — they'll plan before coding, verify before marking done, and capture lessons after corrections

## The Pattern

```
your-repo/
├── skills.md                          # Agent behavioral governance (auto-discovered)
├── .github/
│   └── copilot-instructions.md        # Project-specific instructions
└── tasks/
    ├── todo.md                        # Agent planning workspace
    └── lessons.md                     # Captured mistakes & prevention rules
```

## Adapt It

The Code Standards section in `copilot-instructions.md` is specific to a TypeScript/Next.js stack. Replace it with your own:

- **Python**: pytest, Black, type hints, FastAPI/Django conventions
- **Java**: JUnit, Spring Boot patterns, Maven/Gradle standards
- **Go**: standard library conventions, table-driven tests
- **.NET**: xUnit, clean architecture, nullable reference types

The behavioral governance in `skills.md` is **stack-agnostic** — it works for any language or framework.

## Credits

Born from real-world AI delivery methodology work. These patterns emerged from running agents across production projects and learning what separates chaotic AI-assisted development from disciplined, reliable delivery.

---

**Star this repo** if you're tired of babysitting your AI agents. Fork it, adapt it, make it yours.
