# Q3 — Pass 2 BAR RAISER Critique (repaired story)

Story: `answers_v2/Q3.md` — genAI solving a business problem with a measurable result (BGSW PCB Inspector Suite, GPT-4o VLM).
Sources re-checked for pass 2: `AMAZON_INTERVIEW_PREPARATION.md` STORY 8 (lines 755–841: 757, 777, 783, 787–793, 797, 799, 805, 813, 817, 821, 825, 829, 833, 837, 841) + STORY 4 (line 459) + Project Context (line 4); `AMAZON_INTERVIEW_PREP.md` STORY 1 (line 55), STORY 3 (lines 123, 134, 137, 140), STORY 12 (lines 466, 481–482); `LP_RUBRIC.md` (lines 53–59, 75–78, 207–210); `BAR_RAISER_TECHNICAL_PREP.md` (lines 42–63, 102, 368); `STORY_LEDGER.md` (Q3 = PASS). Every provenance line reference in the repaired answer was spot-checked against the source; all cited lines are accurate.

## Repair verification (pass-1 plan → pass-2 state)

| Pass-1 repair item | Status | Evidence |
|---|---|---|
| 1. Measurement-method disclosure + reconcile 3s vs 5s | **DONE** | Core para 5: "estimates logged from validation use, not an instrumented study: no labeled eval set, no recorded sample size"; one reconciled line "typical response ~3s, inside the 5s budget"; provenance line 65 names the source tension (813 vs 797). No new numbers invented. |
| 2. Fix borrowed claims (sessions purpose, "expert eye") | **DONE, one residual** | "Expert eye" quote gone; custom-classifier rejection restated as plain trade-off and honestly sourced to PREP STORY 3:123 in provenance (line 72). Sessions re-scoped to the comparison workflow the AI "built on top of, not designed from fresh observation." Residual: "before writing the *first* comparison tool" — the sessions (PREP STORY 1:55) preceded the *Good Board* tool, which STORY 12 places third (week 5–6). Timeline imprecision, new. |
| 3. Qualify suite adoption; delete "slowest boards" | **DONE** | "the *suite* — not the AI specifically — was adopted by 15 engineers across two sites; I never instrumented feature-level usage"; "slowest boards" phrase absent from entire file. Verified against STORY 12:466, 481–482. |
| 4. Ready reconciliation of BYOK panel vs no-VLM standalone | **DONE, one residual** | Dedicated follow-up Q (lines 49–50) resolves via documented mechanism: panel built (793) + "if no API key is configured, the VLM analysis is gracefully disabled" (793) + deployed standalone doesn't use the VLM (459). Residual: "the standalone build as deployed to the floor *shipped with no key*" asserts the causal bridge as history; sources document panel + disable-mechanism + no-VLM outcome, not the shipping decision. Provenance line 67 nearly flags this but then labels the bridge "two documented facts." |
| 5. Feedback-loop follow-through in learning | **DONE (as far as sources allow)** | No invented catch; follow-up 2 states errors "surface systematically"; provenance line 75 admits what it surfaced is undocumented. Minor mismatch: the body never volunteers the "what did it catch — unknown" line, it lives only in provenance. |
| Header LP fix | **DONE** | Now matches STORY 8's actual header (line 757: Invent and Simplify, Think Big, Learn and Be Curious, Customer Obsession); Deliver Results honestly routed to STORY 12 with "I'll say so if pressed." |

**New overclaims flagged:** (a) follow-up 2's "the analyses checked against what the engineers' inspection actually found" — line 797 documents no such checking mechanism; this dresses an undocumented origin in plausible clothing (hedge "Measured is too strong a word" partly saves it, the specificity doesn't). (b) "shipped with no key" causal bridge (above). (c) "first comparison tool" timing (above). All three are small; none reintroduces a fabricated metric.

## 1. Verdict

- **Bar Raiser readiness: 4.5 / 5** (pass 1: 4/5). Improved: all five pass-1 repairs landed without inventing facts; the three live contradictions (3s/5s, BYOK-vs-no-VLM, borrowed session purpose) now have ready, source-exact reconciliations instead of provenance-only awareness; the one rhetorical claim outrunning evidence is deleted; the LP header matches the source. The remaining half-point is **source-capped, not writing-capped**: no honest repair can manufacture a measurement protocol or floor-level AI-usage data that the record does not contain.
- **Strongest LP:** Invent and Simplify — now correctly labeled per the source header, and demonstrated by documented rejections (custom classifier, three alternative VLMs, per-component VLM on cost/auditability), schema-first prompting, flagged-regions-only scaling, and enhancement-not-dependency architecture.
- **Biggest weakness:** The question demands a *measurable* genAI result. The repaired answer's honest ceiling is: documented per-mismatch estimates with no protocol, labeled-derived board arithmetic, one reported anecdote, and suite-level (never AI-level) adoption — deployed where the VLM ran (server) is not where the floor worked (offline tool). Causation from genAI to a measured business outcome remains unproven; it is now disclosed rather than papered over, which survives questioning but cannot win the "Data Driven" half of the question.

## 2. What works

1. **Every softening traces to a line.** 85% and 30s→5s explicitly demoted to "documented estimates"; the 100-pair F1 methodology is *not* borrowed from the excluded 92% telling (provenance line 64) — the exclusion rule is kept intact under pressure, which is exactly what pass 1 demanded.
2. **The pass-1 traps now have scripted answers.** The BYOK contradiction has a dedicated follow-up with a one-sentence resolution ("The code path existed; the feature was not live on the floor"); the 3s-vs-5s tension has one reconciled line; both read as resolved knowledge, not open questions.
3. **Ownership and register intact.** "I was the only developer" (line 4: "built entirely solo"), first-person failure, no "we"-laundering, and the STORY 4 natural voice survives the lawyering — the caveats are spoken ("I want to be explicit…"), not just footnoted.
4. **Scope language is actively self-limiting.** "The honest business-impact claim is:", "designed, not built" for the cascade (per TECH_PREP:368), "not something I evaluated or ran" for LLaVA (per 837), "I won't tell you an offline AI usage story I can't substantiate."
5. **The learning line is real:** wrong assumption (value OCR on SMD, line 805), simpler-prompt-first, and the named next step (labeled eval set + feature telemetry) that directly targets the disclosed gaps.

## 3. Biggest gaps (ranked)

1. **The genAI→measured-result causal link is still empty at the floor.** Disclosed, not fixed: server-only VLM, floor on offline tool, feature-level usage never instrumented, one unnumbered engineer anecdote (line 799). A BR can accept the honesty and still conclude: capability shipped, business problem measurably solved — unproven.
2. **The softened numbers gained a slightly-over-specified origin.** "Logged from validation use — the analyses checked against what the engineers' inspection actually found" asserts a validation mechanism no source documents. Keep the caveat, drop the mechanism claim or mark it memory ("as best I can recall, these were spot-checked against engineer findings — that's why I won't call it measured").
3. **Two inference-presented-as-fact seams:** "the deployed standalone shipped with no key" (bridge, not record) and "before writing the *first* comparison tool" (sessions preceded the *third* tool per STORY 12's sequence). Both are the kind of detail a prepared BR with the deeper bank pokes.
4. **Error direction still unmeasured.** 85% is a combined "component type and mismatch type" figure (797); no precision/recall split, no answer for "what happens when a real defect is called a false alarm." Suggestion-not-verdict architecture (829) mitigates but doesn't measure. Provenance flags the feedback-loop outcome gap; the body never volunteers it.
5. **No disagreement record for the AI itself.** Security conversation (841) is documented; engineer skepticism, if any, is not — Q9 ("did anyone disagree") has only a non-answer.

## 4. Credibility audit

| Claim (as now stated) | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|
| 30s→~5s, ~85% — "documented estimates logged from validation use" | "Logged how? Checked against what, by whom?" | Protocol — does not exist in sources | **Keep** (correctly softened) — but **soften again** the "checked against what the engineers' inspection actually found" clause; mechanism undocumented |
| Server build attribution ("figures belong to the server build") | "Line 797 names no build" | — | **Keep** — provenance correctly marks it inference from STORY 4:459 + key-handling; consider "almost certainly the server build" in the spoken line |
| "Typical response ~3s, inside the 5s budget" | "Your own notes say ~5s" | — | **Keep** — reconciled (813 vs 797), single line now |
| 5–20 mismatches/board; ~$0.01/analysis; ~$0.10/board | "Token math?" | Two ~1k-tok images + ~200 prompt + ~100 out at $2.50/$10 per M | **Keep** — 821, 833; reproducible |
| 10-mismatch board 5 min → under a minute | "Measured?" | — | **Keep** — labeled derived in spoken text; correct practice |
| "Deployed standalone shipped with no key → feature disabled" | "Where does the record say what shipped?" | Deployment history | **Soften** — say "as deployed, the standalone never had a key configured, so by design the VLM sat disabled"; keep the mechanism (793), flag the bridge as inference |
| "Sat in on three sessions before writing the first comparison tool" | "Wasn't Good Board your third tool?" | Timeline | **Soften** — "before writing the Good Board comparison tool" (PREP STORY 1:55); STORY 12 sequence otherwise contradicts |
| Model evals: 4V ~8s, Claude 3 immature API, Gemini weak small SMD | "Benchmark or vibes?" | — | **Keep** — 813 |
| Custom-classifier rejection (labeling/retraining per defect type) | "Source?" | — | **Keep** — honestly re-sourced to PREP STORY 3:123 in provenance, quote dropped |
| Suite adoption: 3 tools/8 weeks, 15 engineers, 2 sites | "AI adoption?" | — | **Keep** — qualified "suite — not the AI"; explicit no-telemetry admission; correct per STORY 12 |
| "Engineers reported AI helped prioritize on dense boards" | "How many? Written?" | n, form | **Keep as anecdote** — 799; provenance admits count/format undocumented; consider volunteering that in the spoken line |
| Suggestion + confidence + correct/incorrect feedback | "What did the loop catch? Error direction?" | Outcomes; precision vs recall | **Keep, PARTIAL** — 829; outcomes undocumented; body should volunteer it as provenance does |
| Security approved photos (no trade secrets) | "DPA or conversation?" | — | **Keep** — 841, provenance honest ("no vendor-DPA paperwork claimed") |
| LLaVA ≥8GB VRAM, future-only | "Considered during build?" | — | **Keep** — 837; framing held |
| Cost-aware cascade | "Built?" | — | **Keep** — "designed, not built" per TECH_PREP:368 |
| 92%/100-pair telling excluded | — | — | **Correct exclusion maintained** — and F1 methodology explicitly refused as dressing for 85% |
| LP header (I&S primary; DR via STORY 12, disclosed) | — | — | **Keep** — matches line 757; STORY 12 routing honest |

## 5. Follow-ups (12)

1. **What was the actual business problem?** — **SAFE** (interpretation bottleneck, 777).
2. **What did you personally do vs the API?** — **SAFE** (solo dev; pipeline/prompt/parse).
3. **How was ~85% measured — n, ground truth, who labeled?** — **PARTIAL** (was GAP pass 1; disclosure is now scripted and pre-commits to the eval-set answer, but there is still no protocol behind the number; the added "checked against engineer inspection" line is itself challengeable — see audit).
4. **30s→5s: timed or estimated?** — **PARTIAL** (same disclosure; baseline timing method remains absent).
5. **The floor ran the offline tool with no VLM. What measurable result did the genAI actually deliver in production?** — **GAP** (disclosed; the honest answer is estimates + derived math + one anecdote on a server build. Unfixable without new facts).
6. **How many of the 15 engineers used AI Analysis, and how often?** — **GAP** (explicitly never instrumented; answer correctly names telemetry as the first fix).
7. **Why hosted GPT-4o over custom or self-hosted?** — **SAFE** (documented evals, honest rejections, LLaVA held to future-only).
8. **What's the recall on real defects — when the AI calls a genuine defect a false alarm, what happens?** — **PARTIAL** (suggestion-not-verdict + mandatory human verify, 829; no error-direction measurement exists).
9. **Your record says both "built a standalone BYOK panel" and "standalone doesn't use the VLM." Which is it?** — **SAFE** (dedicated reconciliation follow-up; mechanism-level answer from 793 + 459).
10. **Is the API 3 seconds or 5 seconds?** — **SAFE** (single reconciled line, budget explicit).
11. **Did anyone disagree with putting an LLM in a verification workflow?** — **PARTIAL** (security sign-off documented, 841; no engineer-disagreement record for the AI exists).
12. **What happens at 500 components × 1,000 boards/day? What would you do differently?** — **SAFE** (flagged-regions-only scaling, per-component refusal on cost/auditability per TECH_PREP:102, cascade as designed-not-built; learning line grounded in 803–805).

## 6. Repair plan (5 highest-impact, pass-2 residual)

1. **Credibility — strip the invented-feeling mechanism.** In follow-up 2 and core para 5, downgrade "the analyses checked against what the engineers' inspection actually found" to explicitly recalled-level framing ("what I can honestly tell you is how they were *used*, not how they were *tabulated*"). The caveat is the strength; the mechanism claim is the new soft spot.
2. **Credibility — mark the two inference seams as inference in the spoken text:** "as deployed, the standalone never had a key configured, so the VLM stayed disabled" (not "shipped with no key") and "before writing the Good Board tool" (not "first"). Both are one-word fixes that remove the only places a fact-check can catch the story in a lie the sources don't tell.
3. **Measurable impact — volunteer the two remaining holes before being asked,** in the Result's last breath: "nobody ever counted how many times the AI analysis was opened, and nobody split the 15% into missed-defects vs false alarms." Pair each with its named fix (telemetry, eval set with per-class PR). Converts the two GAP follow-ups into demonstrated Dive Deep instead of discovered exposure.
4. **Judgment — add one rejection-of-alternative with a number already in hand:** on "why accept 85%," cite the architecture *and* the cost asymmetry — a wrong AI guess costs a re-look the engineer was going to take anyway; a missed defect costs far more, which is exactly why per-component auto-verdicts were refused (TECH_PREP:102). Documented material, sharper trade-off framing.
5. **Learning — surface the feedback-loop honesty line from provenance into the body:** "the correct/incorrect buttons existed; what they caught I never compiled into a number — another thing I'd instrument." One sentence, kills the last unsourced-sounding implication in Customer Obsession.

## 7. Recommended structure (STAR outline, pass-2 state)

- **S (45s):** Floor verification bottleneck — tool says *where*, not *what*; ~30s interpretation × 5–20 mismatches/board (documented); solo developer; my job: delete the step.
- **T (20s):** <5s per analysis, accuracy worth the operator's attention, deterministic core must survive; API-access constraint splits server vs offline standalone (783, 459).
- **A (2 min):** (1) model eval + rejections (4V/Claude 3/Gemini; custom classifier; no per-component VLM); (2) pipeline: crop layout+photo, fixed JSON schema, examples after verbose-prompt failure; (3) guardrails: suggestion+confidence+verify+feedback, graceful API-down behavior, security sign-off; (4) parallel delivery: 3 tools/8 weeks, suite (not AI) adopted by 15 engineers, 2 sites.
- **R (60s):** Stated as documented estimates: 30s→~5s, ~85% on type+mismatch, ~3s typical inside the 5s budget, ~$0.01/analysis; board math labeled derived; one engineer-report anecdote; *volunteer* the three absences — no eval set, no feature telemetry, no error-direction split; server-only scope and no-VLM-on-floor admitted unprompted.
- **L (30s):** Value-OCR assumption was wrong; simpler prompt first; labeled eval set + feature-level telemetry are the explicit next measurements; cascade designed, not built.

> **"What would still make me unconvinced as a Bar Raiser?"** The candor is now airtight — but candor is not evidence. The question asked for a measurable result, and after every honest fix, the genAI's measured footprint is: two estimates no one can show me a protocol for, arithmetic I derived myself on a board build the factory floor never ran, and zero counts of anyone actually using the AI feature. I'd believe the engineer is trustworthy — I would not believe the business problem was *measurably* solved by genAI. If this candidate wants a 5, the repair is not in the story; it's in building the labeled eval set and usage telemetry this quarter, so the next telling replaces "documented estimate" with "measured."
