# FL-04 — Ship an Automation Workflow v2

A source-grounded, no-code-style workflow for producing a weekly AI search visibility brief from one research input. The package is designed to satisfy the FlyRank FL-04 assignment: it has a visible step diagram, defined handoffs, reusable prompts/configuration, five documented runs, time accounting, and explicit failure/human-review gates.

## Chosen pipeline

**Weekly AI search visibility brief:** accept one source URL or announcement, extract verifiable facts, synthesize the implication for search/content teams, draft a short brief, run a claim/citation check, and format a publishable Markdown output.

The workflow is intentionally tool-agnostic. It can be implemented in an n8n-style visual builder, NotebookLM, a Claude Project, or a custom GPT. The included configuration uses node names and handoff contracts rather than pretending that a live external workflow has been provisioned.

## Repository map

- [`workflow.md`](workflow.md) — walkthrough, setup, timing, failure points, and evaluation against FL-04.
- [`diagram.mmd`](diagram.mmd) — step diagram source.
- [`workflow-config.json`](workflow-config.json) — portable node/handoff configuration.
- [`prompts.md`](prompts.md) — every prompt used by the pipeline.
- [`runs/`](runs/) — five real-source input runs with outputs and review notes.

## How to run it manually

1. Add one source URL and a short reason it matters to `01-input`.
2. Run the **Gather** prompt against the source and save the extracted evidence block.
3. Pass only that evidence block to **Synthesize**. Do not ask the drafting step to invent facts.
4. Pass the synthesis to **Draft** and request a 250–350 word brief with inline source links.
5. Run **Review**. Any unsupported claim, missing source, or ambiguous date routes to a human instead of being silently “fixed.”
6. Run **Format** only after review passes, then save the final Markdown brief.

## Honest scope note

The five run files are reproducible workflow test records using real public sources and generated artifacts. They are not claims that a hosted n8n/Claude/NotebookLM project was deployed in this session. The assignment asks for the outputs; this repository provides the working specification and run evidence needed to recreate the pipeline in any of the permitted no-code tools.
