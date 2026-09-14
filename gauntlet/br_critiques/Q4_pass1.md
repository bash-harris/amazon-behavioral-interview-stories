# Q4 Pass 1 — Bar Raiser Story Critic
**Story under review:** `answers/Q4.md` ("tell me about a time you failed" — BOM reconciliation pin-count mismatch)
**Critic run:** Pass 1 per `BR_CRITIC_SPEC.md`. Claims verified against: `AMAZON_INTERVIEW_PREPARATION.md` STORY 10 (lines 927–1015), `AMAZON_INTERVIEW_PREP.md` Stories 2/10/11 (behavioral folder), `LP_RUBRIC.md`, `BAR_RAISER_TECHNICAL_PREP.md` (line 201), `CODEBASE_DOCUMENTATION.md`, repo code (`deploy/SchematicvsEbom/`).

---

### 1. Verdict
- **Bar Raiser readiness: 3 / 5** — genuinely grounded story with strong ownership and real learning, but the headline metric has no measurement method, the LP re-tag contains two rubric-citation errors, and the discovery channel is embellished beyond the sources.
- **Strongest LP (as demonstrated):** Earn Trust — the vocal, specific self-criticism ("my wrong assumption, not bad data and not a subtle upstream bug") matches rubric strengths "Openly acknowledges mistakes" and "Takes responsibility for shortfalls" (LP_RUBRIC.md:114–115) without defensiveness or blame.
- **Biggest weakness:** The 12% → <2% false-positive result is asserted with no baseline definition, denominator, ground-truth source, or held-out set — and the candidate's own `BAR_RAISER_TECHNICAL_PREP.md` (line 201) documents a practice of tuning thresholds "with no held-out set to measure what it cost," which a prepared Bar Raiser could use to undermine the number.

---

### 2. What works
1. **Ownership is unambiguous and first-person throughout.** "I wrote a comparison," "I pulled twenty BOMs," "this was my wrong assumption." Near-zero "we." The explicit rejection of scapegoats (bad data, upstream bug) is exactly what Earn Trust concerns probe for.
2. **The failure is a real cognitive error, not a fake failure.** Building a rule on an unvalidated signal (pin count ≠ invariant under package variants / no-connects) is a credible, common, senior-level mistake, and the reflection names the *better* signal (reference designator + footprint name, STORY 10 line 979).
3. **Judgment in the fix is evidenced.** Three-category analysis of 20 failing BOMs (line 959), the two-stage rule (more pads → review, fewer → mismatch, line 963), then the discovered hole (wrong-but-larger footprint, line 965) and the type-check + configurable-threshold patch (line 967) — a documented chain of thought with a mid-course correction.
4. **Trade-offs are surfaced voluntarily.** False-negative risk of the heuristic (line 999), why ML was rejected (~200 examples, line 1007), why pin count wasn't just dropped (line 991). Rare in drafts.
5. **Provenance discipline is strong.** Line-level citations, one-telling rule, and explicit exclusion of the conflicting four-edge-case telling (verified: `AMAZON_INTERVIEW_PREP.md` Story 2, line 88, "False negatives dropped from 15% to under 1%" — correctly excluded).

---

### 3. Biggest gaps (ranked)
1. **Metrics without method.** 12% → under 2% (line 973) and "about 30 seconds" (TECHNICAL_PREP:201) are the only numbers anchoring impact; neither has a stated denominator, measurement process, or ground truth. Worse, the 30-second figure lives in a document that *self-criticizes* the absence of held-out measurement, and `AMAZON_INTERVIEW_PREP.md` Story 10 (line 387) says an engineer spent **30 minutes** verifying one false positive on a sibling tool — a 60× cross-story contradiction a BR can catch.
2. **Discovery channel embellished.** "Engineers' reports of false alarms drove the root-cause work" and "They had started re-checking the tool's output by hand" are not in STORY 10's sources — the Situation (lines 949–951) never says how the bug surfaced. The strong-signal bullet claiming "seeks out and accepts feedback" therefore rests on invented connective tissue; it's plausible framing but currently ungrounded.
3. **LP mislabeling risk.** STORY 10 is documented as covering "Dive Deep, Are Right, A Lot, Deliver Results, Have Backbone" (line 929) — not Earn Trust. Re-tagging is legitimate, but two cited signals are faulty: (a) the "LABC strong signal" quoted — "reacts to negative situations by focusing on how to improve for the future" — is a paraphrase of a **Concern** line (LP_RUBRIC.md:223 reads "focuses on what went wrong *rather than* how to improve"), not a strength; (b) "Honors commitments and makes good on promises" (line 118) has no documented commitment — nothing was promised to anyone in the sources.
4. **The fix contradicts the reflection.** The story's own lesson (line 979) is that pin count was "never the right signal — reference designator plus footprint name is." Yet the shipped fix keeps pin count as the core rule. No alternative "switch the matching key entirely" is discussed as considered-and-rejected. A sharp BR: "You said the right signal was different — so you fixed the wrong signal and called it done?" Currently unanswerable.
5. **Code-level evidence gap.** STORY 10's self-validation table (PREPARATION.md line 1493) claims "pin count comparison logic and the configurable threshold are in **bom_parser.js**." No `bom_parser.js` exists anywhere in the repository; neither `bom_server.py` nor `bom-verification.js` contains any pin-count/ratio/threshold logic (only DNP proximity threshold). The `/debug` route is real (CODEBASE_DOCUMENTATION.md:256, 950) but its documented payload is parser debug data, not the per-component pin/ratio/type decision table described. Either the artifact lived elsewhere or this piece of the story is documentation-only. Mark as verification gap — do not present code-level depth beyond what the docs support.

Minor: header claims "~440 words"; the core is **516**. The "honors commitments" bullet cites "core, para 5" but para 5 never mentions the regression suite (it's follow-up 4 only).

---

### 4. Credibility audit
| # | Claim | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | "~12% false-positive rate" baseline | How measured? Denominator — components, boards, or flags? Ground truth for "false"? | Definition of the metric + what it was computed over; sources give only the before/after numbers (line 973) | **Soften** to "false-positive *reports* dropped from about 12% to under 2% (counted per reported mismatch on mixed-type boards)" and mark method as a GAP if asked beyond the source |
| 2 | "…dropped to under 2%" | Any regression data at n=15 BOMs? Held-out set? Your own tech-prep doc says you tuned with no held-out set | Nothing more exists in sources; regression suite (line 1011) is 15 BOMs, 5 with mismatches | **Keep with hedge** — attribute to the 15-BOM suite scope, do not imply production measurement |
| 3 | "Engineers stopped hand-verifying… used the debug view" | How do you know usage changed? Telemetry? | Line 973 supports "could now trust… without manually verifying"; *observed* adoption is inference | **Soften** to source wording; adoption evidence = GAP |
| 4 | "False alarm costs ~30 seconds" | Measured or assumed? Story bank elsewhere says 30 *minutes* | TECHNICAL_PREP:201 is a cost-of-error maxim in a self-critique, not a measurement; PREP Story 10:387 says 30 min for a different tool | **Soften** — present as an order-of-magnitude assumption and state it as such; reconcile the 30s-vs-30min collision or drop |
| 5 | "I pulled twenty BOMs and categorized them" | Where did the 20 come from — reported failures or your own scans? | Line 959 supports collection/categorization; provenance of the 20 is silent | **Keep**; mark discovery channel as GAP |
| 6 | "Default 2:1 from analyzing the 20 BOMs" | 20 boards is a thin base for a ratio rule | Line 995 documents exactly this reasoning — and invites "n=20?" pushback | **Keep**, but pre-empt: state the config escape hatch (line 995) and review-flag path as the hedge |
| 7 | "~200 examples for ML; too small" | 200 examples but you analyzed 20 BOMs? Consistent? | Line 1007 supports ~200 examples; reconciliation with the 20 BOMs (examples-per-BOM) needs one sentence | **Keep** with one bridging clause |
| 8 | "BOM lists 'U1 (8-pin)', footprint has 16 pads" | Real board? | Line 949 verbatim | **Keep** |
| 9 | Debug endpoint shows per-component decision trace | Show me; where's the code? | Line 1003 documents the fields; `/debug` route real (CODEBASE_DOCUMENTATION:256); pin-logic file `bom_parser.js` not found in repo | **Keep** at documentation level; **never claim code artifacts that can't be pointed to** — flag as verification gap |
| 10 | "Not bad data, not an upstream bug — my assumption" | Was any part of it upstream? | Line 979 reflection supports self-attribution | **Keep** — this is the story's spine and it's solid |
| 11 | Earn Trust "honors commitments" signal | What commitment? | No commitment documented | **Remove/replace** with "Takes responsibility for shortfalls" (LP_RUBRIC:114) |
| 12 | LABC "reacts to negative situations focusing on improvement" as strength | That's a Concern line | Correct strengths: "Discusses lessons learned from past setbacks" (231), "Seeks and embraces feedback" (230) | **Fix citation** |

---

### 5. Follow-ups (Bar Raiser probe test)
1. **What was the actual problem?** — **SAFE.** False alarms from a literal comparison; concrete U1 example.
2. **What did you personally do?** — **SAFE.** I wrote the rule, I collected the 20 BOMs, I changed the logic, I built the endpoint.
3. **Why this approach (type + ratio) rather than something else?** — **PARTIAL.** Categorization-driven rationale documented (959–967), but no explanation of why the *review-flag* middle state was right instead of ask-the-engineer-first.
4. **What alternatives did you reject?** — **GAP (critical).** ML and "ignore pin count" are covered (991, 1007), but the story's own reflection names reference-designator + footprint-name as *the right signal*. "Why didn't you just fix the matching key?" cannot currently be answered — the strongest version of this question is unstaffed.
5. **How did you measure success?** — **GAP.** 12%→<2% has no defined method, denominator, or ground-truth source anywhere in the banks.
6. **How reliable were the results? Would they hold on unseen boards?** — **GAP.** 15-BOM suite; 20-BOM analysis; no holdout. The candidate's own TECHNICAL_PREP finding ("no held-out set to measure what it cost") is usable against them.
7. **What went wrong?** — **SAFE.** The failure *is* the story; second-order discovery (wrong-but-larger footprint, line 965) shows the fix itself broke under new evidence.
8. **What was the hardest part?** — **PARTIAL.** Material exists (the 965 setback mid-fix, the threshold justification) but the answer never narrates a hardest moment; builder can ground this without invention.
9. **Did anyone disagree with you?** — **GAP.** No documented disagreement in STORY 10 or banks for this event.
10. **What were the trade-offs/costs?** — **SAFE.** False-negative risk (999), heuristic-not-proof framing, configurable threshold, review flags.
11. **What happens at larger scale — hundreds of board types?** — **PARTIAL.** Configurable threshold + per-board override are documented (995, 1015), but maintenance cost of ratio rules across package families is unaddressed.
12. **What would you do differently?** — **SAFE.** Diverse data upfront (977), better signal (979), day-one observability (PREP Story 10, line 415 — used only as a transferable lesson).

Score: 5 SAFE / 4 PARTIAL / 3 GAP — the three GAPs cluster on **measurement and alternatives**, not on character.

---

### 6. Repair plan (builder: no invention; soften or mark gap)
1. **Credibility — anchor the numbers honestly.** Restate 12%→<2% exactly as the source words it ("false positive reports... for boards with mixed component types," line 973); add one sentence defining what was counted *if and only if* supportable — otherwise add a provenance note "measurement method: not documented — GAP." Replace the bare "thirty seconds" with an explicitly labeled estimate and drop the confident cost math.
2. **Credibility — fix the two rubric errors.** Remove "Honors commitments" (no commitment exists); substitute "Takes responsibility for shortfalls" (LP_RUBRIC:114). Re-label the LABC bullet to the actual strengths "Discusses lessons learned from past setbacks" (231) / "Seeks and embraces feedback" (230) — never quote a Concern line as a strength.
3. **Ownership of the discovery channel.** Delete or soften "engineers' reports drove the work" and "they had started re-checking by hand" to what line 973 supports (they *could now* trust the report without manual verification), and mark "how the bug surfaced" as an open GAP with a note to keep it consistent with whichever channel actually occurred.
4. **Judgment — staff the unanswerable question.** Using only source material (979 + 991 + 965–967), add a follow-up: "Why keep pin count if refdes+footprint name was the right signal?" — grounded answer shape: refdes+footprint name fixes the *matching* decision, but the pin/pad relationship still had to gate *component-fit* errors (the 16-pin-on-8-pad case, line 991); the ratio rule was the minimum fix that preserved genuine-mismatch detection while the key-change was scoped. If the sources won't carry it, mark it as a GAP instead of fabricating.
5. **Scope the reliability answer.** In follow-up 4 (regression) and the Result paragraph, bound the claim to the 15-BOM suite and mixed-type boards — pre-empt the "no holdout" attack by naming the suite as the evidence base rather than implying production measurement. (Bonus fixes: header word count ~440 → ~516 or trim to ≤450; correct the "core, para 5" citation for the regression claim; keep the Story 2 exclusion note, which is correct.)

---

### 7. Recommended structure (improved STAR outline)
- **S (3 sentences):** I built the BOM reconciliation tool comparing BOM against layout. I shipped one rule — pin count must equal pad count — on an untested assumption. On mixed-type boards it flagged correct parts: false-positive reports ran about 12%, e.g. "U1 (8-pin)" vs a 16-pad footprint serving package variants/no-connects. *(Ground: 949–951. No invented discovery channel.)*
- **T (1–2 sentences):** My job: fix the false alarms without letting genuine mismatches — like a 16-pin part on an 8-pad footprint, physically impossible — slip through. *(Ground: 955, 991.)*
- **A (beats):** (1) Owned it publicly as my assumption, not data or upstream. *(979.)* (2) Collected and categorized 20 failing BOMs into three types. *(959.)* (3) Rule change: more pads → review flag, fewer → definite mismatch. *(963.)* (4) Hit a second-order hole: wrong component, larger footprint *(965)* → added type-check + configurable 2:1 threshold *(967, 995)*. (5) Built per-component debug view exposing counts, type match, ratio, decision, with override. *(1003.)* (6) Considered and rejected: dropping pin count *(991)*, ML on ~200 examples *(1007)*.
- **R (bounded):** False-positive *reports* on mixed-component-type boards dropped from about 12% to under 2% *(973)*; verified on the 15-BOM regression suite — 5 fixed, 10 unchanged, no previously-correct match regressed *(1011)*. State scope plainly; do not imply a production measurement.
- **L (three layers):** Signal = hypothesis until it fails across diverse samples *(977)*; the deeper error — wrong signal choice, refdes+footprint name beats pin count *(979)*; and observability from day one *(PREP Story 10:415, as transferable lesson).*
- **Pre-empted probes:** "was there a holdout?" / "why not the better signal?" / "who told you it was wrong?" — answer only from the four sources above; anything else = named gap.

---

> **"What would still make me unconvinced as a Bar Raiser?"** — The result numbers. A 12%→<2% improvement measured on a 15-board suite, chosen and labeled by the same person who wrote the rule being tested, with no stated ground truth, no held-out set, and a self-authored technical review in the same folder confessing to exactly that failure mode ("tuning on the same boards I was looking at... no held-out set to measure what it cost"). If the candidate cannot say *what the denominator was and who confirmed the boards were actually correct*, the whole "Results" paragraph — and with it the claim that they now treat signals as hypotheses — collapses into the very behavior the story is supposed to atone for.
