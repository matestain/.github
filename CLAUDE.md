# CLAUDE.md — MATESTAIN Organization

This file provides organization-wide context for Claude Code and any AI assistant working within the MATESTAIN GitHub organization. Read this before touching any repo.
For technical standards, stack details, and architecture decisions, refer to the CLAUDE.md in each specific repo.

---

## What is MATESTAIN?

**MATESTAIN** (_Making Automation Through Engineering — Software Trusted Across Industries & Nations_) is an Argentine industrial automation and software company founded by Lucas Viera.

The name is a deliberate double meaning: a technical acronym and a cultural reference to mate — the Argentine drink that symbolizes sharing, trust, and long sessions of focused work. The "stain" is the mark left by real engineering.

**We are not a consulting firm. We are a technology company that happens to know what a PLC smells like when it's burning.**

---

## Business Model

### Layer 1 — Field Engineering Services

Direct industrial services to end clients (bypassing agencies):

- PLC programming (Siemens S7, Rockwell)
- Robotics and end-of-line automation
- Field commissioning and startup
- Remote support and after-sales
- Operator training

Primary industries: food & beverage, dairy, packaging, steel.
Primary geographies: Latin America, USA, Europe (project-based travel).

### Layer 2 — Software Products (SaaS / Tools)

Scalable digital products for industrial environments:

- **Plantwise** — unified industrial plant intelligence platform (flagship product)
- Future products TBD

Layer 1 funds the company while Layer 2 grows. The long-term exit is Layer 2 independence.

---

## Vision

MATESTAIN in 5–10 years is a company with multiple industrial programmers, engineers, and software developers. It offers:

- Multiple SaaS and tooling products for industrial operators and engineers
- Tailor-made automation projects (PLC, robotics, SCADA) for clients
- Field commissioning, remote support, and after-sales services
- Open source contributions to the industrial automation community

**Everything we build is open source by default** unless there is a specific contractual reason not to be. Transparency builds trust. Trust builds clients.

Cloud-based infrastructure, globally distributed team, Argentine roots.

---

## Organization Structure

```
github.com/matestain/

├── .github              # Org defaults (this repo)
├── plantwise            # Flagship SaaS product
├── tidemark             # Personal finance app
├── brand                # Visual identity, logo, assets, templates
├── website              # matestain.com public landing page
├── docs                 # Public cross-product documentation
├── infra                # Terraform, Docker, cloud configs (private)
├── internal-tools       # Scripts, automations, internal utilities
├── project-template     # Base template for new client projects
└── [cc####-client-name] # Client projects — private, one repo each
```

**Repo visibility rules:**

- Products → Public (open source)
- Client projects → Private (NDA / client IP)
- Brand, website, docs → Public
- Infra → Private (security)
- Internal tools → Private

---

## Branching & Commit Conventions

```
main          — production-ready, protected
develop       — integration branch
feature/xxx   — new features
fix/xxx       — bug fixes
docs/xxx      — documentation only
chore/xxx     — tooling, deps, config
```

Commit messages follow Conventional Commits:

```
feat(scope): short description
fix(scope): what was broken
docs(scope): what was documented
chore(scope): tooling, deps, config
refactor(scope): no behavior change
test(scope): adding or fixing tests
```

Examples:

```
feat(plantwise): add OPC-UA connection diagnostics
fix(brand): correct logo export DPI
docs(.github): update contributing guidelines
```

---

## Repo Conventions

Every repo in this org must have:

- `README.md` — what it is, how to run it, who it's for
- `CLAUDE.md` — AI context specific to that repo
- `CONTRIBUTING.md` — how to contribute (can reference this org-level file)
- `.gitignore` — appropriate for the stack

Client project repos additionally require:

- `docs/scope.md` — project scope and deliverables
- `docs/contacts.md` — client contacts (gitignored from public forks)

---

## Key People

| Person      | Role                   |
| ----------- | ---------------------- |
| Lucas Viera | Founder, Lead Engineer |

---

## Important Links

- Website: https://matestain.com (in development)
- Domain registrar: Cloudflare
- Trademark: INPI Argentina (Class 42 filed), USPTO pending
- Primary dev machine: AI-WORKSTATION (i7-11700K, RTX 4060Ti, Windows 11)
- Travel machine: Lenovo Legion 7i Pro (Ultra 9 275HX, RTX 5080, Windows 11)

---

## What We Don't Do

- We don't patch. We fix properly.
- We don't write code without understanding it.
- We don't deploy without knowing what we're deploying.
- We don't lock clients into proprietary systems when open standards exist.
- We don't use microservices because they sound cool.

---

_Last updated: April 2026_
_Maintained by: Lucas Viera — lucas@matestain.com_
_hello@matestain.com_
