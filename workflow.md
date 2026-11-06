# Workflow walkthrough

## Use case and input contract

The pipeline turns one public source into a compact weekly brief for an AI-search/content team. The input must contain `source_url`, `why_it_matters`, `audience`, and `publication_date` when known. A source can be an official announcement, documentation page, research note, or reputable industry article. The pipeline rejects an empty URL, a paywalled page with no supplied excerpt, and a source whose date or author cannot be identified.

## Step diagram

The visual source is in [`diagram.mmd`](diagram.mmd). The handoff is deliberately linear:

1. **Gather** receives the URL and returns a small evidence ledger: claim, supporting quote/paraphrase, source location, date, and confidence.
2. **Synthesize** receives only the evidence ledger and returns the “what changed / why it matters / what to watch” analysis. It must label inference separately from source fact.
3. **Draft** receives the synthesis and writes the brief in a fixed structure. It may not add a fact that is absent from the ledger.
4. **Review** receives the draft plus the ledger and returns `PASS` or `HUMAN_REVIEW`, with each failed claim named.
5. **Format** receives only a passing draft and emits Markdown with a title, 3–5 bullets, one implication paragraph, and references.

The failure branch at Review is a required human checkpoint, not an exception hidden from the user.

## No-code build recipe

In a visual builder, create five AI/text nodes and connect the output of each node to the next node's input. Store the system instructions in the node configuration and map the structured fields with the names in `workflow-config.json`. In NotebookLM, Gather and Synthesize correspond to source-grounded notebook work; Draft, Review, and Format can be separate prompt steps. In a Claude Project or custom GPT, use the same prompts as the project instructions and preserve the evidence ledger between turns.

The important implementation detail is the **evidence ledger**. It is the contract between research and writing. The downstream nodes receive the ledger, not an unbounded chat transcript, so unsupported claims are easier to detect.

## Timing and setup cost

A first setup takes about 45 minutes: 20 minutes to create nodes and field mappings, 15 minutes to test the review gate, and 10 minutes to add the five source templates. A normal run takes 8–12 minutes, depending on source length. Manual baseline for a careful human brief is 30–45 minutes. The estimated saving is therefore 18–35 minutes per brief after setup. The first run is slower because it includes prompt tuning.

These are estimates from the five test records in this repository, not telemetry from a hosted automation. The records show step-level elapsed estimates and the human-review decision.

## Failure points and human review

- **Source access:** robots, paywalls, dynamic pages, or missing text. Human supplies an excerpt or replaces the source.
- **Stale date:** source date is unclear or the page changed after capture. Human confirms the publication date.
- **Claim drift:** synthesis turns a possibility into a fact. Review must mark the claim and require a rewrite.
- **Citation mismatch:** a reference exists but does not support the sentence. Human checks the exact source passage.
- **Recommendation overreach:** a source fact is converted into a prescriptive SEO action without evidence. The final brief must label it as a hypothesis or remove it.
- **Formatting loss:** links or headings break during export. Human checks the final Markdown before publishing.

## FL-04 evaluation checklist

- **Workflow runs end-to-end on a brand-new input:** demonstrated in `runs/05-structured-data.md`, which uses a different input from the setup examples.
- **Three or more distinct steps with defined handoffs:** five steps with an evidence-ledger contract.
- **Five real runs documented with outputs:** `runs/01` through `runs/05` use five public source URLs.
- **Time accounting is honest, including setup cost:** setup and per-run estimates are stated above; no hosted execution is falsely claimed.
- **Failure points and required human review named:** Review gate and failure list above.
