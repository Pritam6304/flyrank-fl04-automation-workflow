# Run 03 — Anthropic prompt-engineering overview

**Input:** https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview  
**Why it matters:** The pipeline itself depends on explicit success criteria and repeatable evaluation.  
**Audience:** Automation builders and editorial QA owners  
**Estimated elapsed time:** 8 minutes (Gather 2, Synthesize 2, Draft 2, Review 1, Format 1).  
**Review decision:** PASS

## Evidence ledger

- Anthropic’s overview assumes a clear definition of success criteria, ways to test against them, and a first-draft prompt.
- It says prompt engineering is not always the best solution; model choice can sometimes improve latency and cost more directly.
- The overview points to clarity, examples, XML structuring, role prompting, thinking, and prompt chaining as techniques covered in its best-practices reference.

## Output

### Automation prompts need an evaluation target before they need polish

Anthropic’s prompt-engineering overview starts with the evaluation problem: define what success means, establish a way to test it, and keep a first prompt to improve. It also warns that not every failure should be solved with prompt changes; model selection can be a better lever for latency or cost.

- Success criteria should be written before prompt optimization.
- A test method is part of the prompt-engineering setup, not an optional afterthought.
- Prompt chaining is one of the techniques in the broader best-practices reference.
- Prompt changes are not the only available fix for quality, latency, or cost problems.

**Implication (inference):** A no-code workflow should ship with a review rubric and sample inputs alongside its prompts. Otherwise, a builder can tune language without knowing whether the workflow became more accurate or merely more fluent.

**Source:** [Anthropic — Prompt engineering overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)

## Human check

“Prompt chaining” is presented as a documented technique, not as evidence that Anthropic recommends this exact five-node architecture. The inference is labeled.
