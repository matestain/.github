# Contributing to MATESTAIN

Thank you for your interest in contributing to MATESTAIN projects.
This document covers organization-wide contribution guidelines.
Individual repos may have additional rules in their own `CONTRIBUTING.md`.

---

## Before You Start

1. Read the `CLAUDE.md` in this repo for full organization context.
2. Read the `CLAUDE.md` in the specific repo you're contributing to.
3. Check open issues — your idea or bug may already be tracked.

---

## Types of Contributions

| Type                         | Welcome?     | Notes                  |
| ---------------------------- | ------------ | ---------------------- |
| Bug fixes                    | ✅ Always    | Open a fix/xxx branch  |
| Feature proposals            | ✅ Yes       | Open an issue first    |
| Documentation                | ✅ Always    | Docs are never "done"  |
| Industrial protocol adapters | ✅ Yes       | Must be read-only safe |
| Client project code          | ❌ No        | Private repos, NDA     |
| Infra changes                | ⚠️ Ask first | Security-sensitive     |

---

## Workflow

### 1. Fork or branch

For external contributors: fork the repo, work on your fork.
For team members: create a branch from `develop` using the convention:

```
feature/short-description
fix/what-is-broken
docs/what-is-documented
chore/what-is-maintained
```

### 2. Write your code

- Follow the code style in `CLAUDE.md` (Black, Ruff, ESLint, Prettier)
- Add or update tests for any logic changes
- Update documentation if behavior changes
- No commented-out code in PRs

### 3. Commit

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(scope): short description
fix(scope): what was broken and how it's fixed
docs(scope): what was documented
chore(scope): tooling, deps, config
refactor(scope): no behavior change
test(scope): adding or fixing tests
```

Examples:

```
feat(plantwise): add Modbus RTU connection diagnostics
fix(tidemark): correct currency conversion rounding
docs(brand): add logo usage guidelines
```

### 4. Open a Pull Request

- Use the PR template provided
- Link the related issue with `Closes #123`
- Keep PRs focused — one concern per PR
- PRs against `main` require at least one review

---

## Industrial Protocol Safety

This is non-negotiable for any code that interacts with industrial systems:

- **Read-only by default.** No writes to PLCs, SCADA, or field devices
  without explicit, documented, operator-confirmed authorization.
- **No auto-reconnect loops** that could mask a lost connection on a live system.
- **Timeouts and error states must be explicit.** Silent failures are dangerous.
- If you're unsure whether something is safe in a plant environment, ask.

---

## Issues

Use the appropriate issue template:

- **Bug Report** — something is broken
- **Feature Request** — something should exist
- **Client Project** — new project intake (internal team only)

Please search before opening — duplicates slow everyone down.

---

## Code of Conduct

We work in environments where bad code can stop a production line or injure someone.
We take our work seriously. We expect the same from contributors.

- Be direct and technical. Ego doesn't ship products.
- Disagreements about architecture are healthy. Personal attacks are not.
- If you don't know something, say so. We'd rather have an honest "I don't know"
  than a confident wrong answer in a commissioning document.

---

## Questions?

Open a Discussion in the relevant repo, or reach out at _lucas@matestain.com_ or _hello@matestain.com_.

---

_MATESTAIN — Making Automation Through Engineering_
