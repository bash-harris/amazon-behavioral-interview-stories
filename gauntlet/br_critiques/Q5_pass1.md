# Q5 — Bar Raiser Critique, Pass 1

Target: `gauntlet/answers/Q5.md` ("tell me about a time you directly interacted with a stakeholder")
Critic run per `BR_CRITIC_SPEC.md`. Claims verified against: `AMAZON_INTERVIEW_PREPARATION.md` (STORY 1 lines 45–119, STORY 11 lines 1019–1091, STORY 4 line 379+, STORY 8 line 755+), `AMAZON_INTERVIEW_PREP.md` (Story 1 lines 35–67, Story 2 lines 68–105), `LP_RUBRIC.md`, `deploy/SchematicvsEbom/bom_server.py`, `deploy/SchematicvsEbom/bom_verification.html`, `CODEBASE_DOCUMENTATION.md`, `STORY_LEDGER.md`.

---

## 1. Verdict

- **Bar Raiser readiness: 3 / 5**
- **Strongest LP:** Customer Obsession — two distinct, source-grounded direct stakeholder interactions, each producing a shipped change. The primary LP fit for the question is genuine, not nominal.
- **Biggest weakness:** The story's centerpiece (the `?debug=true` transparency view) is grounded **only** in story-bank prose. The code file the answer itself cites as evidence (`bom_server.py`, line 617) documents a *different mechanism*: a `POST /debug` JSON diagnostic taking a PDF + hardcoded-style target list and returning raw span data (`found_on_pages`, `instances`, `nearby_links`, `nearby_dnp_keywords`) — not an engineer-facing URL-parameter view with a per-component decision tree. No `?debug=true` handler exists anywhere in the checked frontend code. A Bar Raiser who asks "walk me through how the engineer opens it and what renders" hits a narrative the repo cannot show.

### Verification summary (what held up)
- All 12 provenance line references to STORY 1 / STORY 11 resolve correctly to the cited facts (67, 89, 99, 103; 1041, 1049–51, 1053, 1057, 1059, 1063, 1071, 1083, 1091). No misquotes at line level.
- All "strong signals covered" phrasings exist verbatim in `LP_RUBRIC.md` (Customer Obsession strengths lines 53–61; Earn Trust line 117; Ownership line 253).
- The fusion-avoidance exclusions are real and correctly excluded: `AMAZON_INTERVIEW_PREP.md` Story 1 is the Good Board tool (30–60 min → under 2 min, "sat in on three screen-sharing sessions", highlighting-not-score); Story 2 carries a competing variant telling (`R1 (Rev A)`/`R1 (Rev B)`) and a third debug-endpoint version (`/api/debug`, 15%→1% false negatives); STORY 8 carries the VLM correct/incorrect flag. Q5 uses none of them. Ledger Q5 status PASS is consistent.
- Flask service, `/verify`, `/debug`, `/health`, `app.run(host='0.0.0.0', port=5001, debug=True)` at line 617, and a "STATS DASHBOARD" in `bom_verification.html` (fetches `http://localhost:5001/verify`) all exist in code.

---

## 2. What works

1. **One stakeholder group, two real interactions, zero fusion.** A correction (`R1||R2` semantics → splitter rewrite) and a trust problem (opacity → debug view/dashboard). Both facts are sourced to a single telling each, and the answer explicitly quarantines the conflicting Good Board / `/api/debug` / Rev A-B tellings. Rare discipline; survives "which engineer, what exactly did he say" probing.
2. **Own-goal confession.** The first interaction is the candidate's own bug dropped silently, fixed on customer input. Credible humility, maps to "takes actions guided by customer input" without spin.
3. **"I" is clean.** Parser rewrite, view addition, dashboard addition, two fixes — all first-person. The "we" problem is absent.
4. **Learning is specific and sourced.** Both reflection items (debug from day one; collect floor BOMs first) trace to STORY 11 line 1063 and STORY 1 line 103, and are unified under one lesson rather than listed generically.
5. **Deployment honesty.** The deep follow-up explicitly refuses to let the debug trace ride into the standalone offline build — correct per STORY 4 (server vs standalone were different deployments).

---

## 3. Biggest gaps (ranked)

1. **Mechanism–code contradiction on the debug view.** `?debug=true` GET view, "parsed reference after each preprocessing step", "per-component decision tree", "50+ columns", "engineers learned to add ?debug=true to the URL" — none of this is implementable from the repo. What demonstrably exists: `POST /debug` raw-PDF JSON diagnostic and a dashboard fed by `/verify` stats (`matched`, `issues`, `reviews`, `colorStats`). The answer's own provenance cites `bom_server.py` as support while the file undercuts the claimed form. Highest-priority fix.
2. **Three unsupported embellishments inside the sourced frame.**
   - "they re-verified by hand, which defeated the purpose" — STORY 11 line 1041 says only "hesitant to rely on the tool for critical decisions." The re-verification loop is invented color.
   - "I didn't wait to be asked for a fix" — STORY 11's Task (line 1045) frames the debug mode as "my responsibility," i.e. assigned. The initiative claim contradicts its own source.
   - "they were willing to rely on the results for production verification" / "engineers adopted the tool for production verification" — source says "**more** willing to rely" (line 1059). Adoption as a done fact is stronger than evidence.
3. **Numbers with no measurement story.** "20–30 minutes per board" — reported by whom, over how many boards? "seconds" — end-to-end or parse only (STORY 1 line 97 separately says <200 ms for 2000 components — a *stronger, sourced* number Q5 omits)? "three real mismatches … that manual review had missed" — how were they confirmed real, and confirmed previously missed? Source line 99 says "had been missed" (already happened); Q5 quietly downgrades to "would have missed" without noticing. Also: dashboard claims "component-type distribution" (source wording) while the code's aggregate is `colorStats` (Active/DNP color classes) — an engineer would call colors "population state," not component type.
4. **Judgment/thin trade-offs.** Beyond the URL-param-vs-toggle answer (grounded, line 1071), no rejected alternatives: not for the variant-matching design (why "either matches" vs "review-flag"? what about `R1||R2` with a genuine single populated part?), not for the transparency solution (why a trace view vs. pair-debugging sessions vs. exportable audit log?), and no cost: time spent building it, what was deferred, who sanctioned a long-running LAN server under plant IT rules.
5. **Scale and durability never addressed.** One tool, one plant, one week of "results." STORY 1's 15-BOM regression suite (line 93) is free ammunition Q5 doesn't use. "What happens when two more lines adopt it / the server host PC reboots / you leave?" — no answer exists in the story.

---

## 4. Credibility audit

| # | Claim | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | Manual cross-reference took 20–30 min/board | "Who timed that? Sample size?" | Engineer-reported baseline; say it's their estimate, not a measurement | **Keep, with attribution** (STORY 1 line 99 supports the number only) |
| 2 | Reconciliation dropped to "seconds" | "Seconds of what — upload, parse, report?" | Split: parse <200 ms for 2000-comp BOM (line 97); report generation seconds (line 99) | **Soften/split** |
| 3 | Parser caught 3 real mismatches week one "that manual review had missed" | "How do you know they were real? How do you know humans missed them?" | Confirmation on physical board; the prior manual review of same boards | **Keep; soften tense to source's "had been missed"; add confirmation method or mark gap** |
| 4 | `R1||R2` / `R1/R2` = variant semantics, engineer-supplied; splitter rewritten | "Show the code"; "where did you find this in SAP exports?" | STORY 1 line 89 supports intent; **code grep of bom_server.py/bom-verification.js shows no `||` variant splitter** | **Keep in narrative; GAP on code demo — do not offer "I can show you" on the splitter** |
| 5 | "I rewrote the variant splitter" | Source says "built a variant splitter" (line 89) | Minor drift; before it, refs were "silently dropped" so "rewrote the handling" is defensible | **Soften to "built a splitter to replace the drop behavior"** |
| 6 | Engineers re-verified flagged mismatches by hand, "defeating the purpose" | "How did you observe that?" | Not in any source | **Remove** (replace with sourced "hesitant to rely for critical decisions") |
| 7 | "I didn't wait to be asked" | "So who assigned it? STORY says it was your responsibility" | Contradicts STORY 11 line 1045 | **Remove or make true** |
| 8 | `?debug=true` view; decision tree; 50+ columns; engineers learned to append the URL param | "Walk me through the request; what route serves it?"; repo has only `POST /debug` + console-log gates | Story-bank prose only (lines 1049–51, 1071, 1091); code contradicts form | **Soften to what code supports** (raw per-component trace endpoint + `/verify` stats dashboard) **or** state up front the UI-build lived in a local iteration not in the repo snapshot — never claim the demo |
| 9 | Dashboard shows total/matches/mismatches/reviews/component-type distribution | "Component type? I see colors" | `bom_verification.html` dashboard + `/verify` stats exist (code-verified); labels differ ("issues" not "mismatches"; colorStats = Active/DNP classes) | **Keep; relabel to code truth** |
| 10 | Two naming edge cases surfaced via the view in week one, fixed | "What were they? What did the fix touch?" | STORY 11 line 1057 supports; specifics unrecorded | **Keep; prep concrete examples or admit you'd need to look them up** |
| 11 | "Ran for them a small Flask service on the plant network" | "Who provisioned it? IT security? On whose machine?" | STORY 4 shows server hosting was a known burden (drove standalone); no source for who operated it | **PARTIAL — mark gap; have the real hosting answer** |
| 12 | "reachable on localhost, not the internet" | Code binds `0.0.0.0` = whole LAN | Source line 1083 says "localhost or local network" | **Soften wording to "local network, not routable/internet"** |
| 13 | Debug view "became the feedback channel"; CO signal "identifies new ways of gathering feedback" | "Did you design it as a feedback channel, or did they just use it that way?" | Source supports use, not design intent | **Soften to "it turned into"; drop that signal or label it as observed outcome** |
| 14 | "engineers adopted the tool for production verification" | "Permanent adoption? Still used after you left?" | Source: "more willing to rely" (line 1059) | **Soften to "more willing to rely"** |
| 15 | LP mapping (all 11 signal bullets) | — | All phrasings verified verbatim against LP_RUBRIC lines 53–61, 117, 253 | **Keep** |

---

## 5. Follow-ups (Bar Raiser probe test)

1. **"What was the actual problem the stakeholder had?"** — **SAFE.** 20–30 min manual reconciliation (line 99) + distrust of black-box verdicts (line 1041), both sourced.
2. **"What did you personally do?"** — **SAFE.** Splitter rewrite and debug/dashboard build are first-person and sourced; "we" contamination absent.
3. **"Why a trace/audit view rather than, say, sitting with engineers on flagged cases, or an exportable report?"** — **PARTIAL.** Line 1087 gives the design principle ("answer 'why' completely, else they must ask me"); no genuinely rejected alternative named. Prep the pair-debugging rejection with a real reason.
4. **"What alternatives did you reject on the variant handling itself?"** — **GAP.** "Match either" vs. "flag for review" trade-off never discussed in any source. And note the code reality: no `||` splitter is visible in the repo — do not volunteer "I can show you."
5. **"How did you measure success?"** — **PARTIAL.** Numbers exist; method doesn't. Add regression suite (line 93) and the <200 ms parse (line 97) as verification anchors — both real, both unused.
6. **"How reliable were the results — n=what?"** — **PARTIAL.** 15 BOMs, one week, one plant, 3 mismatches + 2 edge cases. Small n must be volunteered, not extracted.
7. **"What went wrong?"** — **SAFE.** The silently-dropped variants bug is your own error, customer-detected; clean.
8. **"What was the hardest part?"** — **GAP.** Nothing in the story names a difficulty (convincing anyone to fund the view, reverse-engineering SAP export quirks, IT constraints). Currently unanswerable without invention.
9. **"Did anyone disagree with you?"** — **PARTIAL.** The engineer's correction is one; the debug view met no resistance on record. One is enough for this question, but expect "did anyone doubt the view was worth the effort?"
10. **"What did it cost?"** — **GAP.** No time/effort figures for the view or the LAN server, no deferred work, no IT/security sign-off story (only the localhost-scope answer at line 1083).
11. **"What happens at larger scale — more lines, more plants?"** — **GAP.** Single-server, single-team; nothing sourced about scale-out. Honest answer is "it didn't — that's what the standalone build was for" (STORY 4), which Q5 must connect explicitly.
12. **"What would you do differently?"** — **SAFE.** Two sourced lessons unified into one principle (line 1063 + line 103).

Score: 4 SAFE / 4 PARTIAL / 4 GAP.

---

## 6. Repair plan (5 highest-impact, in priority order)

1. **Credibility — reconcile the debug mechanism with the code.** Retell the second interaction as what the repo can actually show: the server exposed a per-component debug endpoint (raw BOM entry data, matched PDF positions, nearby hyperlink and DNP evidence) plus a stats dashboard over every reconciliation run (totals, matched, flagged, review, color/population breakdown). Either drop `?debug=true` / decision-tree / 50+ columns from the spoken story or explicitly frame them as the story-bank's earlier/different build — never offer them as a demo. Remove "reachable on localhost" (code binds LAN-wide; say "local network only").
2. **Credibility — excise the three embellishments.** Delete "re-verified by hand, defeating the purpose" → use "hesitant to rely on it for critical decisions." Delete "I didn't wait to be asked" (contradicts its own source's Task framing). Downgrade "adopted for production verification" → "more willing to rely on the results for production verification." Restore "had been missed" tense on the three mismatches.
3. **Measurable impact — attribute and split the numbers.** Baseline: "the engineers reported 20–30 minutes per board." Speed: "sub-200 ms parse for a 2000-component BOM; a full report in seconds." Verification: "15-BOM regression suite covering every known edge case." Realism: volunteer that this was one team, one week, three mismatches. All four facts exist in STORY 1 — move them into the answer body.
4. **Judgment — add one genuine trade-off per interaction.** Variant fix: why treat both references as valid matches rather than flag for review (a false "missing" on a variant board costs more production time than a caught review — keep it honest; if the real reason differs, use the real one, else mark gap). Transparency: keep the URL-gate-vs-UI-toggle reasoning (line 1071, sourced) and add what the debug work cost / displaced — gap-flagged unless a real figure exists.
5. **Learning/stake continuity — fix the feedback-channel framing and close the scale loop.** Say the audit capability *became* an informal test channel (engineers surfaced two naming edge cases), and drop or relabel the "identifies new ways of gathering feedback" signal to match. Add one sentence connecting the LAN-server constraint to why the standalone single-file build existed (STORY 4) — it converts the "what at scale" GAP into an honest boundary: "it stayed one plant server; the no-infrastructure problem got solved differently, in the standalone build."

Rule compliance for the builder: every substitution above traces to a verified source line or is explicitly gap-marked; nothing may be invented to fill #4's cost figure, #8's "hardest part," or #10's trade-off if the candidate has no real memory of them.

---

## 7. Recommended structure (improved STAR outline)

- **S (45s):** Manufacturing engineers were the customers of the BOM reconciliation tool I built (SAP-exported BOM vs Altium layout PDF). Baseline they reported: 20–30 min manual cross-reference per board. After v1 shipped, two problems: a class of legitimate entries was being dropped, and — bigger — they didn't trust a black-box verdict: when a mismatch fired they couldn't see why, and were hesitant to rely on it for critical decisions.
- **T (20s):** My job: fix matching correctness, and — my own call on scope — fix the trust problem, since a distrusted correct tool still gets bypassed.
- **A (2–2.5 min, three beats, each "what they said → what I changed"):**
  1. *Correction:* engineer explains `R1||R2`/`R1/R2` = variant at one position; I'd been silently dropping them; I built a splitter normalizing both separators so either reference matches. Trade-off: either-matches vs review-flag, [gap if no real reason].
  2. *Transparency:* per-component debug endpoint — raw entry text, parsed reference, matched PDF position, nearby link/DNP evidence — plus a run-level stats dashboard (totals, matched, flagged, review, population-state breakdown) so they could see the shape before drilling in. Gated off the main UI (URL/endpoint, not clutter) [reasons sourced line 1071]. Ran as a Flask service on the plant LAN only.
  3. *Loop:* week one through the view: two naming edge cases, both fixed; verified against my 15-BOM regression suite; parse <200 ms on 2000 components.
- **R (40s):** Engineers reported "more willing to rely" for production verification; three real mismatches caught week one that manual review had already missed; reconciliation in seconds vs their 20–30 min baseline. Honest scope: one team, one plant, one week of numbers.
- **L (30s):** Transparency features are not afterthoughts — I'd ship the trace view on day one; and floor BOMs before parser code. One lesson: get real customer artifacts in front of me before designing, not after.

---

> **"What would still make me unconvinced as a Bar Raiser?"**
> I'd ask the candidate to open the tool and walk me through one mismatch — and I'm fairly sure what's in the repo wouldn't match the story as told, which after that moment colors every other number in the answer. I'd also press on whether two conversations and one week of use constitute "stakeholder interaction" or just responsive bug-fixing: where was the ongoing relationship, the prioritization of their requests against a roadmap, the pushback? And the entire impact case rests on engineer-reported baselines with no count of boards or users — if the candidate can't say roughly how many boards a week this touched, I'd treat "20–30 min → seconds" as a demo claim, not a production result.
