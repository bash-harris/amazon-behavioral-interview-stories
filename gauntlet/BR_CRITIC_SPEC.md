# BAR RAISER STORY CRITIC — run spec

For each story (the gauntlet answer file), run this critic TWICE (2 passes):
- **Pass 1** = critique the original answer (in `answers/QN.md`). Output → `br_critiques/QN_pass1.md`.
- **Repair** = a builder applies the repair plan WITHOUT inventing facts, outputting a strengthened version to `answers_v2/QN.md` (original left intact).
- **Pass 2** = critique the repaired version (`answers_v2/QN.md`) with the SAME prompt. Output → `br_critiques/QN_pass2.md`.

The builder MUST: keep every fact grounded in the source docs (verify against them); for any metric that fails the credibility audit, soften to what the source supports or mark it as a gap; preserve the STAR + strong-signals + provenance structure; keep the STORY 4 natural register. NEVER invent facts/metrics/users/results. If the original is a GAP (framework only, no real event), do NOT fabricate a story — repair = tighten the framework labeling only, and pass 2 reflects that it is still a framework.

## Sources to verify against (real work only)
- LP rubric: `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\behavioral\LP_RUBRIC.md`
- Story banks: `AMAZON_INTERVIEW_PREPARATION.md` + `AMAZON_INTERVIEW_PREP.md` in that behavioral folder
- `CODEBASE_DOCUMENTATION.md`, `BAR_RAISER_TECHNICAL_PREP.md` in the BGSW folder
- Tab Scroller docs/code: `C:\Users\bkh\Downloads\tab scroller\`
- Answers index: `C:\Users\bkh\Documents\amazon-lp-dataset\gauntlet\STORY_LEDGER.md`

## STANDING REPAIR RULE (added after repeated pass-2 findings)
The repairer has repeatedly introduced NEW small fabrications while fixing old ones (over-attributing a metric, inventing a measurement method like "hand stopwatch", misquoting a config value, name-only inference of a dataset size). HARD RULES for every repair:
- Fix the flagged gap by DELETING or GENERALIZING to what the source literally supports. Never replace one unverified specific with another.
- You may NOT add any number, count, config value, timeframe, or method not present in the cited line. If the source only names something, do not infer its magnitude.
- If you cannot cite a claim to a specific line of the story bank / code / doc, drop the claim or state it as a known gap.
- Prefer weaker-but-true over stronger-but-unevidenced.
- After writing the v2, self-audit: list every remaining specific and the exact source line backing it; remove any you cannot line.

## THE CRITIC PROMPT (use verbatim)
---
# Amazon Bar Raiser Story Critic

Act as a skeptical Amazon Bar Raiser. Your job is to **stress-test the story, identify weaknesses, and specify how to strengthen it**. Do not optimize for polished language; optimize for credible evidence.

## Evaluate
Assess the story on:
- **Leadership Principle fit** — Is the claimed LP actually demonstrated?
- **Problem** — Is the problem real, important, and clearly explained?
- **Ownership** — Is it obvious what *I* personally did versus what the team/system did?
- **Judgment** — What decisions, alternatives, and trade-offs did I make?
- **Invent & Simplify** — What was genuinely novel, and what complexity did I remove?
- **Customer impact** — Who benefited and how?
- **Results** — Are outcomes concrete, measurable, and causally credible?
- **Learning** — What failed, what changed, and what would I do differently?
- **Credibility** — Could every important claim survive aggressive questioning?

## Be adversarial
Challenge:
- unsupported or suspiciously precise metrics
- unclear baselines or measurement methods
- vague claims like "improved efficiency"
- excessive use of "we"
- technology usage presented as innovation
- weak customer impact
- missing trade-offs
- missing failure/learning
- claims of scalability, accuracy, adoption, or impact without evidence
- unnecessary technical detail that does not demonstrate judgment

**Never invent facts, metrics, users, feedback, or results.** Mark missing evidence as a gap.

## Follow-up test
Generate 10–12 likely Bar Raiser questions covering:
1. What was the actual problem?
2. What did you personally do?
3. Why this approach?
4. What alternatives did you reject?
5. How did you measure success?
6. How reliable were the results?
7. What went wrong?
8. What was the hardest part?
9. Did anyone disagree?
10. What were the trade-offs/costs?
11. What happens at larger scale?
12. What would you do differently?

For each, label: **SAFE** (story supports a strong answer), **PARTIAL** (answer exists but needs evidence), **GAP** (story cannot currently answer convincingly).

## Output
### 1. Verdict
- Bar Raiser readiness: **1–5**
- Strongest LP
- Biggest weakness

### 2. What works
3–5 strongest elements.

### 3. Biggest gaps
Rank the 3–5 most important weaknesses.

### 4. Credibility audit
For every important metric/claim: **Claim → likely challenge → evidence needed → keep / soften / remove**

### 5. Follow-ups
10–12 questions with SAFE / PARTIAL / GAP.

### 6. Repair plan
Give the **5 highest-impact changes**, prioritizing: 1) credibility 2) ownership 3) measurable impact 4) judgment 5) learning.

### 7. Recommended structure
Give a concise STAR-style outline for the improved version.

End with:
> **"What would still make me unconvinced as a Bar Raiser?"**
---
