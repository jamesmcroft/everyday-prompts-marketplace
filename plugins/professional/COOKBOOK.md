# Professional Cookbook

Practical workflows and real-world examples for the `professional` plugin. These scenarios show how knowledge workers can use skills individually and how agents chain them for end-to-end workflows.

## Getting Started

```
/plugin marketplace add jamesmcroft/everyday-prompts-marketplace
/plugin install professional@everyday-prompts-marketplace
```

Once installed, invoke the `@professional` agent as your starting point. It classifies what you need and routes to the right skill or agent.

---

## Workflow 1: Full Meeting Lifecycle

**Scenario:** You have a project review meeting in 30 minutes, then need to send follow-up notes afterward.

**Before the meeting:**

> I have a project review meeting in 30 minutes. Here's the agenda and the notes from last week's meeting. Help me prepare.

The `@meeting-manager` agent produces a prep brief: purpose, desired outcome, key context, open decisions, and risks.

**After the meeting:**

> Here's the transcript from the meeting. Process it.

The agent:

1. Structures the notes (participants, discussion points, decisions, actions).
2. Drafts a follow-up email with decisions and action items.
3. Offers to create decision records for any meaningful decisions made.

**What you get:** Prep brief, structured notes, follow-up email, and decision records, all from one workflow.

---

## Workflow 2: Weekly Status Report

**Scenario:** It's Friday and your manager expects a status update.

**What to say:**

> Write a status update for my manager. This week I shipped the auth module, unblocked the frontend team on the API contract, and hit a delay on the data migration due to schema changes. Next week I'm focusing on the migration and starting the monitoring setup.

**What happens:**

The `/status-update` skill structures it:

- **Summary line:** one sentence headline.
- **Completed:** shipped auth module, unblocked frontend on API contract.
- **Blockers:** data migration delayed by schema changes.
- **Next steps:** migration completion, monitoring setup.

Tone is outcome-focused for a manager audience. No padding.

---

## Workflow 3: Prepare for a Performance Review

**Scenario:** Your mid-year review is in two weeks. You've been writing weekly journals all half.

**What to say:**

> Prepare for my performance review. I'm a Senior Engineer at a SaaS company. The review covers January to June. I have weekly journals for that period.

**What happens:**

The `@professional` coordinator runs the Review Cycle:

1. **Reads your weekly journals** for the period.
2. **Synthesizes monthly summaries** using the `/monthly-journal` skill, identifying compounding wins, persistent challenges, and lessons.
3. **Generates the impact assessment** using the `/performance-review` with four sections: results delivered, setbacks and growth, goals for next period, and actions to reach them.

**What you get:** A polished review document grounded in 6 months of evidence, not scrambled together the night before.

---

## Workflow 4: Write a Stakeholder Brief

**Scenario:** You need to propose a platform migration to your VP and need a one-pager.

**What to say:**

> Write an executive brief proposing we migrate our analytics platform from Redshift to BigQuery. The audience is the VP of Engineering. We need a decision by end of month. Key reasons: cost reduction, better ML integration, and our data team already knows BigQuery.

**What happens:**

The `/stakeholder-brief` skill produces:

- **TL;DR:** 2-3 sentences the VP can read and understand the entire proposal.
- **Problem:** current platform costs and limitations.
- **Recommendation:** migrate to BigQuery, with key benefits.
- **Ask:** approval to proceed with a migration plan by end of month.

Total length: one page. The VP can make a decision in 2 minutes.

---

## Workflow 5: Document a Technical Decision

**Scenario:** Your team just decided to use PostgreSQL instead of MongoDB for a new service. You want to capture why.

**What to say:**

> Document this decision: we chose PostgreSQL over MongoDB for the order management service. We also considered DynamoDB. The main factors were relational query patterns, team familiarity, and cost.

**What happens:**

The `/decision-record` skill produces a lightweight ADR:

- **Title:** Use PostgreSQL for the order management service.
- **Context:** why a decision was needed.
- **Options:** PostgreSQL, MongoDB, DynamoDB with pros/cons.
- **Decision:** PostgreSQL.
- **Rationale:** relational patterns, team familiarity, cost.
- **Consequences:** what becomes easier, what's ruled out.

Six months from now, anyone can read this and understand why PostgreSQL was chosen.

---

## Workflow 6: Draft a Difficult Email

**Scenario:** You need to push back on a deadline that leadership set without consulting the engineering team.

**What to say:**

> Draft an email to my director explaining that the Q3 launch date is not feasible with current scope. I want to propose either cutting scope or moving the date. Tone should be direct but diplomatic.

**What happens:**

The `/email-draft` skill produces:

- Subject line: clear and non-inflammatory.
- Opening: acknowledges the goal and timeline.
- Body: explains the gap between scope and timeline with specifics.
- Options: two paths forward (reduce scope or adjust date).
- Closing: clear ask for a 15-minute discussion to align.

No filler, no "I hope this email finds you well."

---

## Workflow 7: Research, Write, and Present

**Scenario:** Leadership asks you to investigate a technology and present a recommendation next week.

**What to say:**

> I need to research serverless vs. container-based deployment for our API layer, write a report, and create a presentation for the architecture review. The audience is the engineering leadership team.

**What happens:**

The `@report-to-presentation` agent runs the full pipeline:

1. **Plans the report** with the `@report-planner` agent: title, context, sections.
2. **Writes the report** with the `@report-writer` agent: section by section with citations.
3. **Creates a slide outline** from the report with speaker scripts per slide.
4. **Generates a stakeholder brief** as the "send ahead" one-pager.

**What you get:** A written report, a presentation deck outline with scripts, and an executive brief.

---

## Workflow 8: OKR Planning

**Scenario:** It's the start of the quarter and you need to turn your team's priorities into measurable OKRs.

**What to say:**

> Help me plan OKRs for my platform team for Q3. Our priorities are improving developer experience, reducing incident response time, and completing the cloud migration. We have 8 engineers.

**What happens:**

The `/okr-planner` skill:

- Produces 3-5 objectives as qualitative outcomes.
- Attaches 2-4 measurable key results to each.
- Flags if the scope seems too broad for the team size.
- Connects objectives to the stated business priorities.

---

## Tips

- **Start with `@professional`** for multi-step workflows. It chains skills and carries context.
- **The Review Cycle** works best when you've been writing weekly journals consistently. Start the habit now; your future self will thank you at review time.
- **Meeting notes are the source of truth.** The `@meeting-manager` agent builds everything (follow-ups, decisions) from the notes, not from memory.
- **Status updates should focus on outcomes.** "Shipped the auth module" beats "worked on authentication." The `/status-update` skill enforces this.
- **Executive briefs lead with the TL;DR.** If the VP reads nothing else, they should understand the ask from the first 3 sentences.
