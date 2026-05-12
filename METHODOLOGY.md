# VCaaS™ Methodology — The Six Modules

> Conceptual overview of the six-module VCaaS™ engagement.
> Implementation details, templates, and deployable artifacts are part of the full kit — see [README.md](README.md) for how to access it.

---

VCaaS™ is delivered in six modules, organized into three phases. Each module produces a signed-off artifact that becomes part of the organization's canonical context architecture. Modules are sequenced: each one depends on the work of the previous module.

| Phase | Module | Theme |
|---|---|---|
| **Audit & Architect** | 1 | Context Landscape Audit |
| | 2 | Architecture Design |
| **Govern & Own** | 3 | Ownership & RACI |
| | 4 | Zones, Propagation, and Approvals |
| **Operate & Maintain** | 5 | Migration & Deployment |
| | 6 | Maintenance, Drift Detection, and Health |

---

## Phase 1 — Audit & Architect

The goal of Phase 1 is to **understand the current state** of AI context inside the organization, then **design the target architecture**. No code moves yet. No files are written. The output of Phase 1 is a paper architecture that everyone has agreed to.

### Module 1 — Context Landscape Audit

**Question this module answers:** *Where does company knowledge actually live today, and where are the fractures?*

Every team using AI tools has accumulated context in many places: Notion pages, Google Docs, Slack canvases, internal wikis, README files, individual prompt libraries, half-finished CLAUDE.md files in private repos. Module 1 inventories all of it.

**What gets produced:**

- A **Context Landscape Map**: every place company knowledge lives today, mapped to a canonical taxonomy. File paths, owners, word counts, source platform.
- A **Fragmentation Report**: where the same answer lives in multiple, conflicting places. The #1 cause of AI hallucination. Ranked by severity.
- A **Risk Assessment**: which fragments could cost money, break an integration, or be noticed outside the team if they were left to drift further.

**Why it matters:** You cannot architect for a system you have not mapped. Skipping Module 1 leads to architectures that look elegant on paper but fail at the first encounter with the existing mess.

### Module 2 — Architecture Design

**Question this module answers:** *What is the target shape of our context governance system, and how do we name everything in it?*

Module 2 takes the audit findings and designs the target system: the three-tier hierarchy, the folder structure, the inheritance rules, the naming conventions, and the migration plan to get from current state to target state.

**What gets produced:**

- An **Architecture Blueprint**: the signed-off three-tier hierarchy, folder structure, inheritance rules, file inventory, and architecture decisions log.
- A **Naming Convention Guide**: the reference every team member uses before creating any file. Five file types, ten non-negotiable naming rules, twelve good-vs-bad examples, the approved domain taxonomy, a decision tree, and a quick-reference card.
- A **Context Hierarchy Diagram**: the visual map of the full system, suitable for printing. The diagram is referenced by every other artifact and shows where each file lives, who owns it, and how inheritance flows.
- A **Migration Plan**: the three-pass operational plan to move from current fragmented state to the clean architecture — consolidation, gap fill, orphan cleanup — with timelines, validation checks, and sign-off blocks.

**Why it matters:** Without a written architecture, every new file becomes a one-off judgment call. Within six months, the system is back to fragmentation. The Blueprint is the artifact that prevents that.

---

## Phase 2 — Govern & Own

Phase 2 is the **governance layer**. Where does authority live? What can AI do on its own? What requires a human? Phase 2 answers those questions explicitly, in writing, with named owners.

### Module 3 — Ownership & RACI

**Question this module answers:** *Who owns what, and who has the authority to approve a change?*

Every file in the system needs a named Responsible and a named Accountable. No exceptions. Files without an owner are orphans, and orphans are the largest single source of context rot.

**What gets produced:**

- A **Full RACI Matrix** for every Tier 1 file and every Tier 2 folder. Specifically: who is Responsible (does the work), Accountable (approves the work), Consulted, and Informed.
- An **Owner Onboarding Pack**: what it means to own a file, what review cadence is required, what to do when an AI proposes a change, how to write `APPROVED, PROCEED`.
- An **Escalation Ladder**: if the owner is unavailable, who has fallback authority? For how long?

**Why it matters:** Ambiguous ownership produces ambiguous AI behavior. If three people might own a file, none of them feel responsible for keeping it current. Module 3 forces the answer.

### Module 4 — Zones, Propagation, and Approvals

**Question this module answers:** *What is AI allowed to change autonomously, and what requires a human in the loop?*

Module 4 is where the **protected zone** and the **autonomous zone** are defined for the specific organization. The defaults are inherited from the framework, but every organization has industry-specific additions: regulated data fields, jurisdiction-specific compliance language, niche pricing rules, contractual constraints.

**What gets produced:**

- A **Zones Registry**: the canonical list of which files are protected and which are autonomous, with a justification for each protected category.
- An **Approval Workflow**: the exact flow a change request takes — from AI-drafted proposal, to owner review, to the literal `APPROVED, PROCEED` signal that unblocks the agent.
- A **Propagation Protocol**: when a Tier 1 file changes, how does the change ripple to Tier 2 and Tier 3 files that depend on it? Who is notified? What re-reviews are triggered?
- **Refusal Patterns** for agents: how an AI should respond when asked to do something in a protected zone, in a way that does not feel like a brick wall to the human asking.

**Why it matters:** Without explicit zones, AI is either too cautious (and useless) or too aggressive (and dangerous). Module 4 makes the boundary specific, documented, and enforceable.

---

## Phase 3 — Operate & Maintain

Phase 3 is **execution and longevity**. The system exists on paper after Phase 2. Phase 3 makes it live, and then keeps it healthy.

### Module 5 — Migration & Deployment

**Question this module answers:** *How do we move from current scattered state to the new governed system without losing knowledge or breaking AI agents that are already running?*

Module 5 takes the Migration Plan from Module 2 and executes it. The migration is sequenced by risk: the highest-fragmentation, highest-cost topics move first.

**What happens:**

- **Foundation files** (Tier 1 root, guidelines, governance docs) are populated first. Owners are assigned.
- **Top-risk fragmented topics** are consolidated into skills files in priority order. Old scattered sources are archived, not deleted.
- **Agents are registered** in the agent registry before they are allowed to run in production. Agents not in the registry are, by definition, not authorized.
- **Teams, projects, and personal folders** are populated last, on the team's own schedule.
- **The first reviews** are scheduled before the engagement ends — weekly, monthly, quarterly cadences are calendared and assigned.

**Why it matters:** A migration without sequencing is a chaotic copy-paste exercise that produces a new flavor of fragmentation. Module 5 is the controlled rollout.

### Module 6 — Maintenance, Drift Detection, and Health

**Question this module answers:** *How do we keep the system healthy six months from now, when the people who built it have moved on to other work?*

A VCaaS™ deployment is not "set and forget." Module 6 installs the rituals, the metrics, and the drift detection signals that keep the system from rotting.

**What gets installed:**

- A **Health Scorecard**: a composite 0–10 score across seven dimensions — Coverage, Freshness, Ownership, Drift, Fragmentation, AI Compliance, Adoption. Reviewed at every weekly meeting.
- A **Review Cadence**: weekly (30 min), monthly (60 min), quarterly (3–4 hour strategic review with full re-audit).
- **Drift Detection Signals** (see [DRIFT-SIGNALS.md](DRIFT-SIGNALS.md)): the specific symptoms that indicate context is rotting, scored by severity.
- A **Violation Log**: every time an AI agent crosses a protected-zone boundary, the incident is logged, root-caused, and used to patch the agent's config.
- **Annual Re-Certification**: every agent re-justifies its existence yearly; every Tier 1 file is re-reviewed for relevance.

**Why it matters:** Context rot is not a sudden event. It is gradual drift that becomes visible only when AI is already producing wrong answers in production. Module 6 makes drift visible early, while it is still cheap to fix.

---

## How the modules fit together

Modules build sequentially. Each one is gated by the previous one's signed-off artifact.

```
Module 1 ──► Module 2 ──► Module 3 ──► Module 4 ──► Module 5 ──► Module 6
  Audit       Design       Own           Govern       Deploy       Maintain
   │            │            │             │            │             │
   ▼            ▼            ▼             ▼            ▼             ▼
Landscape   Blueprint    RACI matrix   Zones         Live           Health
map +       + naming     + owner       registry +    system,        scorecard,
fragment    convention   onboarding    approval      first          drift
report      guide +      pack +        workflow +    reviews        signals,
+ risk      hierarchy    escalation    propagation   calendared,    review
assessment  diagram +    ladder        protocol +    agents         cadence,
            migration                  refusal       registered     violation
            plan                       patterns                     log
```

The modules can be compressed (a small team running through all six in two weeks) or stretched (a large enterprise running each module over a quarter). The sequence does not change.

---

## What's not in this document

This is the **conceptual** description of the methodology. The full engagement includes:

- The working `CLAUDE.md` templates at every tier.
- The five `guidelines-*.md` files with default content.
- The skill files for finance, sales, operations, support, marketing, HR.
- The proposed-changes protocol with worked examples (approved, pending, rejected).
- The discovery-agent prompt that runs against the existing context landscape.
- The health scorecard with the trend tracker.
- The slash command and prompt for `/vcaas-classify`.
- The four Module 1 & 2 deliverable templates (Architecture Blueprint, Naming Convention Guide, Context Hierarchy Diagram, Migration Plan).
- The 30-day day-by-day deployment guide.

Those artifacts are part of the paid VCaaS™ engagement. To access them, visit [thecfointel.com](https://thecfointel.com).

---

*VCaaS™ — Vibecoding as a Service*
*Winventions LLC · [thecfointel.com](https://thecfointel.com)*
*USPTO Trademark Serial No. 99694926*
