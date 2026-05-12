# VCaaS™ Reference Architecture

> An illustrative, public example of how AI context governance can be structured under VCaaS™.
> This is **not** the deployable layout. Production deployments vary by organization size, tool stack, regulatory environment, agent topology, and operating model. The full deployable kit — with working templates, calibrated zones, and client-specific structures — is part of the paid engagement. See [README.md](README.md).

---

## Illustrative Reference Architecture

This is a simplified public example of how context governance can be structured. Production deployments vary by organization, tool stack, regulatory environment, and operating model. Treat the layout below as a conceptual reference, not a copy-paste skeleton.

```
<organization-root>/
│
├── CLAUDE.md                              ← Tier 1 root — the organization brain
│                                            (identity, mission, principles, inheritance rules,
│                                             non-negotiable AI rules, where-to-find-what map)
│
├── LICENCE.md                             ← Licence governing the deployment
│
├── vcaas/                                 ← THE GOVERNANCE LAYER
│   │                                        the files that police the rest of the system
│   │
│   ├── VCAAS-README.md                    ← Plain-English user manual (day-1 reading)
│   ├── VCAAS-ZONES.md                     ← Protected vs Autonomous registry
│   ├── VCAAS-OWNERSHIP.md                 ← RACI matrix for every file
│   ├── VCAAS-HEALTH.md                    ← 0–10 composite health scorecard
│   ├── VCAAS-CHANGELOG.md                 ← Every context change, ever
│   ├── VCAAS-DECISION-TREE.md             ← Where-does-this-go classification guide
│   │
│   ├── audits/                            ← Periodic context audits
│   │   ├── audit-<DATE>-landscape.md          (where knowledge lives today)
│   │   ├── audit-<DATE>-fragments.md          (conflicts and redundancies)
│   │   └── audit-<DATE>-risk.md               (risk assessment with severity)
│   │
│   ├── proposed-changes/                  ← Queue for protected-zone change requests
│   │   └── proposed-changes.md                (Pending / Approved / Rejected)
│   │
│   ├── prompts/                           ← System prompts that govern AI behavior
│   │   └── vcaas-classify.md                  (the classification assistant)
│   │
│   ├── deliverables/                      ← Module 1 & 2 client artifacts
│   │   ├── architecture-blueprint.md
│   │   ├── naming-convention-guide.md
│   │   ├── context-hierarchy-diagram.md
│   │   └── migration-plan.md
│   │
│   └── reviews/                           ← Recurring review templates
│       ├── weekly/weekly-template.md          (30-min standup)
│       ├── monthly/monthly-template.md        (60-min cross-team)
│       └── quarterly/quarterly-template.md    (3–4 hour strategic review)
│
├── guidelines/                            ← TIER 1 · UNIVERSAL RULES
│   │                                        every agent reads these
│   ├── guidelines-tone.md                     (voice attributes, forbidden phrases)
│   ├── guidelines-data-handling.md            (PII rules, approved vendors, redaction)
│   ├── guidelines-compliance.md               (regulatory, contracts, disclosure)
│   ├── guidelines-customer-comms.md           (what AI may draft vs send by channel)
│   └── guidelines-ai-behavior.md              (decision flow, ambiguity, refusal patterns)
│
├── skills/                                ← TIER 1 · ORG-WIDE REUSABLE KNOWLEDGE
│   │                                        organized by department
│   ├── core/                                  company-overview, product-knowledge,
│   │                                          pricing-rules, terminology-glossary
│   ├── finance/                               fpa-standards, billing-rules,
│   │                                          invoice-process, audit-trail-requirements
│   ├── operations/                            onboarding-process, escalation-paths,
│   │                                          vendor-management
│   ├── sales/                                 proposal-standards, pricing-tiers,
│   │                                          objection-handling, contract-terms
│   ├── support/                               refund-policy, sla-standards,
│   │                                          escalation-decision-tree
│   ├── marketing/                             brand-voice, messaging-framework,
│   │                                          content-standards
│   └── hr/                                    hiring-process, performance-standards,
│                                              offboarding-checklist
│
├── agents/                                ← TIER 2 · CONFIGURED AI AGENTS
│   │
│   ├── AGENTS-REGISTRY.md                     (live registry — every agent registered
│   │                                           here before production)
│   │
│   ├── <agent-name>/                          one folder per agent
│   │   ├── CLAUDE.md                              (the agent's operating manual)
│   │   ├── agent-config.md                        (model, tools, permissions, limits)
│   │   ├── agent-purpose.md                       (what this agent is for, what it is NOT for)
│   │   └── skills/                                (agent-specific skills)
│   │       └── <agent-skill>.md
│   │
│   └── sub-agents/                            sub-agents — spawned by parents, never humans
│       └── <sub-agent-name>/
│           ├── CLAUDE.md
│           ├── parent-agent.md                    (declares parent agent)
│           └── agent-config.md
│
├── teams/                                 ← TIER 2 · TEAMS
│   └── <team-name>/                           one folder per team
│       ├── CLAUDE.md                              (team operating manual)
│       ├── team-processes.md                      (rituals, cadences, runbook)
│       └── skills/                                (team-specific skills)
│           └── <team-skill>.md
│
├── projects/                              ← TIER 2 · TIME-BOUND PROJECTS
│   └── <project-name>/                        one folder per active project
│       ├── CLAUDE.md                              (project brain)
│       ├── <project-name>-context.md              (decisions, key facts, open questions)
│       └── skills/                                (project-specific skills)
│           └── <project-skill>.md
│
└── personal/                              ← TIER 3 · INDIVIDUAL PREFERENCES
    └── <person-name>/                         one folder per individual
        ├── CLAUDE.md                              (personal manual)
        └── skills/                                (personal skills)
            └── <personal-skill>.md
```

---

## How to read this layout

- **Tier 1** lives at the root and inside `guidelines/`, `skills/`, and `vcaas/`. Every agent and every human reads from here.
- **Tier 2** lives under `agents/`, `teams/`, and `projects/`. Each is scoped to its specific domain and inherits from Tier 1.
- **Tier 3** lives under `personal/`. One folder per person. Inherits from everything above; may customize within autonomous zones only.
- **The governance layer** (`vcaas/`) sits beside the rest of the system and audits it. It is not a tier — it is the metadata about the tiers.

## Inheritance rules

- A child `CLAUDE.md` always reads its parent's rules.
- A child may **extend** parent rules (add team-specific cadence on top of org-wide cadence).
- A child may **never override** rules in the protected zone (compliance, customer-facing voice, calculation logic, etc.).
- The frontmatter on each file declares its parent explicitly. If the parent does not exist, the file is an orphan.

## What's missing from this layout

This is the structural skeleton. The deployable kit fills it in with:

- Working `CLAUDE.md` content at every level (root, team, project, agent, sub-agent, personal).
- The actual text of all five `guidelines-*.md` files.
- Twenty-plus skill files across seven departments.
- A discovery-agent prompt that scans existing context and populates the audit files.
- Proposed-changes worked examples (one approved, one pending, one rejected).
- Health scorecard templates with the trend tracker pre-built.
- A 30-day day-by-day deployment guide.

For the full kit, see [README.md](README.md) → *Get the full deployment kit*.

---

*VCaaS™ — Vibecoding as a Service*
*Winventions LLC · [thecfointel.com](https://thecfointel.com)*
*USPTO Trademark Serial No. 99694926*
