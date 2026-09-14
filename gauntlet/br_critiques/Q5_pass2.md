# Q5 — Bar Raiser Critique, Pass 2

Target: `gauntlet/answers_v2/Q5.md` (repaired "directly interacted with a stakeholder"). Critic run per `BR_CRITIC_SPEC.md`, same prompt as pass 1. Repairs verified against: `AMAZON_INTERVIEW_PREPARATION.md` (STORY 1 lines 45–119, STORY 4 lines 379–433, STORY 11 lines 1019–1091), `AMAZON_INTERVIEW_PREP.md` (Story 1, Story 2 — exclusion check), `LP_RUBRIC.md` (CO strengths lines 53–61), `deploy/SchematicvsEbom/bom_server.py`, `deploy/SchematicvsEbom/bom_verification.html`, `deploy/SchematicvsEbom/bom-verification.js`, `STORY_LEDGER.md`.

---

## 1. Verdict

- **Bar Raiser readiness: 4 / 5** (was 3 / 5 at pass 1)
- **Strongest LP:** Customer Obsession — two distinct, single-telling stakeholder interactions (variant-semantics correction; trust/auditability), each mapped to a verbatim rubric strength, with the over-reach signal ("identifies new ways of gathering feedback") correctly demoted to an observed outcome.
- **Biggest weakness (downgraded from pass 1's centerpiece contradiction):** the debug mechanism now matches the code — but the *engineer-facing usage* of it still rides on prose. The shipped `POST /debug` route (bom_server.py:503–591) requires a fresh PDF upload and comma-separated `targets` (defaulting to four hardcoded refs); there is **no UI integration for it anywhere** — the only "debug" hit in `bom_verification.html` is a console-log comment (line 562). STORY 1's own text says the engineers "were not software developers — they needed to upload files and get results" (line 77). So "gave them the ability to audit any decision themselves" and "engineers used the debug route to surface two edge cases" fuse a developer-facing JSON endpoint with usage attested for the now-excluded `?debug=true` page. Smaller residual: "give it a reference and it returns the raw evidence behind the decision" understates that the route re-extracts from the PDF independently of the run that made the decision — corroborating evidence, not the decision's own trace.

### Verification summary (what held up)
- **Tier (a) code-verified claims all check out.** `POST /debug` returns per-target `found_on_pages`, `instances` (text, color, `color_rgb` classification, bbox, page), `nearby_links` (distance + URI), `nearby_dnp_keywords` — docstring verbatim: "Useful for understanding why edge cases aren't triggering" (503–591). Dashboard cards Schematic Comps / BOM Entries / Matched / Issues Found sit above the results table (html:404–421, 423). `0.0.0.0:5001` bind at 617; `/health` 498; `/debug` 503. "The nearby hyperlinks and DNP keywords **the matcher weighed**" is supported: `analyze_component(refdes, instances, link_rects, dnp_labels, …)` at line 250 plus the startup banner ("Hyperlinks: Blue+Link = Active", "DNP Proximity").
- **Tier (b) prose citations all resolve at line level:** 67, 89, 93, 97, 99, 103; 1041, 1045, 1049–51, 1053, 1057, 1059, 1063, 1071, 1083, 1091; STORY 4 lines 401–403, 423–425. No misquotes. "My responsibility" for the debug work correctly follows line 1045's assigned framing — the prior "I didn't wait to be asked" is gone.
- **Tier (c) quarantine is accurate:** `?debug=true`, decision tree, "50+ columns", "learned to add ?debug=true", "reviews"/"component-type distribution" labels — all genuinely present only in STORY 11 prose (1049–51, 1071, 1091, 1053) and genuinely absent from the frontend; correctly dropped from the spoken answer and labeled "describe, never demo."
- **The variant-splitter honesty note is correct and important:** grep confirms no `||`/`/` BOM-side splitter in `bom_server.py`; the code's "variant" handling is PDF-side A/B suffix logic (lines 292–300), a *different* mechanism. The "do not offer 'I can show you' on this one" flag is right.
- **Fusion discipline intact:** `/api/debug` (15%→1%), `R1 (Rev A)/(Rev B)`, Good Board 30–60 min numbers, STORY 8 VLM flag — all still excluded, all confirmed present in their source tellings. Ledger Q5 remains consistent.

---

## 2. What works

1. **The pass-1 centerpiece fix is real.** The transparency beat is retold in exactly the form the repo can produce: per-reference evidence route + four-card stats dashboard, gated off the main view, on a LAN-bound Flask service. Nothing in the spoken answer now requires the missing `?debug=true` page to be true.
2. **Numbers attributed and split as prescribed.** Baseline = "their estimate, not a measurement I took"; speed = "<200 ms parse on 2000 components, report in seconds"; verification = 15-BOM regression suite; scope = "one team, one plant, one week of numbers," volunteered before being extracted. Every one of those traces to STORY 1 lines 93/97/99.
3. **The three embellishments are gone and the removals are logged.** "Re-verified by hand" → sourced "hesitant to rely"; "didn't wait to be asked" → dropped per line 1045; adoption → "reported being more willing to rely" per line 1059; "localhost" → "local network only, not the internet"; mismatches tense restored to source's "had missed." The provenance section shows each substitution — auditable repair, not silent editing.
4. **Judgment gaps are gap-flagged, not filled.** The either-matches-vs-review-flag trade-off is answered as "stated requirement + my reasoning + my record shows no formal comparison." The cost/provisioning question is answered as "I'd need to check rather than guess." This is what compliant repair looks like under the no-invention rule.
5. **The scale loop now closes honestly.** Server stays one plant-network box; the no-infrastructure problem "got solved differently, in the standalone file" — sourced to STORY 4 (401–403, 423–425), and the answer correctly keeps the debug capability out of the standalone build.

---

## 3. Biggest gaps (ranked)

1. **Usage-path fusion on the debug route.** Mechanism is code-verified; *engineer adoption of that mechanism* is not. No frontend control calls `/debug` (grep: zero hits in the shipped HTML/JS). The workflow described in the follow-up — engineer questions a mismatch, "the server's debug route answers," "they compare against their own BOM and layout file" — requires a manual POST with PDF re-upload and typed targets, for users STORY 1 itself labels non-developers. Either own it as "I ran the queries and walked them through the output" (a developer-mediated audit) or accept that "they could audit the decisions themselves" is stronger than the shipped build supports.
2. **"Raw evidence behind the decision" slightly overstates linkage.** `/debug` re-parses the uploaded PDF; it does not read the state of the `/verify` run that produced the flagged verdict. Corroborating evidence, not the decision's trace. A BR who asks "does it show what *that* run did, or what a fresh parse finds?" exposes the difference.
3. **Baseline measurement still thin by design.** Attribution fixed, but the count of boards/users behind "20–30 minutes" and the confirmation method for the three mismatches remain open gaps (honestly carried — still the first thing I'd press).
4. **Hardest part remains GAP.** Pass 1 gap #8 untouched (correctly listed in open gaps rather than invented), but the story still has no sourced difficulty beyond the bug fixes.
5. **Ambiguity in the demo caveat.** "I'd describe the former, not demo it" — antecedent unclear on first listen (the former = the `?debug=true` page, per provenance). A fumble here risks the candidate accidentally inviting a demo of the excluded page. Minor wording, outsized moment.

---

## 4. Credibility audit

| # | Claim (v2) | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | Engineers' baseline 20–30 min/board, "their estimate, not a measurement I took" | "How many boards? Whose estimate?" | STORY 1 line 99; attribution already correct | **Keep** (board count stays a carried gap) |
| 2 | Silent drop of `R1||R2`/`R1/R2`; engineer correction; built splitter matching either reference | "Show me the splitter" | Line 89 supports intent + build; repo has **no** `||` splitter (code variant logic is A/B suffixes, 292–300) | **Keep in narrative; keep the no-demo flag — do not offer "I can show you"** |
| 3 | Per-component debug route: "give it a reference and it returns… pages, spans with position/color classification, nearby hyperlinks and DNP keywords the matcher weighed" | "From where? A button in the report?" | Code: 503–591 (requires PDF upload + form `targets`, default hardcoded; no UI caller); matcher linkage via 250 + banner | **Keep — soften one step**: add "you post the layout PDF with the reference" so the lookup isn't implied to be one-click from the report |
| 4 | "The raw evidence behind the decision" | "Same run state, or fresh parse?" | Route re-extracts independently of `/verify` state | **Soften to "the raw evidence the matcher's rules work with"** |
| 5 | Stats dashboard: schematic comps, BOM entries, matched, issues, above every reconciliation | "Demo it" | html:404–421 code-verified; labels match provenance | **Keep — fully demoable** |
| 6 | Engineers "couldn't see why" / "hesitant to rely for critical decisions" | "How did you learn this?" | Line 1041 verbatim ground | **Keep** |
| 7 | Audit channel: week one, two naming edge cases, both fixed | "What were they?" | Line 1057; specifics unrecorded (provenance says prep or admit) | **Keep; specifics stay a gap** |
| 8 | Three real mismatches week one "that manual review had missed" | "Confirmed real how?" | Line 99, tense now correct; confirmation method gap at provenance line 90 | **Keep, with the stated gap** |
| 9 | Sub-200 ms parse of 2000-component BOM; 15-BOM regression suite after every change | — | Lines 93, 97 | **Keep** |
| 10 | Flask service, plant network, local only, data already theirs | "Who provisioned/signed off?" | 617 bind + line 1083; provisioning gap flagged at answer line 54 | **Keep wording; keep gap admission** |
| 11 | Separate route "so the main view stayed clean" / "technical users" | "Source of that reasoning?" | Line 1071 (query-param rationale adapted to route) | **Keep** |
| 12 | "Gave them the ability to audit any decision themselves" + follow-up walkthrough of engineers querying the route | "No UI exists — who actually ran these queries?" | Usage attested in prose (1057) for the excluded view; code endpoint is dev-shaped | **Soften: developer-mediated or scripted use, not engineer-self-serve** ← #1 remaining |
| 13 | "More willing to rely" (reported), one-team/one-plant/one-week scope | — | Line 1059; scope volunteered | **Keep** |
| 14 | LP signals (CO strengths, Earn Trust line 117, Ownership line 253) | — | Spot-checked against LP_RUBRIC 53–61; over-claiming signal removed | **Keep** |
| 15 | Either-matches trade-off defense ("manual queue the tool existed to clear") | "Did you compare options?" | Not in any source — but explicitly framed as own reasoning with "my record doesn't show a formal comparison" | **Keep as-is; compliant gap-framing, do not let it harden into a claimed decision process** |

---

## 5. Follow-ups (Bar Raiser probe test, v2)

1. **"What was the actual problem the stakeholder had?"** — **SAFE.** Manual baseline (attributed) + distrust of uninspectable verdicts, both sourced.
2. **"What did you personally do?"** — **SAFE.** Splitter, endpoint, dashboard, two fixes, all first-person, all sourced.
3. **"Why a debug endpoint + dashboard rather than pair-debugging or an exportable audit file?"** — **PARTIAL.** Line 1071 explains gating, not the choice of transparency mechanism over alternatives. Still no rejected-alternative for the *form* of the fix.
4. **"What alternatives did you reject on variant handling?"** — **PARTIAL** (was GAP). Honest stated-requirement answer plus self-flagged absence of a formal comparison — no longer answerable only by invention, but no longer a strong judgment answer either.
5. **"How did you measure success?"** — **PARTIAL.** Regression suite + parse time volunteered; the baseline itself remains engineer-reported with no sample count.
6. **"How reliable were the results — n = what?"** — **PARTIAL.** n=15 BOMs, one week, one team now volunteered; confirmation method for the three mismatches and the two naming cases' specifics still thin.
7. **"What went wrong?"** — **SAFE.** Own silently-dropped-variants bug, customer-detected.
8. **"What was the hardest part?"** — **GAP** (unchanged, carried honestly in the gaps list; nothing sourced to answer it).
9. **"Did anyone disagree with you?"** — **PARTIAL.** The engineer's correction remains the only recorded disagreement; no doubt about the transparency work's worth is on record.
10. **"What did it cost?"** — **PARTIAL** (was GAP). Explicit "check rather guess" on provisioning trail and time cost; defensible admission, not a convincing answer.
11. **"What happens at larger scale?"** — **SAFE** (was GAP). One plant server, stated; standalone single-file build for the no-infrastructure floor machines, sourced to STORY 4.
12. **"Walk me through an engineer questioning a mismatch end-to-end."** — **PARTIAL.** The walkthrough describes evidence the endpoint can produce, but the self-serve path has no UI; one sharp "how did they type the request?" question and the answer must become developer-mediated.

Score: **5 SAFE / 6 PARTIAL / 1 GAP** (pass 1: 4 / 4 / 4).

---

## 6. Repair plan (remaining highest-impact changes)

1. **Credibility — fix the usage path.** Retell the transparency beat as: dashboard = in the engineers' UI (true, demoable); debug endpoint = raw-evidence lookup over the layout PDF that *I* drove when they questioned a verdict (post the PDF + reference, read the span/link/DNP evidence back), with the two week-one edge cases surfacing through that loop. This keeps every code-verified fact and drops only the unsupported "they clicked and audited themselves." One sentence in core para 3–4 and one tweak in the walkthrough follow-up.
2. **Credibility — precision on evidence linkage.** Swap "raw evidence behind the decision" for "raw evidence the matching rules work with on that PDF" — one clause, closes the fresh-parse-vs-run-trace distinction before a deep technical BR opens it.
3. **Judgment — one concrete hardest-part memory, or a standing honest fallback.** Still the only pure GAP. If a real difficulty exists (IT constraints on the server, reproducing a naming edge case, the DNP×variant interaction from STORY 1 line 107 is *sourced* and adjacent — usable only if genuinely experienced), name it; otherwise script the fallback: "the trust gap was the hard part, and I under-invested in it early" — which the reflection already supports.
4. **Learning — de-fang the demo caveat.** Replace "I'd describe the former, not demo it" with an explicit referent: "the richer trace page is from my written summary, not the build I can show you." Ambiguity at the most dangerous moment of the story is a self-inflicted wound.
5. **Measurable impact — prep the two unrecorded specifics offline.** The two naming edge cases and the mismatch-confirmation method are the last places where "how did you know?" ends in a recorded gap; recovering either (from the fix commits or the boards themselves, if real memory exists) would move probes 6 and 7 from PARTIAL to SAFE. Do **not** fabricate them at the table.

---

## 7. Recommended structure (v2.1 STAR outline)

- **S (45s):** Manufacturing engineers = the customers of the BOM reconciliation tool I built (SAP BOM vs Altium layout PDF). Their reported baseline: 20–30 min per board, entry by entry — their estimate, and I say so. After v1: a class of legitimate variant entries silently dropped, and — bigger — they were hesitant to rely on black-box verdicts for critical decisions.
- **T (20s):** Fix matching correctness; and make the results auditable — my stated responsibility, and I treated the trust problem as in-scope for me, not theirs to get over.
- **A (2–2.5 min):**
  1. *Correction:* engineer explains `R1||R2`/`R1/R2` = one position, either part; I built a splitter normalizing both separators. Design came from the customer; my record shows no formal review-flag comparison — said plainly.
  2. *Transparency (two layers, correctly separated):* the run-level stats dashboard **in their UI** (Schematic Comps / BOM Entries / Matched / Issues Found) so they saw the shape of a run first; and a per-component debug endpoint on the server — post the layout PDF and reference(s), get back the raw evidence the rules work with (pages, span text/position/color, nearby hyperlinks, DNP keywords). I ran it with/for them on questioned verdicts; kept it off the main view so routine verification stayed clean. Flask on the plant LAN only.
  3. *Loop:* week one through that channel: two naming edge cases, both fixed; every change verified against the 15-BOM regression suite; <200 ms parse on 2000 components.
- **R (40s):** Three real mismatches caught week one that manual review had already missed; report in seconds vs their 20–30 min baseline; they reported being more willing to rely on results for production verification. Honest scope volunteered: one team, one plant, one week.
- **L (30s):** Ship transparency on day one, not after the skepticism; collect floor BOMs before writing the parser. One lesson: real customer artifacts in front of me before design.
- **Held-back line (never spoken as demo-able):** the `?debug=true` trace page / decision tree / 50+ columns — written-story only, and the candidate says so if it comes up.

---

> **"What would still make me unconvinced as a Bar Raiser?"**
> The story is now internally honest and code-consistent — what I'd still poke is *who actually touched the audit tool*. If the engineers never had a button, then the trust fix was really "I made myself inspectable to them," which is a good but smaller story, and I'd want the candidate to say that first rather than have me extract it. Behind that: one week, one team, engineer-reported baseline, no count of boards, two edge cases whose specifics the candidate can't name — the impact case is credible as *a beginning*, not as a result. And if I ask "what was hardest?" and get silence twice, I start wondering whether the two easy interactions are the whole of a shallow stakeholder relationship: where was the prioritization, the ongoing cadence, the pushback? That, not any single number, is what keeps this at 4.
