# Bar Raiser Critique — Q1 (PASS 2)

**Question:** "Tell me about a time you used genAI to improve personal or team productivity."
**Story under review:** BGSW PCB Inspector Suite — GPT-4o VLM analysis feature (`gauntlet/answers_v2/Q1.md`, repaired per pass-1 plan)
**Verification basis:** Every claim re-checked line-by-line against `behavioral/AMAZON_INTERVIEW_PREPARATION.md` STORY 8 (lines 755–841), `behavioral/AMAZON_INTERVIEW_PREP.md` Story 1 (35–64) / Story 3 (106–140) / Story 12 (459–496) / Part 6 Key Metrics (582–592), `BAR_RAISER_TECHNICAL_PREP.md` Part 0 (:26, :322), Part 1 Tier 1 item 1 (:42–61), Part 2 Finding 4 (:176–205), `behavioral/LP_RUBRIC.md` :207–211, `CODEBASE_DOCUMENTATION.md` Tech Stack (:56–62), and `STORY_LEDGER.md`. Tab Scroller docs: N/A (Q1 cites none).

---

## 1. Verdict

- **Bar Raiser readiness: 4 / 5** (pass 1: **3 / 5** — improved, and the improvement is real, not cosmetic)
- **Strongest LP:** Invent and Simplify — still carried by the sourced external-model evaluation, "engineering spent on preprocessing, not the model," and degradation-away-from-AI design (LP_RUBRIC.md:207–211 quoted accurately).
- **Biggest weakness:** The number reconciliation overcorrects at one seam: the story now asserts **92% F1 "measures the engine, not the AI's description"** — but the candidate's own second bank says the 92% was computed by "compar[ing] GPT-4o's response against the ground truth" (`AMAZON_INTERVIEW_PREP.md` Story 3, validation follow-up, line 137). The collision was papered over, not dissolved — and `STORY_LEDGER.md` shows Q3 reuses the same VLM story, so both tellings can surface in one loop.

Why improved from 3 to 4: every pass-1 killer is gone. 30 s is now labeled an estimate, 5 s is labeled machine time, the confirm step is admitted uncosted, 85% is labeled self-assessment with no held-out set, the standalone-build and screen-sharing overclaims are fixed toward honesty, suite-level metrics are correctly attributed, and the 85/92 and 3/5/2 s collisions have a rehearsed reconciliation plus a dedicated ledger. Nothing was fabricated. The remaining weakness is one over-tightened sentence, a minor arithmetic pairing error, and the two gaps that cannot be closed without inventing facts (friction, feature-level volume) — which the story now owns explicitly. Why not 5: a Bar Raiser who probes twice still finds zero quantitative productivity result at feature level — the story survives by disclosure, not by data.

---

## 2. What works

1. **The credibility repair is the model of how it should be done.** "Most of their thirty seconds, not all of it, and I never costed the confirm step"; "that's API time, not engineer time"; "I quote 85% as a ballpark, never as validated accuracy." Each softening *adds* trust rather than subtracting impact — the candidate sounds like someone who has been burned by their own metrics and learned.
2. **The Number ledger + provenance section.** Eleven numbers, each with what-it-measures / basis / status, including two rows ("~2 s — do not mix"; "open item to collect — not a claim") that pre-empt exactly the traps pass 1 identified. The dedicated "Is it 85% or 92%?" follow-up shows the collision is rehearsed, not discovered live.
3. **Ownership stays airtight and is now correctly scoped.** Solo-builder "I" throughout; pass-1's two attribution errors fixed *in the strengthening direction* (user-supplied key + graceful disable is more impressive than "runs offline"; screen-sharing moved to project start "for the original tool," with the in-product feedback loop named as the AI-era input).
4. **The trust design is assembled into one argument** — suggestion-not-verdict, per-analysis marks, opt-in key, security sign-off, offline fallback, error-asymmetry rationale — each element traceable to STORY 8 follow-ups, Story 3 risk mitigations, or Technical Prep Part 2.
5. **Learning is specific, repeated consistently, and self-critical in three places** (failed prompt, SMD-OCR assumption, and — the strongest — "I logged the wrong marks; I never turned them into a number"). The missing-measurement admission is never downplayed differently in different sections, which is what makes it survive round 3.

---

## 3. Repair-landing check (vs pass-1 plan) + remaining gaps

**Did the five repairs land?**

| Pass-1 repair | Landed? | Note |
|---|---|---|
| 1. Rebuild headline numbers (30 s estimate / 5 s turnaround / 85% labeled / 92-vs-85 reconciliation) | **Yes, except one overcorrection** | The reconciliation reassigns 92% to "the engine, not the AI" — contradicted by Story 3's own validation text. See gap #1. |
| 2. Volume with real attribution (15 eng / 20 h/wk = suite, not feature; telemetry flagged as open) | **Yes** | Correctly attributed; no invented feature-level numbers. Residual thinness is factual, not rhetorical. |
| 3. Fix overreach sentences (standalone key; screen-share timeline) | **Yes** | Both verbatim-faithful to STORY 8 / Story 1 now. |
| 4. Assemble trust architecture | **Yes** | With one retro-fit: asymmetry (Part 2 Finding 4) is a *retrospective audit finding* in the source, presented as day-one design motive. |
| 5. Close failure-mode hole (asymmetry + correction-rate admission) | **Yes** | "Categories, not a tally" is the honest answer the sources allow. |

**No fabrication detected** — every number, mechanism, and quote traces to a source line. Two extrapolated *phrasings* (not facts): the "ran candidates side by side manually on the actual task" eval protocol (source says only "I evaluated…"; but pass-1 prescribed this wording), and the 92% re-attribution below.

**Remaining gaps (ranked):**

1. **The 92% "engine, not AI" line over-concludes.** Story 3's validation follow-up: 100-pair set, "ran the pipeline on each pair and compared **GPT-4o's response** against the ground truth… 92% was the F1." So the defensible statement is "92% = end-to-end pipeline accuracy *including* the VLM step, in the Story-3 telling; 85% = the description add-on's self-assessment, in the STORY-8 telling; different features, different accounts." v2's stronger claim ("measures the engine, **not** the AI") invites exactly the round-3 collapse the ledger exists to prevent — and Q3 re-tells the same work with 92% as the VLM-as-engine number.
2. **Feature-level productivity remains unquantified — by the facts, not by the telling.** Savings = estimate (30 s) + labeled ballpark (85%) + unclosed confirm cost + qualitative triage feedback. Every element is honestly framed, but "improved productivity" still rests on disclosure rather than data. This caps the story at 4, not 5.
3. **Post-launch verification hole persists:** feedback marks never tallied ("which systematic errors surfaced?" → "categories, not a tally"); no adoption/friction evidence mined; no conflict anywhere in the record. Now *owned* (good), but still the soft spot a Bar Raiser reads as "shipped, not instrumented."
4. **Arithmetic pairing slip in the scale answer:** the ~25× cut is the source's **4%-band** scenario ($1.50 → $0.06); at the 13% band the same source gives $1.50 → $0.20 ≈ **7.5×** (`BAR_RAISER_TECHNICAL_PREP.md`:56–61). v2 pairs "85/13/2" with "around 25×." Small, but this is a *design-target* number whose whole point is cost-model rigor.
5. **Unprobeable specifics kept as-is:** security sign-off has no named approver/artifact (source: "discussed with the security team and they approved"); model-eval protocol is prescribed phrasing without a concrete memory behind it. Survivable, but the candidate must know where each bottoms out.

---

## 4. Credibility audit

| # | Claim (as v2 states it) | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | "~30 s — the engineers' *own estimate*" per flagged region | "Source-of-estimate — they told you that, or did you time it?" | Nothing more exists; STORY 8 states 30 s unattributed | **KEEP** — conservative attribution; hold the line "no timed study, that's the order they gave me" |
| 2 | "~5 s = model turnaround, API time, not engineer time; confirm step never costed" | "So your headline saving is unmeasured?" | — | **KEEP** — this is now the honest version; the admission *is* the answer |
| 3 | "85% — rough self-assessment from engineers' correct/incorrect marks; no held-out set" | "Were marks logged from day one? Over how many analyses?" | N, start date of feedback mechanism — neither in sources | **KEEP** as-labeled; bottom out at "I don't have a denominator. That's the hole." |
| 4 | "92% F1 measures **the engine, not the AI's description**" | "Your other write-up says the F1 compared GPT-4o's responses to ground truth. Which is it?" | Story 3 line 137 contradicts "not the AI" | **SOFTEN** → "92% = the Story-3 end-to-end pipeline account (VLM included), validated on 100 labeled pairs; 85% = the STORY-8 add-on descriptor account, self-assessed. Different telling of overlapping work; I never mix them." |
| 5 | Cascade: "85/13/2 split… cutting per-board model spend by around 25×" | "Show me the math" | Source: 25× = $1.50→$0.06 at a tightened **4%** band; 13% band = **7.5×** | **SOFTEN** → "~7.5× at the modeled band, up to ~25× if better signals tighten it to 4%" |
| 6 | "All of this leans human-in-the-loop **because of** error asymmetry" | "Was that your reasoning at design time, or after?" | STORY 8's stated motive is engineer expertise + suggestion framing; asymmetry is Part 2 Finding 4 (retrospective threshold audit) | **KEEP with reframe** → "the design already leaned that way; the asymmetry argument is how I later understood why it was right" — doubles as learning |
| 7 | "Ran candidates side-by-side on the actual task, manually" | "What was the eval protocol? Show me one comparison" | Sources say only "I evaluated" + outcome dims (speed, API maturity, small-object) | **KEEP** (pass-1 prescribed); candidate must be able to narrate one concrete comparison or retreat to "I tried them on real flagged regions and compared outputs" |
| 8 | Security team approved cloud API (no trade secrets) | "Who signed off? Written record?" | Name/role/artifact — not in sources | **KEEP**, bottom out honestly: "a review conversation, not a certificate" |
| 9 | 15 engineers / 2 sites / ~20 h/wk attributed to **suite**, telemetry gap flagged "collect before interview" | "Fine — but what's the AI feature's number?" | Feature-level usage — exists nowhere | **KEEP** — exemplary attribution discipline; residual GAP is factual |
| 10 | GPT-4o ~3 s vs GPT-4V ~8 s per request, reconciled against ~5 s end-to-end and the other telling's ~2 s | "Three latency numbers for one feature?" | — | **KEEP** — reconciliation is now the story's own follow-up Q2/Q6 |
| 11 | Standalone: user key in localStorage → direct to OpenAI; no key → AI self-disables, comparison runs | "So 'offline AI' was never a claim?" | — | **KEEP** — corrected; strongest true version |
| 12 | Trust cluster (suggestion-not-verdict, marks, 429×3, 512×512 ROI cap + caching as *risk controls*, ~$0.01/~$0.10, LLaVA ≥8 GB VRAM rejection, degradation path) | "Caching hit rate?" (already answered: none) | — | **KEEP** — all verbatim or correctly re-attributed (Story 3 follow-up + STORY 8 follow-ups verified) |
| 13 | LP mapping & rubric quotes | — | LP_RUBRIC.md:207–211 checked | **KEEP** — quoted exactly, no stretch |

---

## 5. Follow-ups (12 likely Bar Raiser probes)

1. **"What was the actual problem?"** → **SAFE.** Where-not-what gap, 5–20 regions, last manual step — all sourced, volume framing honest.
2. **"What did you personally do?"** → **SAFE.** Solo builder; every action is an "I."
3. **"Why a VLM instead of a classifier you could train?"** → **SAFE.** Custom-classifier avoidance, degrades away from AI, model improves with API updates.
4. **"How exactly did you evaluate the four models?"** → **PARTIAL.** Protocol is prescribed phrasing, not sourced detail; needs one concrete comparison or the honest retreat.
5. **"How did you measure the 30 s → 5 s?"** → **PARTIAL.** Was GAP; now survives as disclosure (estimate + machine time + unclosed confirm) — but the disclosure is the answer, not the data.
6. **"How reliable is 85%?"** → **PARTIAL.** Basis and limit now stated proactively; denominator still doesn't exist.
7. **"Your other story says 92% F1 measured GPT-4o's answers. Here you say 92% isn't the AI's number. Which?"** → **GAP** as currently worded; **PARTIAL** after the #4 softening. This is the probe the repaired version can still fail.
8. **"What went wrong?"** → **SAFE.** Failed prompt, wrong OCR assumption, missing measurement — three, specific, consistent.
9. **"What was the hardest part?"** → **PARTIAL.** Still under-told; prompt convergence named, key-handling/accuracy-vs-latency squeeze not dramatized. Pick one, rehearse depth.
10. **"Did anyone push back on an AI grading their judgment?"** → **GAP** (honestly owned: no friction exists in the record). Cannot be repaired without inventing facts; the "I never mined the incorrect-marks" answer is the best available and is given.
11. **"What did it cost, and what breaks at 10×?"** → **SAFE** — trivial at documented volume, fleet-scale breakage named, cascade explicitly labeled design-not-built; fix the 25×/13% pairing (audit #5) and the arithmetic itself becomes a strength.
12. **"What would you do differently?"** → **SAFE.** Three answers, all sourced, the held-out-set one carrying the whole measurement confession.

---

## 6. Repair plan (5 highest-impact changes, pass-2)

1. **Credibility — restate the 92% seam in one sentence.** Replace "measures the engine, not the AI's description" with: "92% is the end-to-end pipeline validation in the other telling of this work — GPT-4o's output included, scored against 100 labeled pairs; 85% is the add-on descriptor in this telling, self-assessed. Same project, two integrations, two numbers; I never blend them." Then rehearse it *with* the Q3 answer (ledger shows the same story there) so the loop cannot catch a contradiction.
2. **Credibility — fix the cascade math.** "13% band → ~7.5× ($1.50→$0.20); tightening to 4% with better signals → ~25× ($1.50→$0.06)" — the source's actual ladder. Design-target arithmetic must be airtight or it undercuts the design.
3. **Judgment — un-retrofit the asymmetry motive.** Present error asymmetry as the lens that *later* proved the human-in-the-loop design right (Finding 4 was a threshold-calibration audit), not as day-one reasoning. One sentence, and it doubles as a learning signal.
4. **Impact — narrow the one real gap with the cheapest honest artifact.** Before the interview, tally anything recoverable from the feedback marks (even "dozens of analyses, wrong ones clustered in two categories") or state that the artifact is gone. Do not upgrade the qualitative triage claim past "they told me."
5. **Learning — add the retrospective-tuning confession.** Finding 4's real content — "I tuned thresholds until false positives stopped annoying me; loosening traded recall for precision, which is backwards in QA" — is the strongest sourced learning in the whole BGSW corpus and is currently used only as design rationale. Telling it as a mistake *found later* closes gap #3's "instrumented, not verified" read with a fact, not a hedge.

---

## 7. Recommended structure (improved STAR, v3)

- **Situation:** Solo-built PCB inspection suite at Bosch. Four-signal comparison flagged *where* boards mismatched; a manufacturing engineer spent ~30 s (their own estimate) interpreting each flagged region, 5–20 per board. Last manual bottleneck.
- **Task:** Add an AI description — component type, mismatch class, confidence — <5 s, trustworthy enough for engineers, working in server and standalone builds (standalone may have no API access).
- **Action:** Evaluated GPT-4V/Claude 3/Gemini PV on real flagged regions → GPT-4o; rejected LLaVA on the 8 GB VRAM floor constraint. Engineering into preprocessing: dual crops, structured JSON; first prompt failed → schema + few-shot. Trust architecture: suggestion-not-verdict UI, per-analysis marks, opt-in user key (localStorage, never our servers) with graceful AI disable, security-team review of cloud transfer, ROI cap + caching + offline fallback.
- **Result (disclosed):** ~5 s model turnaround (3 s per-request; reconcile 2 s as the other telling); read-and-confirm replaced zoom-and-decide — "most of the 30 s, confirm never costed"; ~85% ballpark from logged marks, no held-out set (the admitted gap); 15% = image quality/size, stated to users; qualitative triage prioritization; suite-level adoption (15 engineers/2 sites/~20 h/wk) correctly *not* claimed for the feature.
- **Learning:** wrong assumption (SMD OCR); simpler-prompt-first; **the retro-find**: my threshold tuning optimized demo comfort and traded recall for precision — the asymmetry I now cite is what that audit taught me; would build the held-out set day one; at fleet scale, the cost-aware cascade (7.5×→25× ladder) as designed-not-built next step.

---

> **"What would still make me unconvinced as a Bar Raiser?"**
> The disclosure discipline is now genuinely strong — I believe everything the candidate says. What I'd still write in the debrief: *productivity impact is asserted, not evidenced* — every number behind "improved productivity" is an estimate, a machine-time figure, or a ballpark, and the one artifact that could have settled it (the feedback marks) exists but was never read. That's survivable at 4. What would take it back down: if the candidate, asked whether the 92% number counted the AI's answers — as their own other story says it did — insists "92% was just the engine." The moment a reconciliation sounds more airtight than the records underneath it, I stop auditing the metric and start auditing the teller.
