# Authoring Knowledge Sources for AI Agents

Read this only when the task is writing or restructuring reference material that an agent will retrieve from. It is not needed for drafting a message.

Well-structured sources reduce hallucination and improve retrieval accuracy. Poorly structured ones fail quietly: the agent retrieves the wrong passage and produces a confident, wrong answer.

## Structure and modularity

- **Avoid monoliths.** A hundred-page document is a weak source. Retrieval pulls fragments, and fragments from a sprawling document carry no reliable context.
- **Go modular.** Topic-focused documents in the range of five to twenty pages retrieve far better.
- **Bound each theme.** Every document should stand alone and be nameable in a short phrase - "BLUF Methodology," "Engineering Translation." If a document needs a second title to describe it, split it.

## Formatting standards

- **Hierarchical headings.** Use H1, H2, and H3 to carry meaning, not just visual weight. Agents use heading structure to locate passages.
- **Summaries up front.** Open each section with two or three sentences stating what it covers. This is often the fragment that gets retrieved.
- **Lists over dense narrative.** Bullets reduce cognitive load for human and machine readers alike.
- **Clean tables.** Use them for comparisons. Avoid nested tables, merged cells, and complex layouts, which flatten into unusable text.

## Content clarity

- **Eliminate jargon.** An agent does not infer implied logic or cultural shorthand. Internal abbreviations need expansion on first use.
- **Be explicit about boundaries.** State what the agent may say, what it must never say, and when it should escalate to a human. Implicit norms do not survive retrieval.
- **Attach metadata.** Topic, audience, purpose, author, document type, and last-updated date all improve retrieval accuracy and let a reader judge whether the content is current.

## Diagrams and processes

- **Text first.** Agents frequently cannot parse images. Any logic that exists only in a diagram is invisible.
- **Summarize every figure.** Add two or three sentences of plain text below it describing what it shows.
- **Consider Mermaid.** Including a Mermaid version of a process diagram keeps the logic alive as text even where the rendered image is unavailable.

## Why this matters

Clear structure produces clarity for the reader, efficiency for both sides, faster decisions, and trust built on respect for the reader's time. For agent consumption specifically, it reduces hallucination and makes retrieval predictable. The same discipline that makes a document useful to an executive makes it useful to an agent: state the point first, keep it bounded, and cut what does not carry weight.
