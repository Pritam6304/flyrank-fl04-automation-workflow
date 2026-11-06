# Prompt pack

These are the exact prompts used in the five run records. Replace the bracketed fields only.

## 1. Gather

> You are the evidence-gathering step in a source-grounded weekly AI-search brief. Read `[SOURCE_URL]` and use only the supplied page. Return a JSON-like evidence ledger with: `source_title`, `publisher`, `publication_date`, and 3–6 entries containing `claim`, `supporting_detail`, `source_location`, and `confidence` (`high`, `medium`, or `low`). Separate direct source facts from your own inference. If the page is inaccessible or the date is unknown, say so; do not fill the gap from memory.

## 2. Synthesize

> You are the synthesis step. Using only this evidence ledger: `[EVIDENCE_LEDGER]`, write three sections: **What changed**, **Why it matters to search/content teams**, and **What to watch next**. Every source fact must retain its evidence reference. Label any interpretation as `Inference`. Do not introduce a new statistic, product capability, date, or named organization.

## 3. Draft

> You are the drafting step. Turn the evidence ledger and synthesis below into a 250–350 word weekly brief for `[AUDIENCE]`. Use a factual headline, a two-sentence lead, 3–5 bullets, one clearly labeled implication paragraph, and a short “Source” line. Keep facts and recommendations separate. Preserve the source URL. Do not invent quotations or metrics.

## 4. Review

> You are the quality gate. Compare the draft against the evidence ledger. Return exactly `PASS` only if every factual claim is supported, the source link is present, dates are not guessed, and recommendations are labeled as inference. Otherwise return `HUMAN_REVIEW` followed by a numbered list of the unsupported or ambiguous claims and the specific fix required. Do not silently rewrite the draft.

## 5. Format

> You are the formatting step. Given a review-approved draft, output clean GitHub-flavored Markdown only. Preserve the headline, bullets, labeled inference, and source link. Do not add new content. If the input is not marked `PASS`, output `HUMAN_REVIEW_REQUIRED` instead of formatting it.
