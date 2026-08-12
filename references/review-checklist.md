# Pre-Delivery Review Checklist

Run this against the draft before returning it. These are the failures that are hard to see in your own writing, which is why the pass is explicit rather than assumed. Fix what fails, then re-check - fixing one item often reintroduces another.

## Structure

- [ ] **The first sentence carries the conclusion.** If a reader stops there, do they know the outcome and what is being asked?
- [ ] **There is exactly one bottom line.** Two competing main points means either two messages or one that should be subordinated.
- [ ] **The ask is explicit.** Approval, awareness, funding, a decision by a date, or an explicit "no action needed." Never implied.
- [ ] **Nothing important sits below the fold.** Anything the reader must see is in the first few lines.

## Content

- [ ] **Every technical fact has a "so what" attached.** Any sentence that describes the mechanism without naming the consequence is either translated or cut.
- [ ] **Risk, effort, reversibility, and impact are all addressed** where the message is a recommendation. Reversibility is the one most often missing.
- [ ] **Claims are quantified.** No "significant," "substantial," or "considerable" standing in for a number. If the number is unknown, say it is unknown.
- [ ] **No new facts.** Everything traces to the source material or to something the user confirmed. Uncertainty is stated as uncertainty rather than smoothed over.
- [ ] **The investigation narrative is gone.** What was tried and in what order is not part of an executive message.

## Voice

- [ ] **No em-dashes.** House style, applied exactly.
- [ ] **Short sentences, one idea each.**
- [ ] **Active voice with a named owner.** "We tested," not "testing was performed."
- [ ] **No throat-clearing.** No "I wanted to reach out," "as you may know," "just a quick update."
- [ ] **No hedging stacks.** "It may potentially be possible that" is a single word in disguise. Pick it.
- [ ] **Jargon is replaced or glossed** on first use, in four words or fewer.
- [ ] **No inline bold in body prose.** Emphasis belongs in structure: headings, bullets, a terms block. Bolding mid-sentence tells the reader what to conclude before they have weighed the evidence, which reads as selling.
- [ ] **No reader instructions.** "Read the bottom row across," "note that this matters." If the structure is right they are unnecessary. If it is wrong they do not fix it.
- [ ] **Written in the sender's voice.** The output is the message. It does not reference the SBAR, ticket, or document it came from unless the reader needs that to act.

## Length

- [ ] **Within the target for the format.** Leadership summary: five sentences, under 150 words. Others: as short as the decision permits.
- [ ] **Every remaining sentence changes what the reader would decide or do.** If it does not, it is context for the writer, not the reader.

## If the document contains figures

Run `scripts/check_figures.py` first, then confirm the rest by hand. `references/numeric-integrity.md` explains each check.

- [ ] **Table totals have been recomputed.** Re-add every column after any row is added or removed. A total carried over from a previous draft is the most common error in these documents and the easiest for a reviewer to find.
- [ ] **Every number in prose matches the table.** These drift apart across revisions.
- [ ] **Percentages match their own base,** and the base is named at first use.
- [ ] **Recurring and non-recurring items are separated.** A one-time credit inside a run-rate table distorts the comparison even when every figure is accurate.
- [ ] **Figures that changed since the last version are accounted for.** Run `compare` mode. An unannounced restatement is the figure that gets challenged.

## If this is an approval document

- [ ] **The total obligation is in the first three sentences.** Full contract value across the full term, not the year-one delta. Find the largest true number in the draft and check that it is near the top.
- [ ] **Tables cover the whole term,** not just year one.
- [ ] **The governance questions are answered:** competitively bid or why not, accounting treatment and who validated it, term length and renewal caps, commercial and legal exposure.
- [ ] **Unsettled figures are not quantified.** Items in live negotiation are named with direction only.
- [ ] **Open items are visibly routed** rather than guessed. An unanswered question with a named owner is an action item; a guessed answer is a liability.
- [ ] **No rebuttals, corrections, or counterfactuals.** State the right numbers and let them stand. Flag any misperception to the sponsor to handle verbally.
- [ ] **No decisions presented as already taken.** "We have declined X" steps on the approver's authority.
- [ ] **The ask is one decision with no task attached to it.**

## Before returning

- [ ] **Open questions surfaced separately.** If a needed fact was missing and an assumption was made, state it outside the draft so the user can correct it rather than discovering it after sending.
- [ ] **Read the draft as the recipient.** A CFO, a CTO, and a board read the same words for different things. Does this land for the one who is actually receiving it?
