# Copilot Agents Dojo 🥋

<h1 align="center">🏯</h1>

**Your AI agents are untrained. Time to put them through the dojo.**

Most teams using GitHub Copilot agents let them run wild — no discipline, no form, no kata. Drop a prompt, hope for the best, clean up the wreckage. That's not engineering. That's sparring with a blindfold on.

This dojo contains training scrolls, helper scripts, and automation that turn reckless agents into disciplined black belts.

## The Training Scrolls

### [`skills.md`](skills.md) — The Six Disciplines
The core kata. Copilot agents auto-discover this scroll and train on these disciplines:

- **🥋 Plan before striking** — No wild swings. Agents plan multi-step work before touching code. Discipline over impulse.
- **🥋 Deploy your students** — A master delegates. Subagents handle research, analysis, testing, and review. One task per subagent.
- **🥋 Learn from every fall** — After every correction, agents capture the lesson with tags and metrics. Patterns feed back into skills.
- **🥋 Prove your technique** — No kata is complete without demonstration. Tests, logs, diffs — show your work or it didn't happen.
- **🥋 Pursue elegant form** — Brute force is for beginners. Challenge hacky solutions. But skip the kata for simple fixes — don't over-engineer.
- **🥋 Fix what's broken, solo** — Reproduce, diagnose, fix, verify. Zero hand-holding. Zero context switching from the user.

### [`.github/copilot-instructions.md`](/.github/copilot-instructions.md) — The Dojo Rules
The house rules that every agent follows when they enter your repo:

- Code standards — multi-stack examples (TypeScript, Python, Java, Go, .NET)
- Behavioral governance summary linking back to the disciplines
- Session-start lesson review workflow
- Helper script references for automation

## Helper Scripts

Reusable scripts in `/scripts/` to reduce token burn and enforce consistency:

| Script | Purpose |
|--------|---------|
| [`scripts/init.sh`](scripts/init.sh) | Scaffolds `tasks/todo.md` and `tasks/lessons.md` on first clone |
| [`scripts/lesson-updater.sh`](scripts/lesson-updater.sh) | Scans lessons for recurring patterns (3+), proposes skill amendments |
| [`scripts/verify.sh`](scripts/verify.sh) | Pre-PR verification: tests, clean tree, plan check |

```bash
# Initialize the dojo in your repo
bash scripts/init.sh

# Check for patterns that should become skills
bash scripts/lesson-updater.sh

# Verify before submitting a PR
bash scripts/verify.sh
```

## Automated Enforcement

The `.github/workflows/dojo-enforce.yml` GitHub Action runs on every PR to `main`:
- Checks that `tasks/todo.md` has a real plan (not the default template)
- Verifies `tasks/lessons.md` exists
- Validates helper scripts are present

## Self-Improvement Loop

Inspired by [cognee](https://github.com/topoteretes/cognee)-style automation:

1. **Observe**: After every correction, log a structured lesson in `tasks/lessons.md` with YAML tags (error type, root cause, fix, rule).
2. **Store**: Lessons are tagged and queryable. Metrics track total lessons, recurring patterns, and amendment rate.
3. **Amend**: When a pattern hits 3+ occurrences, `scripts/lesson-updater.sh` proposes a rule update to `skills.md`.
4. **Evaluate**: Track pre/post-fix metrics in `tasks/lessons.md`. If a rule isn't working, revise it.
5. **Rollback**: Failed fixes get rolled back immediately. Failed rules get revised or removed.

## Why Train Your Agents?

Untrained agents:
- Rush in without a plan — all offense, no strategy
- Never learn from their losses
- Throw sloppy patches instead of finding the root cause
- Declare victory without proof
- Flood the context window like an undisciplined sparring partner

Trained agents operate like **seasoned black belts** — plan the approach, execute with precision, verify the outcome, learn from every round.

## Enter the Dojo

1. **Place `skills.md` at your repo root** — Copilot agents auto-discover this scroll and begin training immediately
2. **Place `.github/copilot-instructions.md`** in your `.github/` folder — customize the Code Standards for your fighting style
3. **Run `bash scripts/init.sh`** — scaffolds `tasks/todo.md` and `tasks/lessons.md`
4. **Watch the transformation** — your agents will plan before coding, verify before bowing out, and grow stronger after every session

## The Dojo Layout

```
your-repo/
├── skills.md                          # The Six Disciplines (auto-discovered)
├── .github/
│   ├── copilot-instructions.md        # The Dojo Rules
│   └── workflows/
│       └── dojo-enforce.yml           # PR enforcement
├── scripts/
│   ├── init.sh                        # Dojo initialization
│   ├── lesson-updater.sh              # Pattern scanner & amendment proposer
│   └── verify.sh                      # Pre-PR verification
└── tasks/
    ├── todo.md                        # Battle plan
    └── lessons.md                     # Defeat log, metrics & prevention rules
```

## Choose Your Fighting Style

The Code Standards in `copilot-instructions.md` ship with examples for multiple stacks:

- **TypeScript** 📘: strict mode, Vitest, Tailwind, Next.js App Router
- **Python** 🐍: pytest, Black, type hints, FastAPI/Django
- **Java** ☕: JUnit 5, Spring Boot, Maven/Gradle
- **Go** 🐹: standard library, table-driven tests
- **.NET** 🛡️: xUnit, clean architecture, nullable reference types

Pick your style. Delete the others. The Six Disciplines are **style-agnostic**.

## Origin Story

Forged in real-world AI delivery. These disciplines emerged from running agents across production projects and learning what separates chaotic AI-assisted development from disciplined, battle-tested delivery.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[MIT](LICENSE)

---

**⭐ Star this dojo** if you're done babysitting your AI agents. Fork it, train your agents, earn your belt.
