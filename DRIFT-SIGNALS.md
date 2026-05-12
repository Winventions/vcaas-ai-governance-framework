# VCaaS™ Drift Detection Signals

> The specific symptoms that indicate AI context governance is rotting.
> Drift is rarely sudden — it accumulates quietly until AI starts producing wrong answers in production. These are the signals that catch it early.

---

## What "drift" means

In a VCaaS™ deployment, **drift** is the gap between what your documented context says and what your team, your AI agents, and your reality actually do. A perfectly healthy system has zero drift — every documented rule matches the lived practice. A rotting system accumulates drift until the documented context is a fiction that no one references.

Drift is monitored in two layers:

1. **Health Scorecard signals** — aggregate metrics scored 0–10 at every weekly review.
2. **Orphan signals** — file-level symptoms applied to individual nodes in the hierarchy.

A healthy system catches drift through the scorecard first, then narrows to the specific orphan files producing the drift.

---

## Layer 1 — The seven health dimensions

The VCaaS™ Health Scorecard composites seven dimensions, each scored 0–10. Drift becomes visible when any single dimension drops, especially when it drops persistently.

| Dimension | What it measures | What "rotting" looks like |
|---|---|---|
| **Coverage** | % of company processes with a documented skill file | Most knowledge still lives in heads, Slack threads, or scattered Notion pages |
| **Freshness** | % of files reviewed in the last 90 days | Files have not been touched in over a year; reviewers no longer remember the cadence |
| **Ownership** | % of files with a named, reachable owner | Many files have `PLACEHOLDER` owners, or named owners who have left the company |
| **Drift** | Distance between documented rules and actual practice | A rule says one thing; an agent or human routinely does another |
| **Fragmentation** | Number of duplicate or conflicting context sources | The same fact appears in three places, and the three places disagree |
| **AI compliance** | % of AI actions that respect protected zones | Agents are modifying protected files; violations show up in the changelog |
| **Adoption** | % of team members who actually use the system | Only the original owner references the kit; everyone else still asks Slack |

### Trigger thresholds

In paid VCaaS™ deployments, health thresholds are **calibrated per client** based on team size, number of active agents, regulatory exposure, and operational risk profile. A two-person consultancy and a regulated financial-services firm do not share the same drift tolerance.

Conceptually, three classes of trigger exist:

- **Composite drop** — when the overall score falls below the calibrated floor, an emergency context review is scheduled.
- **Single-dimension collapse** — when any single dimension falls into the critical band, that dimension's owner is paged for same-week action.
- **Persistent drift** — when the Drift or Fragmentation dimension stays in the warning band across several consecutive reviews, a full audit re-runs against the current landscape.

Exact numeric thresholds, escalation cadences, and the calibration formula are part of the deployment kit and are not published here.

---

## Layer 2 — The five orphan signals

At the file level, drift accumulates around **orphans** — nodes in the hierarchy that have become disconnected from the rest of the system. Orphans are the largest single source of context rot.

A file shows orphan symptoms when **any one** of the following five signals is present. The signals compound: more signals = higher severity.

### 1. The `vcaas_owner` field is a placeholder or a departed person

```
vcaas_owner: PLACEHOLDER
```

…or…

```
vcaas_owner: Sam Lee   ← Sam left the company 8 months ago
```

If no one currently employed at the company owns the file, the file is unowned. Unowned files do not get reviewed, do not get updated, and become AI's most-trusted source of out-of-date truth.

### 2. The `vcaas_last_reviewed` date is more than 90 days old

```
vcaas_last_reviewed: 2024-09-01     ← today is 2026-05-12
```

A file untouched for over 90 days has crossed the freshness threshold. A file untouched for over 12 months is **critical**: it almost certainly contradicts the current state of the business.

### 3. The `vcaas_parent` points to a file that does not exist

```
vcaas_parent: ../../OLD-CLAUDE.md   ← that file was deleted in last quarter's reorg
```

Or `vcaas_parent: none` on a file that is not at Tier 1. A parent that does not exist means inheritance is broken. The file is floating outside the hierarchy, and the rules that should bind it are not loading.

### 4. The file is not listed anywhere in `vcaas/VCAAS-OWNERSHIP.md`

If the ownership matrix does not list the file, the file is operating outside the governance system. It has no formal Responsible, no formal Accountable, and no review cadence applied to it.

### 5. The file has zero incoming references

No other file links to it. No agent's config reads from it. No team or project depends on it. The file is sitting in the repo, technically present, but functionally invisible. AI agents do not consult it; humans do not edit it; the system is structurally pretending it does not exist.

### Severity scoring

Orphan signals are additive:

- **Zero signals** → healthy node.
- **One signal** → **orphan candidate**. Watch at the next weekly review.
- **Two signals** → **orphan confirmed**. Triage at the next weekly review: assign owner, fix parent reference, set review date.
- **Three or more signals** → **orphan critical**. Immediate action required: archive (do not delete), reassign, or remove. Three-plus signals means the file is almost certainly contradicting current reality and producing wrong AI behavior.

---

## Additional drift symptoms outside the scorecard

These are softer signals — they do not get a numeric score, but they are early indicators that drift is starting to accumulate. Listen for them in everyday conversation.

- **"Wait, which doc has the current version?"** Asked in Slack about a topic the kit is supposed to canonicalize.
- **"The agent told me X but I thought we changed that."** Indicates the agent is reading a stale skill file.
- **"Who owns this?"** Asked about a file in the kit. If the answer requires more than five seconds, ownership is unclear.
- **"I just put it in a Google Doc for now."** A new piece of context is being created outside the kit. If repeated, the kit is being bypassed.
- **An AI proposal sits in the queue for more than two weeks.** The approval workflow has stalled. The owner is either disengaged or unclear.
- **A protected file was edited directly without a proposal.** Logged as a violation. If this happens twice in a quarter, the agent's config has a gap.
- **Two skill files in different folders give different answers to the same question.** Fragmentation has returned. Schedule consolidation.
- **A team has stopped attending the weekly review.** Adoption is slipping. Compose a re-engagement plan before the score tanks.
- **The discovery agent has not been re-run in over a quarter.** The landscape map is going stale. Schedule a re-scan.

---

## How drift detection fits into the review cadence

Drift signals are not monitored once a year. They are monitored at every cadence:

| Cadence | What gets checked |
|---|---|
| **Weekly (30 min)** | Composite score, any dimension below threshold, new orphan candidates, new violations |
| **Monthly (60 min)** | Trend across the last four weeks, soft drift symptoms reported by teams, top-3 risk areas |
| **Quarterly (3–4 hr)** | Re-run discovery agent, full re-audit of orphan list, archive of stale files, Tier 1 re-review |
| **Annual** | Full re-audit, agent re-certification, compliance review, year-over-year health snapshot for the board |

Skipping any cadence is itself a drift signal.

---

## The principle behind drift detection

The goal is not to drive every score to 10 every week. The goal is to **make drift visible while it is still cheap to fix**. A composite score of 7 with an upward trend and engaged ownership is healthier than a 9 with no review cadence and silent owners. The scorecard exists to surface conversation, not to grade performance.

If a dimension drops, the question is never "who is at fault?" — it is "what changed in the business that the kit has not caught up with yet?" Drift is information, not blame.

---

*VCaaS™ — Vibecoding as a Service*
*Winventions LLC · [thecfointel.com](https://thecfointel.com)*
*USPTO Trademark Serial No. 99694926*
