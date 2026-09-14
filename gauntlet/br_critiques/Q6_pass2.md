# Q6 — Bar Raiser Critique, Pass 2
**Target:** `answers_v2/Q6.md` (repaired) — "influence a peer who had a differing opinion about a shared goal"
**Pass 1 score:** 3/5. **Sources re-checked for pass 2:** `AMAZON_INTERVIEW_PREPARATION.md` (lines 4, 71–99, 941–973, 1041–1063, 1069–1091, 1462–1471), `AMAZON_INTERVIEW_PREP.md` (lines 308–328, 383–387, 528–538), `LP_RUBRIC.md` (§8, lines 143–151), `STORY_LEDGER.md` (Q6, Q10), `answers/Q6.md` (original), `answers/Q5.md`.

**Repair verification result:** all five pass-1 repair items are genuinely applied, and all citations re-checked line-by-line are accurate:
- ✅ Slip 1 fixed: "re-verified by hand" is gone from the core; para 2 now uses L1041's actual wording ("hesitant to rely on it for critical decisions"), and the removal is documented in provenance with the adjacent-story citations (PREP.md L387, PREPARATION L973 — both verified verbatim).
- ✅ Slip 2 fixed: comparative restored — core says "**more willing** to rely," matching L1059 exactly.
- ✅ Mapping owned: header + strong-signals quote rubric §8 strength 1 literally (verified verbatim at LP_RUBRIC.md line 148), label the disagree half an OPEN GAP, and name Earn Trust as the strongest-fitting LP. The rebrand line ("knowing which disagreement isn't worth holding") is deleted. The meta-claim that the original paraphrased "peers and supervisors" to "others" is itself accurate (checked original line 21).
- ✅ Trade-offs mined: query-param-vs-toggle (L1071) and localhost exposure (L1083) now in core and follow-ups — both verified in source.
- ✅ Results bounded: named non-claim for headcount/verification-time (the 20–30 min figure is at L99, STORY 1, and Q5 carries it — verified); scale probe answered with "one tool, one team, one week," no invented larger-scale win.
- ✅ The universal negative ("no peer/supervisor disagreement documented anywhere in the two story banks") independently checked: PREP.md's own coverage table says Have Backbone has "No primary story — Missing entirely" (L534); the browser-based-deployment counter-advocacy is an explicitly hypothetical "Recommended Addition" example (L537); STORY 10's "push back on a naive approach" is self-directed with no counterpart; the only "disagreement" quotes are me-vs-me label relabeling (L907). The gap claim holds.
- ⚠️ Three minor new nits — see §3 and §4 (rows 13–15).

---

## 1. Verdict

- **Bar Raiser readiness: 4 / 5**
- **Strongest LP (as actually demonstrated):** Earn Trust — and the answer now says so itself, up front, which is the right move. Mistake conceded (L89), domain intent credited, total transparency shipped (L1049–1053), comparative results kept honest (L1059).
- **Biggest weakness (residual, structural):** the claimed primary LP's disagree half still has no event to point at. This is now *disclosed*, not hidden — but disclosure caps the score; it does not close the gap. A BR scoring Have Backbone literally still hears: conceded once to a customer, shipped a feature once, nobody said no to you.

**Why improved from 3 to 4:** pass 1's three softest points (two attribution slips, silent paraphrase of the rubric) are fixed and the fixes are themselves sourced; the missing-trade-offs and unbounded-scale flags are mined and bounded from in-source material; nothing was invented — the two named corrections quote the source's actual wording. What separates this from a 5 is not writing quality; it is that the underlying event never contained the behavior the prompt asks for.

## 2. What works

1. **The credibility core is now bulletproof.** "more willing" (L1059 verbatim), "hesitant to rely on it for critical decisions" (L1041 verbatim), two naming edge cases week one (L1057, corroborated "twice in the first week," L1079). Aggressive quoting questions all land on source text.
2. **The gap is stated in the rubric's own words, then quarantined.** Quoting "Disagrees with *peers and supervisors*" literally, naming the counterpart mismatch, and refusing to borrow the hypothetical lead (L1468–1471) or blend Q10 — self-flagged weakness reads stronger than any widened paraphrase, and the provenance shows the alternatives were considered and rejected on evidence grounds.
3. **Judgment section materially upgraded.** Two real delivery/security decisions (query-param-over-toggle, L1071; local-network exposure rationale, L1083) convert "I shipped a feature" into "I made calls." The "Accuracy wasn't the complaint — verifiability was" reframe (L1041) is now paired with those trade-offs, which was pass 1's missing middle.
4. **Honest bounding everywhere scale pressure appears.** Named non-claim on headcount/time (with the figures and their owning story disclosed); "one team, one week" caveat on adoption; "no development-time figure — so I won't invent one"; the larger-scale probe answered with a mechanism, not a claim.
5. **Register stayed natural.** The concession language ("I won't dress it as one," "nobody argued *against* the debug view") sounds spoken, not legal — the framework honesty didn't turn the story into a disclaimer.

## 3. Biggest gaps (ranked)

1. **Structural (unchanged, unclosable in writing):** no documented instance of tenacious, resisted advocacy against a peer or supervisor. The answer now labels this OPEN GAP; a Have Backbone-scored BR still docks for the substance. Only a new real event (or leading with Q10's engineering-lead construction, which has its own hypothetical problem per pass 1) fixes this.
2. **NEW (minor): "localhost-only" over-tightens the source.** Core says "localhost-only exposure"; L1083 says "only accessible on localhost **or the local network**." The answer's own follow-up (line 40) and provenance (line 62) both correctly say localhost/local-network. An under-claim, not an overclaim of achievement — but it's an internal inconsistency and a factual misstatement a Dive Deep BR could catch ("is it reachable from the line's network?").
3. **NEW (minor): "The only internal person in the record is an engineering lead" is too broad.** PREP.md L320 records the lead sharing the prototype with "the team," and the team identifying three critical issues within an hour — internal feedback that exists outside Q6's declared fact set. Defensible if "record" means Q6's sourcing, but the sentence should scope itself ("in this story's record") or it invites the prototype-review team as a gotcha.
4. **NEW (minor, soft): "rather than letting distrust stall the tool or lowering the bar"** (strong-signals, L23) is an unrecorded counterfactual — nothing in the record shows the tool stalling or the bar being tempting to lower. It's mapping commentary, not a claim of fact, but it's the one sentence where the repaired voice is slightly asserting past events that the sourcing doesn't contain.
5. **Legacy (acknowledged, bounded): results remain anecdote-only by construction.** Two edge cases and a comparative trust shift are all STORY 11's Result section contains. The bounding is now honest, which neutralizes the *credibility* risk but not the *measurable-impact* scoring weakness — a results-focused BR still has no denominator.

## 4. Credibility audit

| # | Claim (repaired) | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | Solo build; no peer on the other side | Any other engineer? | L4 "built entirely solo"; PREP.md L320 lead only received demo | **Keep** |
| 2 | "no documented instance of disagreeing with peers and supervisors… anywhere in the two story banks" | Did you check the pin-count story? The deployment example? | L534 ("Have Backbone: No primary story — Missing entirely"), L537 explicitly hypothetical, STORY 10 counterpart-free, L907 me-vs-me | **Keep** — independently re-verified, holds |
| 3 | Variant concession: I treated `R1\|\|R2` as invalid, silently dropped, "each drop breaking the tool in production," rewrote splitter | Was it the tool or the parser that broke? | L73 "each one breaking the parser"; L89 verbatim otherwise | **Keep** (say "parser" to match L73 — pedant nit) |
| 4 | Engineers "hesitant to rely on it for critical decisions" | Verbatim? | L1041 exact | **Keep** (was Soften in pass 1 — done) |
| 5 | Debug view contents (raw text, per-step parse, matched entry, result, rule, decision tree, dashboard) | Exists in code? | L1049–1053; Authenticity Check L1494 | **Keep** |
| 6 | Query param over UI toggle — technical users, no production clutter | A real decision or post-hoc? | L1071 verbatim rationale | **Keep** |
| 7 | "**localhost-only** exposure" | Localhost *only*? Or local network? | L1083 says "localhost **or the local network**"; answer's own L40/L62 agree with source | **Soften** to "localhost/local-network only" (matches its own follow-up) |
| 8 | Two naming edge cases found by engineers in week one, both fixed | Small n? Self-reported? | L1057 + L1079 corroboration | **Keep**, with the answer's own n-caveat (line 43) retained |
| 9 | "**more willing** to rely… for production verification" | All of them? Baseline? | L1059 comparative intact | **Keep** (was Soften in pass 1 — done) |
| 10 | "No headcount or verification-time number — those live in my stakeholder story, kept unblended" | Why not give the number? | L99 figures held for Q5 (verified in `answers/Q5.md`); provenance names the split | **Keep** — named non-claim is the strength |
| 11 | "Pushed auditability… rather than letting distrust stall the tool or lowering the bar" | Did distrust stall anything? Did you lower a bar? | No record of either counterfactual | **Soften** to "instead of letting distrust stall adoption" as intent, not past event |
| 12 | "One tool, one team, one week; no larger-scale win claimed" | Generalizable at all? | Honest bounding; mechanism sentence is inference, labeled as transferable | **Keep** |
| 13 | "The only internal person in the record is an engineering lead who received a demo" | What about the team that reviewed the prototype (PREP.md L320)? | Scoped correctly only against Q6's declared fact set | **Soften** — add "in this story's record" |
| 14 | Q10 kept separate, not blended | Are these the same prompt twice? | Ledger Q6/Q10 both PASS, different constructions verified | **Keep** — the deliberate split is auditable |
| 15 | Rubric quotes (§8 strengths 1, 2, 4; paraphrases in Earn Trust mapping) | Verbatim? | LP_RUBRIC.md lines 148, 149, 151 — all match; "others" paraphrase correctly attributed to the *original*, not this draft | **Keep** |

## 5. Follow-ups (10–12 likely Bar Raiser probes)

1. **What was the actual problem — distrust, or wrong output?** — **SAFE.** L1041 + the verifiability-not-accuracy follow-up.
2. **What did you personally do?** — **SAFE.** Solo (L4); splitter rewrite (L89); debug view + dashboard (L1049–1053); no "we" anywhere.
3. **Why the debug view — what else could have worked?** — **PARTIAL.** Delivery-form trade-offs now mined (L1071, L1083), but no considered-and-rejected *influence strategies* (training, confidence scores, override UI) exist in the sourcing.
4. **What alternatives did you reject?** — **PARTIAL** (was GAP). The two in-source micro-trade-offs are now answered; strategy-level alternatives remain undocumented.
5. **How did you measure success?** — **PARTIAL.** Behavioral proxy (2 self-found edge cases, increased reliance) with an explicit "no denominator here" bounding; still no baseline or frequency metric — by construction.
6. **How reliable are the results — how many engineers, how long tracked?** — **PARTIAL** (was PARTIAL→GAP). Now answered with "one team, one week" plus the named non-claim; pressure survives but the answer stands on the recorded facts.
7. **What went wrong?** — **SAFE.** Silent drops breaking production (L73); transparency as afterthought (L1063).
8. **What was the hardest part?** — **PARTIAL.** Publicly conceding to a customer is implied; the honest "the concession wasn't hard, I adopted it immediately" framing pre-empts the gotcha but offers no interpersonal cost — because none is recorded.
9. **Did anyone disagree with you?** — **PARTIAL→SAFE-as-disclosed.** The answer names the only documented disagreement (they were right, I committed), states nobody opposed the debug view, and flags the resulting OPEN GAP in rubric language. It can no longer be *surprised* by this question — but it still cannot answer it with a real backbone event.
10. **What were the trade-offs/costs?** — **PARTIAL** (was GAP). Delivery/security decisions in; no dev-time figure, and the answer says so rather than inventing one (L46).
11. **What happens at larger scale?** — **PARTIAL** (was GAP). Bounded + mechanism-only; no invented scale win.
12. **Why is this Have Backbone and not responsive customer support?** — **PARTIAL** (was PARTIAL, now honest). The answer's own reply is "it largely *is* Earn Trust + the commit half, and here's the one backbone-adjacent piece (customer-interest framing) — the disagree half is a documented no." That survives questioning, but a strict BR still won't score strength 1.

Scorecard shift pass 1 → pass 2: GAPs at #4, #10, #11 eliminated via in-source mining and named bounds; #6, #9, #12 hardened from exposed to disclosed. Zero new SAFE→GAP regressions.

## 6. Repair plan (5 highest-impact changes, pass 2)

1. **Fix the "localhost-only" over-tightening.** Core line 13 → "localhost/local-network only" to match L1083 and the answer's own follow-up. One word; removes the only factual misstatement in the repaired draft.
2. **Scope the "only internal person" claim.** Line 31 → "the only internal person *in this story's record* is an engineering lead who received a demo." Pre-empts the prototype-review-team gotcha (PREP.md L320).
3. **De-counterfactual the backbone mapping.** Line 23 → recast "rather than letting distrust stall the tool or lowering the bar" as the forward intent it is ("so distrust wouldn't stall adoption") rather than an event that didn't happen.
4. **Match the source's word: "parser," not "tool," for the production breakage.** Line 11 → "each drop breaking the parser in production" (L73). Pedantic, but this story's whole brand is verbatim fidelity.
5. **Optional delivery note for the table:** add one spoken-word sentence to the opening ("If you're scoring Have Backbone literally, ask me the same question again — I have a second construction with a lead on the other side, and I'll tell you straight which parts are documented") only if the interviewer is explicitly probing backbone; the written answer should NOT import Q10. Current split is correct for the record; this is delivery-time judgment.

## 7. Recommended structure (STAR outline, as-built — largely satisfied)

The repaired draft already matches the pass-1 outline; what remains is the four wording fixes above:

- **S (~60s):** Solo-built suite (L4); shared goal with manufacturing engineers; counterpart = customers, not peers — flagged in the first 15 seconds. ✅
- **T (~30s):** Two documented divergences: a design call I lost, a trust verdict I had to move. ✅
- **A (~90s):** Commit half — splitter rewrite (L89). Transparency move — debug view + dashboard (L1049–1053). Judgment — query-param delivery (L1071), network-scoped exposure (L1083 — wording fix #1). ✅
- **R (~45s):** Two engineer-found edge cases, week one (L1057); "more willing" comparative intact (L1059); named non-claims on scale figures. ✅
- **L (~45s):** Concession as learning; transparency-in-v1 (L1063); scale bounded to mechanism. ✅
- **Mapping note:** Earn Trust leads; backbone = commit half + customer-interest, disagree half = stated OPEN GAP in rubric's literal words. ✅

---

> **"What would still make me unconvinced as a Bar Raiser?"**
> The repaired answer has converted every *stated* claim into source text — what it cannot convert is the absence at its center. The honest ceiling pass 1 set for this story was 3–4, and the repair has taken it to exactly 4: every remaining point off 5 is one thing, and it is not fixable by drafting. There is no meeting in the record where a peer or supervisor said "no" and the candidate, with data, did not fold. A Have Backbone evaluator can still close with: *"You've told me precisely which backbone behavior you don't have an example of. That's the right answer to my question — and it's still a no."* The only real fixes are a new event in actual work, or leading with Earn Trust as the scored LP (which this draft now recommends doing itself). Everything else — the localhost wording, the "only internal person" scoping, the stall/lower-the-bar counterfactual — is polish on an already-credible skeleton.
