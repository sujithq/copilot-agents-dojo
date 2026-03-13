# Copilot Instructions

## Code Standards

Customize this section for your stack. Examples for common fighting styles:

### TypeScript (Default Example)
- Always use TypeScript with `strict: true`
- Naming: camelCase for variables/functions, PascalCase for components/types
- Styling: Tailwind CSS + shadcn/ui components
- Testing: Write Vitest tests for every new component/logic
- Architecture: Next.js App Router, Server Actions, React Server Components when possible
- Security: Never commit secrets, use environment variables

### Python
- Type hints on all function signatures
- Formatting: Black (line length 88)
- Testing: pytest with fixtures, aim for >80% coverage
- Linting: ruff or flake8
- Architecture: FastAPI or Django conventions as applicable
- Dependency management: pyproject.toml / requirements.txt pinned

### Java
- Follow Google Java Style Guide
- Testing: JUnit 5 + Mockito for unit tests
- Build: Maven or Gradle (match existing project)
- Architecture: Spring Boot patterns, constructor injection
- Security: OWASP dependency check in CI

### Go
- Follow standard library conventions and `go fmt`
- Testing: table-driven tests with `testing` package
- Error handling: explicit, no panic in library code
- Architecture: clean package boundaries, interfaces for testability

### .NET
- Nullable reference types enabled
- Testing: xUnit + FluentAssertions
- Architecture: clean architecture, MediatR for CQRS if applicable
- Security: never log PII, use IOptions pattern for config

> **Pick your style.** Delete the others or keep them as reference.

## Agent Behavioral Governance

See [skills.md](../skills.md) for the full behavioral skills framework. Key principles:

- **Plan first**: Enter plan mode for any non-trivial task (3+ steps). Write plan to `tasks/todo.md`.
- **Verify before done**: Run tests, check logs, diff against main. Never mark complete without proof.
- **Subagents for scale**: Offload research and parallel analysis to subagents. Keep context clean.
- **Self-improvement**: Capture lessons in `tasks/lessons.md` after any correction. Review at session start.
- **Elegance over hacks**: Challenge shortcuts on non-trivial changes. Skip for simple fixes — don't over-engineer.
- **Autonomous bug fixing**: Reproduce → diagnose → fix → verify. Zero hand-holding. No context switching from the user.
- **Senior-level discipline**: Find root causes. No temporary fixes. No laziness.
- **Rollback on failure**: If a fix breaks verification, rollback immediately and re-plan.

## Task Management

1. **Session Start**: Review `tasks/lessons.md` for entries relevant to the current project/task.
2. **Plan First**: Write plan to `tasks/todo.md` with checkable items.
3. **Verify Plan**: Check in before starting implementation.
4. **Track Progress**: Mark items complete as you go.
5. **Explain Changes**: High-level summary at each step.
6. **Verify Before Done**: Run `scripts/verify.sh` or manually run tests/diffs.
7. **Document Results**: Add review section to `tasks/todo.md`.
8. **Capture Lessons**: Update `tasks/lessons.md` after corrections. Tag with metadata.

## Helper Scripts

The `/scripts/` directory contains automation helpers. Reference them in your workflow:

- **`scripts/init.sh`** — Scaffolds `tasks/todo.md` and `tasks/lessons.md` on first clone.
- **`scripts/lesson-updater.sh`** — Scans `tasks/lessons.md` for recurring patterns (3+ occurrences) and proposes rule amendments to `skills.md`.
- **`scripts/verify.sh`** — Pre-PR verification: runs tests, checks for uncommitted changes, validates that `tasks/todo.md` has a plan.

Use these for all sessions to ensure consistency.
