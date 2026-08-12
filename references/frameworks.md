# Communication Frameworks

Mechanics and examples for the four structures referenced in SKILL.md. Read the section matching the framework you selected.

**Contents**

1. BLUF (Bottom Line Up Front)
2. Pyramid Principle
3. PREP
4. SBAR to leadership summary
5. Choosing between them

---

## 1. BLUF (Bottom Line Up Front)

A convention originating in military communication: the most critical information goes first, unconditionally.

**What it buys you**

- **Clarity.** The main point is apparent in the first line.
- **Efficiency.** The reader does not have to finish the document to know why they received it.
- **Decision orientation.** Information is sequenced to support a decision rather than to recount events.

**How to apply**

1. **Identify the core message.** Name the single point or action required. If you cannot state it in one sentence, the thinking is not finished and no amount of structure will rescue the draft.
2. **State it first.** Open with that sentence. Resist context, background, or preamble ahead of it.
3. **Support it after.** Add context, data, and explanation below the bottom line, ordered by how much the decision depends on it.
4. **Stop early.** Cut anything the reader does not need in order to act.

**Example**

- *Chronological:* "I have been working with the team on the migration. We encountered server issues. Now it is done."
- *BLUF:* "System migration completed successfully. No impact on service levels. Next review scheduled for Friday."

The BLUF version is shorter, but the real difference is that a reader who stops after seven words still knows the outcome.

**Common failure**

Writing a genuine BLUF sentence and then burying a second, more important point three paragraphs down. If the draft contains two bottom lines, either split it into two messages or subordinate one to the other explicitly.

---

## 2. Pyramid Principle

A structure for arguing toward a decision: conclusion first, then the grouped reasons that support it, then evidence beneath each reason.

**Structure**

1. **Conclusion.** The main point, stated as a claim rather than a topic. "We should retire the legacy policy," not "an update on the legacy policy."
2. **Supporting points.** Three or four, at most. Each should be independently sufficient to matter, and together they should cover the argument without overlap.
3. **Detail.** Evidence, data, and technical specifics, held beneath the relevant supporting point and surfaced only if asked.

**When to use it**

Presentations, proposals, written briefs, and any document where the reader needs the critical message before deciding whether to engage with the detail. It is the natural structure for a deck: conclusion on the title slide, one supporting point per section.

**Why three or four**

More than four supporting points signals that the grouping is wrong. Look for a level of abstraction where several of them collapse into one. Seven reasons read as a list of everything you know; three read as an argument.

---

## 3. PREP

Point, Rationale, Evidence, Point. Built for speaking rather than writing.

**Structure**

1. **Point.** State the conclusion.
2. **Rationale.** Give the logic behind it.
3. **Evidence.** Offer one supporting fact.
4. **Point.** Restate the conclusion.

**When to use it**

Live meetings, unplanned questions, hallway conversations, anywhere you are answering without notes. The closing restatement matters more in speech than in writing, because a listener cannot scroll back.

**Example**

> "We should hold the release until Thursday. The rollback path is untested against the new schema, so a bad deploy would take hours rather than minutes to reverse. We saw exactly that failure mode in the March incident. Holding until Thursday gives us the tested rollback and costs us two days."

**Common failure**

Starting with rationale because it feels more polite or less presumptuous. It reads as uncertainty. Lead with the point and let the rationale earn it.

---

## 4. SBAR to leadership summary

SBAR - Situation, Background, Assessment, Recommendation - is a strong internal engineering format and a poor executive format. It carries the full reasoning chain, which is exactly what a leader does not need.

**Mapping**

| SBAR section | Leadership summary | Transformation |
|---|---|---|
| Situation | Context (1 sentence) | Strip the technical mechanism, keep what is being addressed |
| Background | Usually dropped | Include only if the reader needs history to judge the recommendation |
| Assessment | Risk assessment + business impact (2 sentences) | Convert technical severity into risk level, effort, reversibility, then into cost, stability, or strategic consequence |
| Recommendation | Recommendation (1 sentence) | Keep the action, add the cadence: what happens when, and what gates the next step |

**Rules for the transformation**

- Preserve reversibility. "Can be reversed within minutes" does more to unblock an approval than any other single phrase.
- Name effort in human terms. "Minimal effort" or "roughly two engineer-days," not story points.
- Do not smuggle the mechanism back in. If the summary explains *how* the fix works, it has drifted back toward the SBAR.
- Do not cite the SBAR. The summary is the message, not a report about a document.

**Length target**

Five sentences, under 150 words. If the material genuinely does not fit, the usual cause is two separate decisions bundled into one message. Split them.

---

## 5. Choosing between them

| You are | Use |
|---|---|
| Sending an email, Slack message, or written status | BLUF |
| Arguing for a decision in a doc or deck | Pyramid Principle |
| Answering out loud, unprepared | PREP |
| Converting an engineering SBAR for leadership | SBAR mapping above, delivered in BLUF order |

These are compatible, not competing. Pyramid Principle is BLUF with an explicit second layer. PREP is BLUF with a spoken bookend. The shared commitment is that the conclusion comes first.
