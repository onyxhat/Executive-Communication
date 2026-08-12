# Executive Communication

A skill that turns engineering and operational detail into writing a senior leader can act on in under a minute.

Point it at an SBAR, an incident report, a change request, a contract renewal, or a draft that came back marked "too in the weeds," and it produces the leadership version. It also works in reverse: hand it someone else's draft and it will review, tighten, and check the arithmetic in the tables.

This is a portable skill. It contains no organization-specific content, so it works anywhere.

---

## What it does

**Drafting.** Establishes the frame (audience, decision, stakes, format, required template), picks a structure, translates technical facts into business consequence, drafts against a template, and reviews against a checklist before returning anything.

**Reviewing.** Applies the edits senior leaders predictably make, so a draft absorbs them before it goes out rather than after it comes back.

**Checking figures.** Verifies that tables actually add up and that numbers have not drifted between drafts. This runs as a script, not a judgment call.

**Formats it covers:** leadership summaries, status updates, incident notifications, change and risk notices, escalations, meeting talking points, slide headlines, and contract or spend approvals.

---

## Installation

The skill is distributed two ways: as `executive-communication.skill` (a zip archive) or as the unpacked `executive-communication/` folder. Both hold the same files.

### Claude desktop app or Cowork

Open a conversation, attach `executive-communication.skill`, and click **Save skill** on the file card. It becomes available in every future session on your account.

If the Save skill button does not appear, your organization has skill creation disabled. Ask an administrator, or use the folder method below.

### Claude Code

Copy the unpacked folder into a skills directory:

```bash
# Available in every project
cp -r executive-communication ~/.claude/skills/

# Available only in the current project, and committable to the repo
mkdir -p .claude/skills && cp -r executive-communication .claude/skills/
```

If you have the `.skill` archive rather than the folder, unzip it first:

```bash
unzip executive-communication.skill -d ~/.claude/skills/
```

Restart Claude Code, then confirm it registered by asking it to list available skills.

### Any other LLM agent

The skill is plain markdown with no proprietary format. Give the agent `SKILL.md` as a system prompt or context document, and make the `references/` folder available for it to read on demand. `SKILL.md` names each reference file and says when to open it, so an agent that can read files will pull the right one at the right time.

For an agent that cannot read files, `SKILL.md` alone still works. You lose the depth in the references but keep the workflow.

### Requirements

Nothing, for the writing guidance.

The figure-checking script needs **Python 3.8 or later** and uses only the standard library. Two optional extras let it read binary formats directly:

```bash
pip install python-docx pdfplumber   # optional: adds .docx and .pdf support
```

Without them the script still reads markdown and plain text, and tells you what is missing if you hand it a file it cannot open.

---

## Using it

### In conversation

The skill triggers on its own when a request matches. You do not need to name it. These all work:

- "Turn this recommendation into something I can send to leadership."
- "This memo is too technical. Make it work for the steering committee."
- "Draft the executive summary for this vendor renewal."
- "Review this before I send it to Finance."
- "What changed between these two versions?"

If it does not trigger and you want it, name it directly: "Use the executive-communication skill on this."

### Getting good results

Give it the raw material rather than a summary you already wrote. The skill's value is in the translation, and it cannot translate what you have already flattened.

Answer its questions. It will ask who the audience is, what decision they need to make, and whether the receiving body has a required form. That last one matters more than it sounds: a strong document in the wrong container gets rewritten by whoever owns the container, and your reasoning is what gets lost in the transfer.

Tell it when a number is not settled. Figures still under negotiation are handled differently from figures that are final, and the skill cannot tell which is which by looking.

### Checking figures

Run this on anything containing a table, before reviewing the prose.

```bash
# Verify totals and derived columns
python3 scripts/check_figures.py check draft.md

# See which figures moved between two drafts
python3 scripts/check_figures.py compare v1.md v2.md
```

`check` reports two categories. **ISSUES** are arithmetic that does not hold, such as a total row that disagrees with the column above it. These are always real. **REVIEW** lists figures that appear in prose but in no table, which usually just need a human to confirm what they refer to.

`compare` matches table rows across two drafts even when the labels were shortened, and reports values that changed. Run it any time a document has been through someone else's hands. A figure that moved without anyone announcing it is the one that gets challenged in the meeting.

The script exits 1 when a check fails, so it can gate a build or a pre-send hook.

Both commands read `.md` and `.txt` anywhere, and `.docx` and `.pdf` when the optional libraries are installed.

---

## What is inside

```
executive-communication/
├── SKILL.md                             The workflow. Start here.
├── README.md                            This file.
├── references/
│   ├── frameworks.md                    BLUF, Pyramid Principle, PREP, SBAR mapping
│   ├── engineering-translation.md       Technical facts into business consequence
│   ├── output-templates.md              Eight copy-ready structures
│   ├── approval-documents.md            Contracts, purchases, capital requests
│   ├── numeric-integrity.md             Finding errors in tables and figures
│   ├── revision-patterns.md             What senior editors cut and add
│   ├── review-checklist.md              Pre-delivery quality gate
│   └── knowledge-base-authoring.md      Structuring docs for agent retrieval
└── scripts/
    └── check_figures.py                 Table arithmetic and cross-draft diffs
```

`SKILL.md` is the only file loaded automatically. It names every reference and says when to open it, so the rest load on demand and cost nothing until they are needed.

---

## House style

The skill applies a specific set of conventions, applied consistently because they came from observed practice rather than from general writing advice:

- No em-dashes or en-dashes. A period or comma instead.
- Short sentences, one idea each.
- Active voice with a named owner.
- Quantify what is settled. Name but do not quantify what is still being negotiated.
- Emphasis lives in structure, not in inline bold.
- The default leadership summary is five sentences and under 150 words. Approval documents are the deliberate exception and run longer.

If your organization's conventions differ, edit `SKILL.md` under **Voice and mechanics** and `references/review-checklist.md`. Those two files hold nearly all the style rules.

---

## Editing and repackaging

Edit the unpacked folder, then rebuild the archive. The skill-creator skill ships the packaging script:

```bash
python3 -m scripts.package_skill /path/to/executive-communication
```

Run it from the skill-creator directory. It validates the skill before packaging and refuses to build an invalid one.

Two constraints worth knowing before you edit:

- The `description` field in `SKILL.md` frontmatter has a hard limit of **1024 characters**. It is also the only thing determining whether the skill triggers, so keep new use cases in it and cut adjectives rather than triggers.
- Keep `SKILL.md` under about 500 lines. If it grows past that, move the detail into a new file under `references/` and leave a pointer.

To add organization-specific content such as your own approval forms or house terminology, prefer a separate skill that references this one. Keeping this skill neutral is what lets it move between teams.
