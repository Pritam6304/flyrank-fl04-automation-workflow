# Run 04 — llms.txt proposal

**Input:** https://llmstxt.org/  
**Why it matters:** The source is a live example of a proposed content-access convention that matters to agent-facing documentation.  
**Audience:** Technical content and documentation teams  
**Estimated elapsed time:** 10 minutes (Gather 4, Synthesize 2, Draft 2, Review 1, Format 1).  
**Review decision:** HUMAN_REVIEW → PASS after one edit

## Evidence ledger

- The proposal describes `/llms.txt` as a Markdown file intended to help agents use a website.
- It recommends a concise file with background information and links to more detailed Markdown content.
- The proposal specifies an H1 as the only required section, with an optional blockquote and file-list sections.
- The page characterizes the specification as open for community input.

## Output after review

### llms.txt is a proposal for agent-readable site orientation

The llms.txt proposal targets a practical problem: human-oriented pages can wrap useful information in navigation, ads, and JavaScript, making extraction harder for agents. It proposes a small Markdown file at the site root or a subpath that gives background context and links to more detailed content.

- The proposed file is named `llms.txt` and is Markdown-based.
- The required structural element is an H1 naming the project or site.
- Optional sections can provide context and lists of relevant Markdown links.
- The proposal is open for community input rather than presented as a universal search requirement.

**Implication (inference):** Documentation teams can experiment with a small, human-readable agent index, but should treat it as an interoperability experiment and keep canonical HTML documentation healthy.

**Source:** [llms.txt proposal](https://llmstxt.org/)

## Human check

The first draft said “search engines now require llms.txt.” Review removed it because the source describes a proposal and community-input process, not a requirement.
