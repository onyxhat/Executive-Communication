# Numeric Integrity

Read this whenever a document contains a table, a financial figure, or a claim built on numbers, and always before an approval document goes out.

A single figure that does not reconcile costs more than a badly structured argument. Executives read numbers first and prose second. Finding one error licenses a reader to distrust every other number on the page, and they will stop reading your reasoning and start auditing your arithmetic. Recovering from that in the meeting is much harder than catching it beforehand.

**Contents**

1. Run the script first
2. Where errors actually come from
3. Checks that need judgment
4. Reporting what you find

---

## 1. Run the script first

`scripts/check_figures.py` handles the deterministic checks. Run it before reading the document closely, so you review a draft you already know adds up.

```bash
# Verify tables inside one or more documents
python3 scripts/check_figures.py check draft.md

# Diff figures between two drafts, keyed on table row labels
python3 scripts/check_figures.py compare v1.md v2.md
```

It reads markdown and plain text with no dependencies, and `.docx` and `.pdf` when `python-docx` or `pdfplumber` are installed. It reports two categories:

- **ISSUES** are arithmetic that does not hold: a total row that does not equal the sum of its column, or a change column that does not equal the difference it claims. These are always real. Fix them.
- **REVIEW** lists figures that appear in prose but in no table. These are usually fine. They exist because deciding whether "$230K in other tooling" reconciles with a table requires knowing which rows the phrase refers to, which is a judgment the script cannot make. Check each one by hand.

Use `compare` any time a document has been through someone else's hands. A figure that moved between drafts without anyone announcing it is the one that gets challenged, and neither author may have noticed it changed.

## 2. Where errors actually come from

Almost every numeric error in an executive document comes from editing rather than from calculation. Knowing the failure modes tells you where to look.

**The stale total.** Someone adds or deletes a row and the total is not recalculated. This is by far the most common, and it is especially likely when a row is deleted, because deleting feels like a subtraction that needs no follow-up. The tell is a total row that disagrees with its own change column. The script catches it.

**Prose and table drift apart.** A number is updated in the table but not in the sentence that quotes it, or the reverse. Every revision cycle increases the odds. The script flags candidates; you confirm.

**The unannounced restatement.** Someone corrects a figure based on better data and does not say so. Legitimate, and dangerous when it silently changes a headline conclusion, because the author who wrote that conclusion may not know it moved. `compare` mode exists for this.

**Mixed recurring and non-recurring.** A one-time credit or a one-off cost sitting inside a table of annual spend. Every individual figure is accurate and the comparison is still misleading. Report non-recurring items separately, below the run-rate table.

**Inconsistent baselines.** Two sections comparing against different starting points, so their percentages cannot both be right. Pick one baseline, state it once, and measure everything against it.

**Percentages without a stated base.** "A 29% increase" is meaningless until the reader knows 29% of what. Name the base at first use.

## 3. Checks that need judgment

Work through these after the script is clean. None of them can be automated.

**Does every prose figure reconcile to something?** For each item in the REVIEW list, identify what it refers to. If it is a sum of table rows, add them and confirm. If it comes from outside the document, name the source. If neither, it does not belong.

**Do the percentages match their own numerators?** Recompute each one. A percentage inherited from an earlier draft whose underlying figures have since changed is silent and common.

**Is the baseline the right one?** Not just internally consistent, but the number a reader would consider fair. Comparing against a figure that was artificially low makes an increase look larger than it is, and comparing against an artificially high one is worse, because it looks like a favorable choice once someone notices.

**Is the headline the total?** For anything seeking approval, the largest true number belongs near the top. See `references/approval-documents.md`.

**Does the table answer the question the prose asks?** A table of annual spend does not settle a claim about total contract value. Readers assume the table proves the sentence next to it.

**Are units and periods consistent?** Monthly against annual, per-user against total, fiscal year against calendar year. Label every column with its period.

**Does rounding change the conclusion?** "Roughly $3.0M" is fine. "Roughly $3.0M" where the real figure is $3.4M is not, and rounding that always favors the argument reads as motivated once a reader spots it.

**Would the numbers survive the obvious follow-up?** Pick the two most quotable figures and ask where each came from. If the answer is not in the document or one message away, either add the basis or drop the claim.

## 4. Reporting what you find

When reviewing someone else's draft, separate errors from judgment. Errors are not negotiable and should lead. Judgment calls are the author's to make.

State each error as: the location, what it says, what it should say, and why. "The Year 1 Total reads $770,000 but the three rows above it sum to $850,000. The $770,000 is left over from the previous draft, which had a fourth row that has since been deleted." That is actionable without being an accusation.

Do not bury a numeric error inside general feedback about structure or tone. Put it first, under its own heading, before anything else. The author needs to fix it before the document moves, and everything else can wait.

If a figure changed between versions and you cannot tell whether it was deliberate, ask rather than assume. Both possibilities, a correction or a transcription slip, are ordinary, and the cost of asking is one sentence.
