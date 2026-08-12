# Output Templates

Structures for the recurring executive communication types. Use the one matching the frame established in step 1 of the workflow. Bracketed text is a slot, not literal output. Every template inherits the voice rules in SKILL.md: plain language, short sentences, no em-dashes, active voice, quantified claims.

**Contents**

1. Leadership summary (from SBAR, RCA, or change request)
2. Status update
3. Incident notification
4. Change or risk notice
5. Escalation
6. Meeting talking points
7. Slide headline
8. Contract or spend approval

---

## 1. Leadership summary

The default. Five sentences, under 150 words.

```
[Context: one sentence on the issue being addressed.]
[Risk assessment: one sentence on risk level, effort required, and reversibility.]
[Business impact: one sentence on stability, cost, or strategic goals.]
[Recommendation: one sentence with next actions, including testing and deployment cadence.]
[Optional closing: one sentence conveying confidence in the plan.]
```

A filled example, with commentary on what was deliberately left out, is in the "Worked example" section of SKILL.md.

---

## 2. Status update

For recurring reporting. Lead with condition, not activity.

```
Status: [On track | At risk | Blocked]

[One sentence stating where things stand against the commitment.]

Progress: [What moved, expressed as outcome not activity.]
Risk: [What could derail it, with likelihood and mitigation. Write "None material" if true.]
Ask: [What you need from the reader, or "No action needed."]
```

Writing "No action needed" is valuable. It lets the reader close the message with confidence rather than scanning for a hidden request.

---

## 3. Incident notification

Current condition first. Cause last, or not at all.

```
[Service] is [restored | degraded | down] as of [time].

Impact: [Who was affected, how, and for how long. Quantify.]
Current state: [What is true right now.]
Next update: [Time, or "final update" if resolved.]
```

During an active incident, omit cause entirely. Speculation stated early tends to be quoted back after it turns out to be wrong. Cause belongs in the postmortem.

---

## 4. Change or risk notice

For planned work that needs awareness or approval.

```
[What is changing, in one sentence.]

Risk: [Level, and what happens if it fails.]
Reversibility: [How fast it can be undone.]
Effort: [People and time.]
Impact: [What improves.]
Timing: [When, and what gates it.]

[Ask: approval, awareness, or a decision by a date.]
```

Reversibility earns its own line because it is the fact most likely to convert a hesitant reader into an approving one.

---

## 5. Escalation

Escalations fail when they read as complaint. Keep the emphasis on the decision you need.

```
I need a decision on [X] by [date].

Situation: [One or two sentences on what is blocked and what it costs.]
Options: [Two or three, each with its consequence.]
Recommendation: [Which one, and why.]
```

Bring options, not just a problem. An escalation with a recommendation attached is a request for confirmation, which is fast. One without is a request for someone else to do the thinking, which is slow.

---

## 6. Meeting talking points

For speaking. Structured with PREP so it holds without notes.

```
Opening line: [The point, stated in one sentence.]

If asked why: [Rationale in one sentence.]
If asked for proof: [One fact or number.]
If challenged on [likely objection]: [Response in one sentence.]

Closing: [Restate the point and the ask.]
```

Anticipating one or two objections is usually enough. Preparing for every possible question produces a script that sounds like a script.

---

## 7. Slide headline

Slide titles should be claims, not labels. A reader flipping through only the headlines should get the whole argument.

- *Label:* "Q3 Infrastructure Metrics"
- *Claim:* "Infrastructure costs fell 18 percent while uptime improved"

Apply the Pyramid Principle across a deck: the title slide carries the conclusion, each section headline carries one supporting point, and the body slides hold the detail.

---

## 8. Contract or spend approval

For anything a review board signs off on. Use the organization's own form where one exists. `references/approval-documents.md` has the full structure and the governance questions behind each section.

```
[Subject and contract type]

Summary and business rationale:
[One sentence defining what this is, for readers outside the working group.]
[What is being requested: structure, total contract value, term.]
[Why this path rather than the alternatives, including whether it was competitively bid.]

Key terms: [Term length, structure, total value, commercial position,
cost containment, accounting treatment, competitive bid status.]

Spend table: [Every year of the term. Recurring items only.]

Key benefits: [Quantified capability claims. No justification tails.]
Business outcomes / technical outcomes: [Two short verb-first lists.]
Risks: [Named plainly. Open negotiations named but not quantified.]
Accounting: [Treatment, and whether it has been validated. Leave visibly open if not.]

Ask: [One decision.]
```

The headline number is the total obligation across the full term, not the year-one increase. The approval body is approving the total, so the smaller framing is not the thing being decided, and a reader who finds the total late will re-read everything else looking for what else was framed favorably.

Run `scripts/check_figures.py` on the spend table before sending. See `references/numeric-integrity.md`.
