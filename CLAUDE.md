# CLAUDE.md — MATESTAIN Organization

This file provides organization-wide context for Claude Code and any AI assistant working within the MATESTAIN GitHub organization. Read this before touching any repo.
For technical standards, stack details, and architecture decisions, refer to the CLAUDE.md in each specific repo.

---

## What is MATESTAIN?

**MATESTAIN** (_Modernizing Automation Through Engineering — Software Trusted Across Industries & Nations_) is an Argentine industrial automation and software company founded by Lucas Viera.

The name is a deliberate double meaning: a technical acronym and a cultural reference to mate — the Argentine drink that symbolizes sharing, trust, and long sessions of focused work. The "stain" is the mark left by real engineering.

**We are not a consulting firm. We are a technology company that happens to know what a PLC smells like when it's burning.**

---

## Business Model

### Layer 1 — Engineering Services

> **Naming note:** Layer 1 is called "Engineering Services" externally — not "Field Engineering Services". Field presence is how we deliver, not what we sell.

MATESTAIN offers six service packages under Layer 1, built from underlying Service Units (SU-01
through SU-06 — see `brand/templates/proposal/src/03-commercial-quote.md` for the full quoting logic).
Mechanical engineering is always out of scope — parallel partner model only, no exceptions.

### Service Packages

| Package | Includes | Typical Client |
|---|---|---|
| **Full Control** | Control Engineering (SU-03) + Software Development (SU-02) + Field Commissioning (SU-01) | Mechanical integrator without control capacity |
| **Software & Field** | Software Development (SU-02) + Field Commissioning (SU-01) | Integrator with own electrical team, no software house |
| **Field Services** | Field Commissioning only (SU-01) | Integrator needing trusted field resource — current primary revenue source |
| **Technical Services** | Technical Hours, T&M (SU-04) | Bounded engineering task (e.g. PLC logic migration) without onsite commissioning |
| **Remote Support** | Remote Support (SU-05) | Post-SAT support, no travel |
| **Field Support** | Field Support (SU-06) | Post-SAT support requiring an onsite visit |

### Control Engineering

Selection and specification of complete control hardware architecture (PLC, VFD, safety, HMI,
network). MATESTAIN scope ends at the control system boundary.

**Electrical subcontractor model (two options — agreed per project before proposal):**
- **Integrated:** MATESTAIN invoices full scope. Electrical partner is subcontractor.
  MATESTAIN margin: 10–15% markup on electrical cost.
- **Parallel:** Client contracts electrical firm directly. Separate scopes and invoices.
  MATESTAIN has zero liability on electrical scope. Preferred when electrical scope is large
  or complex.

Electrical panel design, construction, and documentation (IEC/NEC) is always subcontracted
to a certified partner — never MATESTAIN's direct deliverable.

### Software Development

PLC and robot programming from scratch, using base program templates per machine type.

**Platforms:**
- PLC: Siemens TIA Portal (S7-300/1200/1500), Rockwell Studio 5000 (ControlLogix,
  CompactLogix)
- Robotics: KUKA (WorkVisual / KRL), Yaskawa / Motoman (MotoPlus / Inform)

> **Fanuc and OMRON are not part of the current offering.** Fanuc: one from-scratch project
> only. OMRON: zero from-scratch experience. Both are candidates for future platform expansion
> once sufficient project depth exists.

### Field Commissioning

Onsite startup, testing, and handover. Available standalone or as the closing phase of any
other package.

### Pricing Model (reference — full detail in `company/pricing/`)

| Service | Model |
|---|---|
| Field Commissioning | Day rate — 10h/day, Mon–Sat, region-adjusted, all-inclusive except flights |
| Software Development | Fixed price per machine type + overage rate for client-caused scope changes |
| Control Engineering | Base fee per scope tier + hourly for extended scope |

**Travel & standby policy:**
- Standby days: **100% of day rate, always.** Cause documented for negotiation leverage.
- International travel days: 75% of day rate.
- Local mobility (hotel → site > 15 min): billed at travel day rate.
- Flights: always a separate line item at actual cost.
- Visa / travel documentation: always a separate line item at actual cost.

Primary industries served: food & beverage, dairy, packaging, steel.
Primary geographies: Latin America, USA, Europe (project-based travel).

### Layer 2 — Software Products (SaaS / Tools)

Scalable digital products for industrial environments:

- **Plantwise** — unified industrial plant intelligence platform (flagship product)
- **fieldwork** — CMMS: maintenance management, work orders, spare parts (separate product, not a Plantwise module)
- Future products TBD

Layer 1 funds the company while Layer 2 grows. The long-term exit is Layer 2 independence.

### Planned Extensions (post-LLC formation)

- **Hardware resale:** PLC, VFD, safety, HMI components. Margin opportunity vs. integrator
  procurement. Pending LLC formation and distributor agreements.
- **Layer 1 → Layer 2 upsell bridge:** Full Control and SW+Field packages will include a
  complimentary Plantwise subscription (6–12 months) as a conversion path into recurring
  SaaS revenue.
- **Platform expansion:** ABB and Fanuc to be added once sufficient from-scratch project
  depth is established.

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

├── .github/                    # Org defaults — this repo, org-level CLAUDE.md
├── brand/                      # Visual identity, logos, assets, templates (public)
├── company/                    # Private: pricing, services, engineering standards
│   ├── pricing/                # Pricing reference and client registry
│   ├── services/               # Services provided, explained
│   └── standards/              # Engineering standards (naming, safety, network, HMI, etc.)
├── docs/                       # Public cross-product documentation
├── infra/                      # Terraform, Docker, cloud configs (private)
├── internal-tools/             # Scripts, automations, n8n social workflows (private)
│   └── social/                 # n8n workflow for social media
├── plantwise/                  # Flagship SaaS product (private during development)
├── project-template/           # Base template for client automation projects (private)
├── website/                    # matestain.com — landing page, Cloudflare Pages (public)
└── [client-code-client-name]/  # Client folder (for organization purposes)
    └── [project-name]/         # CLient projects — private, one repo each
```

**Repo visibility rules:**

- `brand`, `docs`, `website` → Public
- `company`, `infra`, `internal-tools`, `project-template` → Private
- Client projects (`cc####-*`) → Private (NDA / client IP), no exceptions
- `plantwise` → Private during development, public when released

---

## Engineering Standards

All engineering decisions for Layer 1 projects are governed by the standards in `company/standards/`. These are not suggestions — they are the baseline for every deliverable.
For a condensed reference, see `company/standards/CLAUDE.md`.

Non-negotiable rules (apply everywhere, no exceptions):
- English only in all code identifiers and comments
- LAD default, SCL only when justified (math/arrays/drive libs), FBD never
- No alarm implemented without alarm register entry first
- No post-FAT change without written client authorization
- OPC-UA anonymous access always disabled
- Remote access via VPN only — direct port forwarding never
- PLc is the absolute safety floor — no project delivers below PLc

---

## Branching & Commit Conventions

```
main          — production-ready, protected
develop       — integration branch (dev for client projects)
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
tune(scope): parameter or setpoint adjustment (industrial projects)
export(scope): diffable export commit, no logic change (TIA XML, L5X, KRL)
release: version bump + changelog update
```

Examples:

```
feat(plantwise): add OPC-UA connection diagnostics
fix(brand): correct logo export DPI
feat(cc0001/tia/valv): add valve cluster sequence logic
tune(cc0023/kuka): reduce approach speed to 65% on layer 5
export(cc0001/tia): XML export v0.3.0
release: bump to v1.0.0 — FAT passed 2025-03-14
```

---

## CLAUDE.md Hierarchy and Repo Conventions

Every repo in this org must have:

- `README.md`  — what it is, how to use it, who it's for
- `CLAUDE.md`  — AI context specific to that repo, references this org-level file
- `.gitignore` — appropriate for the stack

CLAUDE.md files are hierarchical — each level adds context without repeating the level above:

`.github/CLAUDE.md`           — org-wide context (this file)
`company/standards/CLAUDE.md` — condensed standards reference
`project-template/CLAUDE.md`  — template structure, naming, module registry
`cc####-*/CLAUDE.md`          — project-specific context (machine, client, scope)

Always read from top to bottom before working in any repo.

Client project repos additionally require before any work starts:

- `docs/scope.md` — agreed scope, deliverables, out-of-scope, timeline, change orders
- `docs/contacts.md` — client contacts, site supervisor, emergency contact
> **`contacts.md` must always be in `.gitignore`** — never committed to any remote

---

## Technology Stack

**Layer 1 — Industrial:**
- Siemens TIA Portal V20 (S7-1200, S7-1500, SIMATIC Safety F-CPU)
- Rockwell Studio 5000 (CompactLogix, ControlLogix, GuardLogix)
- KUKA WorkVisual / KRL (KRC4, KRC5)
- Yaskawa / Motoman (YRC1000, INFORM)
- WinCC Comfort, WinCC Unified, FactoryTalk View ME/SE
- Protocols: PROFINET, EtherNet/IP, OPC-UA, Modbus TCP

**Layer 2 — Software:**
- Backend: Python 3.12+, FastAPI, SQLAlchemy 2.0 (async), Alembic
- Frontend: React 18+, TypeScript, Vite, Tailwind CSS, shadcn/ui, Zustand
- Database: PostgreSQL 16 + TimescaleDB (cloud), SQLite + aiosqlite (edge)
- Industrial protocols: asyncua (OPC-UA), pymodbus (Modbus), paho-mqtt (MQTT)
- AI/LLM: Anthropic Claude API (cloud), rule-based fallback (edge/offline)
- Auth: JWT tokens + API keys
- Deployment: Docker Compose (cloud), PyInstaller/zipapp (edge standalone)
- Testing: pytest + pytest-asyncio, httpx (API), Playwright (E2E)
- Linting: ruff + mypy strict
- Package management: uv (migrating from conda)
- Brand tooling: mistune (Markdown→HTML), pyyaml (project.yaml), openpyxl (BOM Excel)
- OPC-UA as the primary data interface between Layer 1 and Layer 2

---

## Key People

| Person | Role |
|---|---|
| Lucas Viera | Founder, CEO, Lead Engineer |

---

## Important Links and Infrastructure

- Website: https://matestain.com (landing page live, functional email drop — see `website/CLAUDE.md`)
- Domain: matestain.com (Cloudflare Registrar, auto-renewal enabled)
- Hosting: Cloudflare Pages, Git-connected to matestain/website repo, branch main, auto-deploy on push
- Google Workspace Business Starter active, MX records pointing to Google, Cloudflare Email Routing deactivated, DKIM verified
- Emails: lucas@matestain.com (Founder); hello@matestain.com (Main communications channel)
- Social handles: @matestain (LinkedIn, GitHub, Instagram, YouTube), @matestain_ (X — handle suspended, fallback)
- Trademark: INPI Argentina (Class 42 filed April 6, 2026), USPTO pending
- Primary dev machine: AI-WORKSTATION (i7-11700K, RTX 4060Ti, Windows 11)
- Travel machine: Lenovo Legion 7i Pro (Ultra 9 275HX, RTX 5080, Windows 11)
- n8n workflow: self-hosted on AI-WORKSTATION — see `internal-tools/social/`

---

## What We Don't Do

- We don't patch. We fix properly.
- We don't write code without understanding it.
- We don't deploy without knowing what we're deploying.
- We don't lock clients into proprietary systems when open standards exist.
- We don't use microservices because they sound cool.
- We don't implement alarms without adding them to the register first.
- We don't start post-FAT changes without written client authorization.
- We don't expose PLCs directly to the internet.

---

## Legal & Corporate Structure

Current status: Lucas Viera operates as **Monotributista** in Argentina, issuing export invoices (facturas de exportación) for international clients and facturas A for Argentine clients. This is sufficient for current revenue levels.

INPI Argentina Class 42 filed April 6, 2026
Reference number: 3780572
Denominativa (wordmark only — no logo yet)
Class 37 (industrial installation & maintenance) deferred — separate filing required

**Next step — Wyoming LLC:**
When Layer 1 direct clients or Layer 2 revenue materialize, a Wyoming LLC will be formed as the operating entity above the Monotributista layer. Key reasons: professional presentation to international clients, personal asset protection, single-member allowed, ~$200-300/year total cost. See `company/legal.md` for formation requirements and Argentine tax implications.

Delaware C-Corp is deferred until external investment becomes relevant.

**NCA — Automatica Services LLC (Delaware):**
Lucas operates under a Non-Compete Agreement with Automatica Services LLC (current agency) that restricts direct engagement with their client portfolio for 2 years post-termination. Key clause (5.4): restriction applies only to services identical to Automatica's scope (field commissioning, mechanical/electrical installation, machine startup). Software products, SaaS, dashboards, and digital services are explicitly not covered.

Pre-NCA contacts available for Layer 2 outreach (no restriction):
- Royal Canin (MARS) — Argentina plants
- Saputo — Argentina plants
- Unilever — Argentina plants

NCA will not be rescinded until stable parallel income exists (Layer 1 direct or Layer 2). Penalty clause: USD 30,000 cash.

---

## Go-To-Market

**Layer 1 — Direct clients:**
Target: industrial manufacturers not covered by NCA. Entry point: existing pre-NCA contacts for Layer 2 validation first, Layer 1 direct when NCA is resolved.

**Layer 2 — Products:**
- Primary channel: LinkedIn (authority content — technical, first-person, field experience)
- Secondary channel: Instagram (humanizes the brand, backstage of field work)
- Warm outreach: existing contacts for prototype feedback, not sales pitches
- Cold outreach: avoided — authority-first strategy

**Content pipeline:**
Semi-automated via n8n. Lucas provides raw input (voice notes, bullet points from field experience). AI generates platform-specific content. Repurposing across platforms is automatic. See `internal-tools/social/` for pipeline topology, n8n setup, and publishing cadence.

**Social — First posts published:**
- LinkedIn company page + Lucas's personal profile — published
- X — published
- Instagram — published
- GitHub README — updated with full industry stack

---

## Product Pipeline

### Plantwise (flagship — Layer 2)
Unified industrial plant intelligence platform. Starts as a commissioning engineer's personal toolkit and grows into a production-grade SaaS for mid-market manufacturers. "plantwise" is a code name, no official name has been assigned.

**Standards-first architecture:**
ISA-95 (equipment hierarchy + state model), ISA-88 (batch control), IEC 62443 (cybersecurity zones/levels), PackML/ISA-TR88.00.02 (machine state model with OPC-UA companion spec).

**Module roadmap:**
- Phase 1 (months 1-3): Protocol diagnostics (S7 scanner, includes PUT-GET/OPC-UA/Modbus scanner) + Commissioning governance (checklists, sign-offs, compliance docs)
- Phase 2 (months 4-8): Root cause analysis (AI-guided 5-Why/Fishbone) + Batch record compliance & traceability (FSMA/FDA, food first → pharma later). Operator condition reports — manual observation of visual degradation (wear, corrosion, dirt accumulation, leaks). Mobile-first UI, photo capture. Feeds the future predictive module. Schema migration-ready from Phase 1.
- Phase 3 (months 9-18): OEE & production metrics + Downtime capture (NLP reason codes) + Multi-channel delivery (WhatsApp/SMS/QR) + Sensor calibration-as-a-service
- Phase 3+: Adaptive maintenance planning. Correlates sensor data (diagnostics), operator observations (conditions), and fault history (rca) to adapt maintenance intervals. Depends on minimum 3-6 months of labeled historical data — do not implement before data foundation exists.
>Out of scope — fieldwork: Work order management, spare parts inventory (pañol), purchase orders, and maintenance scheduling coordinated with production calendars constitute the domain of **fieldwork** (separate MATESTAIN product). This is not a Plantwise module. Plantwise provides condition data via API; fieldwork consumes it.

**Key design constraints:**
- Edge-first: every core function works offline (SQLite on-site, PostgreSQL in cloud)
- Read-only with respect to industrial protocols — never writes to PLCs or instruments
- Modules communicate only through event bus — no cross-module imports
- Solo-dev sustainable: monorepo, single deployable, no microservices, no Kubernetes

**Stack:**
Python 3.12+ (FastAPI, asyncua, pymodbus), React + TypeScript (PWA), SQLAlchemy 2.0 async, PostgreSQL + TimescaleDB (cloud), SQLite (edge), Anthropic Claude API for NLP features.

**Testing strategy:**
Protocol simulators for CI + real-world data capture during commissioning trips. Every field deployment is a testing opportunity. Field validation notes: see `plantwise/docs/field-validation.md`.

Full architecture in `plantwise/docs/architecture.md`.
Full Claude Code instructions in `plantwise/CLAUDE.md`.

### Candidate MVP — Plant Floor Digital Logbook
Identified pain from direct plant experience across Royal Canin, Saputo, Unilever, and others:
- Operators don't know what happened in the previous shift
- No one knows real line downtime (vs. reported downtime)
- Maintenance learns about problems late or never
- Problems repeat because nothing was documented
- Spare parts leave the stockroom with no record of why

**Proposed entry point:** Digital spare parts checkout at the stockroom (pañol). Technician must log the failed equipment and fault description before withdrawing any part. Zero voluntary behavior change — compliance is enforced by process. Generates automatic fault history per equipment.

**Secondary entry point:** Shift handover digital log for production supervisors. Replaces paper and WhatsApp. Supervisor sees consolidated plant status without leaving the desk.

**v1 scope:** No OT network integration. Tablet at stockroom + web dashboard. Manual data entry only. Target buyer: Production Manager. Price range: $300–800/month per plant.

Integration roadmap: v2 consumes existing ERP exports, v3 introduces OPC-UA connection to PLCs.

**Note:** This candidate MVP maps directly to Plantwise modules: Downtime Capture (Phase 3, NLP-powered reason code classification) and Delivery (Phase 3, WhatsApp/SMS shift reports). If Plantwise Phase 1-2 validates well, this MVP may launch as a Plantwise module rather than a standalone product. The spare parts checkout concept remains a standalone candidate — it doesn't map to any current Plantwise module.

### Opportunity Discovery Tool (internal)
Automated overnight pipeline that scrapes pain signals across forums, review sites, and communities, scores opportunities by revenue potential and competition level, and generates briefings + skeleton prototypes. Parameters refined toward industrial manufacturing niches. High-scoring results feed the product roadmap. See `internal-tools/opportunity-discovery/`. "opportunity discovery Tool" is a code name, no official name has been assigned.

---

## Current Status — May 2026

**What's active:**
- Layer 1: operating as Monotributista, currently under agency model (Automatica NCA active)
- Layer 2: Plantwise in active development — Phase 1 in progress
- Website live, social channels published, trademark filed (INPI Class 42)
- Content pipeline semi-automated via n8n

**What's in progress:**
- 29 registered project templates (3 defined — T-STD-001, 002, 004 — 26 planned, see `project-template/TEMPLATE-MASTER-LIST.md`)
- Plantwise Phase 1 modules (protocol diagnostics + commissioning governance)
- Wyoming LLC formation — pending first direct client or Layer 2 revenue trigger

**What's pending (priority order):**
1. Base client contract
2. Payment conditions document
3. Wyoming LLC formation
4. NCA exit strategy definition
5. Plantwise pricing (Layer 2)
6. Class 37 trademark filing (separate from Class 42)

_Commercial proposal template — done, see `brand/templates/proposal/`._

**NCA status:**
Active. Automatica Services LLC (Delaware). Restriction: field commissioning / mechanical / electrical / machine startup services to their client portfolio only. Software, SaaS, and digital services are explicitly not restricted. Pre-NCA contacts (Royal Canin/MARS, Saputo, Unilever — Argentina) available for Layer 2 outreach immediately.

---

## Pricing — Canonical Reference

One known inconsistency existed between documents — this is the resolved canonical version:

| Situation | Rate |
|---|---|
| Standby days (on-site, waiting on client/other trades) | **100% of day rate** |
| International travel days (airport → site or return) | **75% of day rate** |
| Local mobility (hotel → site > 15 min) | Travel day rate |
| Flights | Always separate line item at cost |
| Visa / travel documentation | Always separate line item at cost |

_Last updated: May 2026_
_Maintained by: Lucas Viera — lucas@matestain.com | hello@matestain.com_
