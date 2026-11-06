# Run 02 — OpenAI web search tool

**Input:** https://platform.openai.com/docs/guides/tools-web-search  
**Why it matters:** The brief needs to explain how source citations behave in a web-grounded model workflow.  
**Audience:** AI product and content-ops leads  
**Estimated elapsed time:** 12 minutes (Gather 5, Synthesize 2, Draft 2, Review 2, Format 1).  
**Review decision:** HUMAN_REVIEW → PASS after one edit

## Evidence ledger

- OpenAI documents web search as a tool that can provide up-to-date information with sourced citations.
- The Responses API uses a `web_search` tool; the page distinguishes it from legacy preview integrations.
- Responses can include a search-call item and a message with URL citation annotations.
- OpenAI says citations should be clearly visible and clickable when web results are shown to end users.

## Output after review

### Source visibility is part of the web-search product contract

OpenAI’s web-search documentation frames search as a tool that can retrieve current information and return sourced citations. In the Responses API, a web-search call and a message with URL-citation annotations are separate parts of the response structure.

- New Responses API integrations use the `web_search` tool.
- Search responses can include the action taken and the URLs cited in the message.
- URL-citation annotations include source metadata and the location of the citation in the response.
- The documentation says citations shown to end users should be visible and clickable.

**Implication (inference):** Any content workflow that summarizes live web results should preserve citation metadata as a first-class field, not flatten it into plain text. A “citation present” check is weaker than a “citation visible, clickable, and attached to the right claim” check.

**Source:** [OpenAI — Web search](https://platform.openai.com/docs/guides/tools-web-search)

## Human check

The first draft called annotations “proof of correctness.” Review rejected that wording because annotations identify sources but do not guarantee that a claim is accurate. The final draft uses “source metadata” instead.
