# VCaaS™ — Vibecoding as a Service

> **A context governance framework for teams using AI coding agents.**
> Trademarked methodology by Winventions LLC · USPTO Serial No. 99694926

---

## About this public repository

This repository is a **public field guide**, not the full VCaaS™ deployment kit.

It is designed to explain the problem of context fragmentation, introduce the VCaaS™ operating model, and help leaders understand why AI context needs governance.

It intentionally excludes the deployable templates, client audit process, implementation prompts, scoring models, practitioner materials, and engagement playbooks. Those remain part of the paid VCaaS™ engagement — see [Deploy VCaaS™ in your organization](#deploy-vcaas-in-your-organization) at the bottom of this README.

---

## The problem

Your team uses Claude Code, Cursor, custom agents, automation scripts. Every one of those tools needs to know how your company works — your tone of voice, your pricing rules, your terminology, your customer policies. Today that knowledge lives in scattered places: Slack threads, Google Docs, somebody's head, three different versions of the same spreadsheet.

The symptoms are familiar:

- Every agent has its own version of reality.
- Nobody knows which file to update.
- The "rules" drift across tools, teams, and people.
- AI confidently invents answers that contradict what the company actually does.
- A change in one place silently breaks behavior somewhere else.

This is **context fragmentation** — and it is the single largest source of AI hallucination, drift, and broken trust inside teams that adopt AI coding tools at scale.

## What VCaaS™ is

**VCaaS™ ("Vibecoding as a Service") is the operating system for shared AI context.** It is a folder structure, an ownership model, and a set of governance rules that gives every AI tool in your organization **one shared, governed source of truth**.

It answers four questions every team eventually has to answer:

1. **Where does this piece of knowledge live?**
2. **Who is allowed to change it?**
3. **What is AI allowed to change on its own — and what requires a human?**
4. **How do we know the system is still healthy six months from now?**

VCaaS™ is methodology-first, tool-second. It assumes you are using Claude Code or a similar AI coding agent, but the principles apply to any AI tool that reads instruction files.

## The three core ideas

### 1. A three-tier hierarchy

Context lives at one of three tiers. Lower tiers inherit from higher tiers and may extend but not override protected rules.

- **Tier 1 — Organization.** Company-wide identity, mission, principles, guidelines, and reusable skills. One root `CLAUDE.md`. Read by every agent. Owned by senior leadership.
- **Tier 2 — Teams, Projects, Agents.** Scoped context: a specific team's workflow, a time-bound project, or a configured AI agent. Inherits from Tier 1.
- **Tier 3 — Personal.** One individual's preferences and private workflows. Inherits from everything above; may customize within autonomous zones only.

### 2. Two zones with one rule each

Every file in the system is in one of two zones. This is the most important governance decision in the kit.

- **Protected Zone — AI proposes, human approves.** AI may read it. AI may write a proposal to change it. AI must never modify it directly. Examples: pricing, calculation logic, customer-facing brand voice, compliance text, integration field mappings, audit-trail rules.
- **Autonomous Zone — AI may modify directly.** Every change is still logged, but no advance approval is required. Examples: internal drafting helpers, AI working notes, internal-only how-to docs.

The line that cannot blur: **AI can improve how intelligence is presented; AI cannot change what the intelligence calculates.**

### 3. A governance layer that polices itself

The system carries the artifacts that keep it honest:

- **Ownership matrix** — every file has a named Responsible and a named Accountable.
- **Changelog** — every context change is logged, including AI-driven changes in the autonomous zone.
- **Zones registry** — the canonical record of what's protected and what's autonomous.
- **Health scorecard** — a composite 0–10 score across seven dimensions, reviewed weekly.
- **Proposed-changes queue** — the inbox where AI drops change requests for human approval.
- **Audits, reviews, drift detection** — the recurring rituals that catch rot before it spreads.

## Who VCaaS™ is for

VCaaS™ is built for organizations where AI coding agents are no longer a curiosity — they are doing real work, in production, every day, with consequences. Specifically:

- **Founders and operators** scaling a team that increasingly relies on AI agents and is starting to feel the cost of every agent having its own version of reality.
- **Engineering leaders** at companies adopting Claude Code, Cursor, or custom agents who need a governance model before AI breaks something expensive.
- **Finance, ops, and revenue leaders** whose agents touch pricing, billing, customer data, or anything regulated — and who cannot afford autonomous AI edits to those zones.
- **Solo operators and small teams** who want the discipline of a governance system from day one, before fragmentation sets in.

If your team has ever said any of the following, VCaaS™ is for you:

- "I asked the agent why it did X, and there's no audit trail."
- "We have the same policy in three different docs and they disagree."
- "I don't know who owns this file."
- "We migrated to a new tool and lost half the context."
- "The agent confidently invented something that isn't true."

## What's in this repository

This is the **public, conceptual version** of the framework. It contains the methodology, the decision tree, and the high-level architecture — enough for anyone to understand how VCaaS™ works and decide whether it fits their team.

| File | What it is |
|---|---|
| [`README.md`](README.md) | This document — the framework overview |
| [`METHODOLOGY.md`](METHODOLOGY.md) | The six-module engagement model, conceptual level |
| [`PUBLIC-CONTEXT-CLASSIFICATION-GUIDE.md`](PUBLIC-CONTEXT-CLASSIFICATION-GUIDE.md) | Simplified classification guide: where does this piece of context go, and who controls it? |
| [`REFERENCE-ARCHITECTURE.md`](REFERENCE-ARCHITECTURE.md) | Illustrative reference architecture as a text diagram |
| [`DRIFT-SIGNALS.md`](DRIFT-SIGNALS.md) | The signals that tell you context governance is rotting |
| [`LICENSE.md`](LICENSE.md) | Licensing terms for this public version |

This repository is **deliberately conceptual**. It does not include the deployable kit — the working `CLAUDE.md` templates, the skill files, the proposed-changes protocol, the discovery agent prompt, the health scorecard templates, or the day-by-day deployment guide. Those are part of the full VCaaS™ engagement.

## The six-module engagement, at a glance

The full framework is delivered in six modules, paired across three phases. The conceptual layer of each module is documented in [`METHODOLOGY.md`](METHODOLOGY.md).

| Phase | Modules | Outcome |
|---|---|---|
| **Audit & Architect** | 1. Context landscape audit · 2. Architecture design | A signed-off architecture blueprint, naming convention guide, hierarchy diagram, and migration plan |
| **Govern & Own** | 3. Ownership & RACI · 4. Zones, propagation, approvals | A clear ownership matrix and a working protected/autonomous zone model with approval workflows |
| **Operate & Maintain** | 5. Migration & deployment · 6. Maintenance, drift detection, health | A live, audited context system with weekly, monthly, and quarterly review cadences |

## The principle behind it all

There is a single line that defines VCaaS™:

> **AI is allowed to improve how intelligence is presented.
> AI is not allowed to change what the intelligence calculates.**

Everything else — zones, ownership, audits, drift detection, the decision tree — is mechanism in service of that one principle.

If your AI tools can edit pricing, change calculation logic, or rewrite compliance text without a human in the loop, you do not have an AI productivity problem. You have a governance problem. VCaaS™ is the framework that closes that gap.

---

## Deploy VCaaS™ in your organization

This repository is the public field guide.

The full VCaaS™ deployment kit is delivered through a paid Winventions LLC engagement and includes:

- Working CLAUDE.md and context governance templates
- Discovery and context audit workflows
- Protected vs. autonomous zone configuration
- Proposed-changes protocol
- Ownership matrix and update propagation system
- Context health scorecard
- Six-module implementation process
- 30-day deployment playbook

VCaaS™ is designed for teams using AI agents in real workflows where context accuracy, ownership, auditability, and change control matter.

To discuss deployment, licensing, or enterprise implementation, contact Winventions LLC:

**Website:** [https://thecfointel.com](https://thecfointel.com)
**Email:** [VCAAS-EMAIL-PLACEHOLDER]
**Subject line:** VCaaS Deployment Inquiry

> **The public repo explains the problem. The paid deployment kit installs the operating system.**

---

*VCaaS™ — Vibecoding as a Service*
*Winventions LLC · [thecfointel.com](https://thecfointel.com)*
*USPTO Trademark Serial No. 99694926*
