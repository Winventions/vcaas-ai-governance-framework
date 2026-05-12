# VCaaS™ Decision Tree

> The printable, AI-readable classification guide.
> A piece of context just appeared in your work. Where does it go, and who controls changes to it?

---

Walk this tree top to bottom. The first branch that fits is your answer.

The tree runs in two passes:

- **Pass 1** assigns a **tier** — where, structurally, the content lives in the hierarchy.
- **Pass 2** assigns a **zone** — protected (AI proposes, human approves) or autonomous (AI may modify directly).

You always do both passes. Tier without zone is half an answer.

---

## Pass 1 — Which tier?

### 1. Content that applies to the WHOLE COMPANY

This is anything everyone, in every team, in every role, must respect.

- **Tier:** Tier 1 — Organization
- **Lives at:**
  - Identity, mission, principles → the root `CLAUDE.md`
  - Cross-cutting rules (tone, data, compliance, AI behavior) → `guidelines/guidelines-[topic].md`
  - Reusable knowledge an AI uses to do a job → `skills/[department]/[domain]-[function].md`
- **Owner:** A senior leader with org-wide authority (CEO, CTO, CFO, department head).
- **Zone trigger:** If a wrong change here would cost money, break an integration, or be noticed outside the team → **Protected**. Otherwise → **Autonomous**.
- **Example:** *"All customer-facing emails must include a real human name in the sign-off."* → `guidelines/guidelines-customer-comms.md`
- **Mistake to avoid:** Putting org-wide rules inside a single team's folder so only that team sees them. If it applies to everyone, it lives at Tier 1.

### 2. Content for a SPECIFIC TEAM or ongoing function

A team-specific workflow, ritual, or piece of knowledge that does not apply outside the team.

- **Tier:** Tier 2 — Team
- **Lives at:**
  - `teams/[team-name]/CLAUDE.md` for the operating manual
  - `teams/[team-name]/team-processes.md` for the runbook
  - `teams/[team-name]/skills/[domain]-[function].md` for team-specific skills
- **Owner:** The team lead. One named person, never "the team."
- **Zone trigger:** Most team content is **Autonomous** unless it touches a protected category (calculation logic, customer-facing voice, compliance, pricing, audit logic, integration mappings, AI behavior boundaries).
- **Example:** *"Engineering uses 2-week sprints; sprint planning happens Mondays at 10 AM ET."* → `teams/engineering/team-processes.md`
- **Mistake to avoid:** Recreating org-wide knowledge inside the team folder. If a skill would help any other team, propose promoting it to `skills/[department]/` at Tier 1.

### 3. Content for a TIME-BOUND PROJECT

A project starts, runs, and ends. Its context is bounded.

- **Tier:** Tier 2 — Project
- **Lives at:**
  - `projects/[project-name]/CLAUDE.md` for the project brain
  - `projects/[project-name]/[project-name]-context.md` for running context (decisions, key facts, open questions)
  - `projects/[project-name]/skills/[domain]-[function].md` for project-specific skills
- **Owner:** The project lead.
- **Zone trigger:** Project content is usually **Mixed** — confidentiality (NDA-bound projects) or financial-impact projects often have protected sub-areas.
- **Example:** *"We chose iOS-first for v1 because 73% of our ICP uses iOS. Decision date: 2026-04-15. Reversible: yes, by Q3 if we ship Android."* → `projects/v1-launch/v1-launch-context.md`
- **Mistake to avoid:** Letting a project folder outlive the project. When it ends, archive (do not delete); promote anything reusable to `/skills/`.

### 4. An AI AGENT being configured

You are building or registering an AI agent.

- **Tier:** Tier 2 — Agent (or Tier 2 — Sub-agent if spawned by a parent agent)
- **Lives at:**
  - Agent: `agents/[agent-name]/CLAUDE.md` + `agent-config.md` + `agent-purpose.md` + optional `skills/`
  - Sub-agent: `agents/sub-agents/[sub-agent-name]/CLAUDE.md` + `parent-agent.md` + `agent-config.md`
- **Owner:** The agent owner (named human, registered in the agents registry).
- **Zone trigger:** Agent operating files are **Protected** by default — wrong changes here can produce production damage. Sub-agent files are also protected.
- **Example:** *A new "sales-draft-agent" that drafts follow-up emails for reps to review and send.* → `agents/sales-draft-agent/CLAUDE.md` + register in the agents registry BEFORE production.
- **Mistake to avoid:** Letting an agent run in production before it is registered. Agents not in the registry are, by definition, not authorized.

### 5. Personal WORKFLOW or PREFERENCES

Your own way of working with AI — your tone preferences, your private prompt templates, your custom checklists.

- **Tier:** Tier 3 — Personal
- **Lives at:**
  - `personal/[your-name]/CLAUDE.md` for the manual
  - `personal/[your-name]/skills/[skill-name].md` for personal skills
- **Owner:** You.
- **Zone trigger:** **Autonomous** — your space, your call. The only exception: you cannot override protected rules from Tier 1 here (e.g., you cannot say "ignore the data-handling rules" — that is not autonomous-zone behavior).
- **Example:** *"AI: when summarizing for me, prefer bulleted lists over prose. I am dyslexic and dense paragraphs slow me down."* → `personal/jane-doe/CLAUDE.md`
- **Mistake to avoid:** Putting institutional knowledge in your personal folder. Anything the company needs to know after you leave does NOT belong here. If others would benefit, promote it via the proposed-changes queue.

---

## Pass 2 — Protected or Autonomous?

You have placed the content. Now decide who controls changes to it.

Walk these three questions in order. The first **yes** wins.

### Q1. If an AI changed this incorrectly, would it cost money?

This includes: pricing, billing rules, refund logic, contract terms, financial calculations, payroll, vendor spend.

- **Yes** → **Protected.** Changes go to the proposed-changes queue. Wait for the file's Accountable owner to write `APPROVED, PROCEED`.
- **No** → continue to Q2.

### Q2. Would a wrong change break an integration?

This includes: field mappings between systems (CRM ↔ accounting ↔ billing), API auth configs, schema definitions, data formats other tools depend on.

- **Yes** → **Protected.** Same workflow as Q1.
- **No** → continue to Q3.

### Q3. Would anyone outside the team notice the change?

This includes: anything in customer-facing voice, marketing copy, support replies, public statements, compliance documents, brand guidelines.

- **Yes** → **Protected.** Same workflow as Q1.
- **No** → **Autonomous.** AI may modify directly. Log the change in the changelog after the fact.

---

## Edge cases

- **The content fits two tiers.** Choose the higher tier. If it applies to a team AND the org, it is Tier 1. If it applies to a project AND the team, it is Tier 2 Team. Higher-tier always wins because of the inheritance rule.
- **The content is partly Protected and partly not.** Split it. Put the protected piece in its own file in a protected location; keep the rest where the autonomous flow works.
- **You are not sure who the owner is.** Default to the most senior person on the relevant team and ask them in the next weekly review. Never leave a file orphaned — orphans drag the Ownership health score down.

---

## What this tree does NOT do

- It does not authorize a change. It only tells you where the change goes and how it is governed.
- It does not replace the audit cadence — even autonomous changes show up in the weekly review.
- It does not replace the ownership matrix — once placed and zoned, the file still needs a named Responsible and Accountable.

---

*VCaaS™ — Vibecoding as a Service*
*Winventions LLC · [thecfointel.com](https://thecfointel.com)*
*USPTO Trademark Serial No. 99694926*
