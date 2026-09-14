# Q7 Pass 2 — Bar Raiser Critique (repaired answer, v2)

**Story under review:** `gauntlet/answers_v2/Q7.md` — "tell me about a time you failed" (BGSW standalone HTML, IE11/WebAssembly compatibility failure)
**Verified against:** `AMAZON_INTERVIEW_PREPARATION.md` STORY 4 (lines 401, 407, 411, 413, 415, 423, 425, 429–431, 455), STORY 1 (line 103), `AMAZON_INTERVIEW_PREP.md` STORY 7 (lines 290–298), `LP_RUBRIC.md` (Deliver Results 65–79, Earn Trust 103–118, LBC 215–232), BGSW source tree re-scan for browser/UA/WebAssembly detection code.
**Repair-adherence check:** pass-1 repair plan items 2–5 verified applied; item 1 verified *partially* applied — see gaps 2–3.

---

### 1. Verdict

- **Bar Raiser readiness: 4 / 5** (pass 1: 3 / 5)
- **Strongest LP:** Earn Trust — and it now *performs* the LP instead of only claiming it. "I never took a fleet count… that missing number was itself part of the same failure" is the answer volunteering its own worst data point. That is rubric line 117 ("Represents data and information entirely transparently") demonstrated in the telling, not asserted about it.
- **Biggest weakness:** The recovery still rests on one sentence of a prep document. No code, no message text, no shipped-artifact evidence exists for the compatibility check anywhere in docs or the codebase — the v2 file now admits this cleanly, but an admission is a defense, not evidence.

**Why 3 → 4:** every one of pass-1's five repair items was executed without inventing a single fact: the fix was restored to line 431's scope ("documented the minimum browser requirement" gone, WASM-detection gone from the core); the impact hole became an owned, explicit gap with a prepared concession line; the mislabeled LBC signal was remapped to a real Strong Signal (verified: line 231 exists; the old mapping was indeed the inverse of Concern line 223); the rewrite cost is now labeled an on-the-spot estimate with "weeks" deleted and the re-open condition lifted into the core; the WebAssembly/WebGL habit-sweep was narrowed to the environment-verify claim tied to the grounded BOM-parser lesson (line 103). Not a 5 because three embellishments survived or mutated (below) and the discovery/impact/artifact triad remains ungrounded.

---

### 2. What works

1. **The fix mechanics are (mostly) back inside the source's envelope.** Line 431 says "a browser compatibility check that displays a clear error message." The core now says exactly that, and the follow-up "What exactly does the compatibility check do?" is model honesty: it scopes to the record, then concedes the detection logic is "candidate recall… not something I can currently point to in documentation."
2. **The unmeasured failure is now the story's strongest ownership beat.** Para 2 ("I don't know today whether it was one cell's machine or half the floor, and that missing number was itself part of the same failure — I never went and looked") converts pass-1's #1 landmine into an Earn Trust demonstration. The GAP-tagged follow-up with the prepared concession line closes the "never invent a number" loop correctly.
3. **Rubric bookkeeping is clean.** All four Earn Trust bullets verified (lines 114, 115, 117; concern-avoidal 109–110). All three LBC bullets verified against real Strong Signals (226, 228, 231). The DR touch maps to line 78. Third-person slip fixed to first person. The v2 annotation explaining the line-223 inversion is correct and shows the builder actually read the rubric.
4. **Judgment is explicit without fabricated history.** The WASM→JS-fallback decomposition is labeled "my on-the-spot estimate… not a scoped plan" (core and follow-up agree), and the re-open condition ("if a still-supported browser on the fleet had shown the same gap, I would have paid that cost") reads as a stated decision rule — legitimate reasoning, not invented meeting minutes.
5. **Source hygiene held.** Conflicting `AMAZON_INTERVIEW_PREP.md` STORY 7 telling verified conflicting again (150MB/3–5s/4GB-float16 at lines 290–298) and correctly excluded; STORY 4 line citations all land on the claimed content (401, 407, 411, 413, 415, 423, 425, 431).

---

### 3. Biggest gaps

Ranked by interview risk:

1. **The recovery artifact still exists nowhere.** A fresh scan of every `.py`/`.html`/`.css` file in the BGSW tree for UA sniffing (`userAgent`, `Trident`, `ActiveXObject`, `IE11`, WebAssembly-support checks) returns **zero hits**. The check lives only in line 431. The v2 follow-up even says "code I wrote" — recall of code that the repo copy does not contain. "What did the error message say?" remains answerable only from memory, and memory of your own fix is exactly what a Bar Raiser pressure-tests.
2. **The file contradicts its own repair note — the "silently failing" claim came back wearing a synonym.** The v2 note says the "failing silently" embellishment "is removed." The core para 4 dropped it ("instead of a mystery"), but the Deliver Results strong-signal bullet reintroduces it verbatim in spirit: "**broken-in-silence**." Line 431 never characterizes the pre-fix UX at all — the pre-check experience on IE11 is undocumented (console error? blank canvas? hang?). A provenance section that claims a removal the text didn't perform is a credibility leak in the answer file itself.
3. **"Startup" survived pass-1's explicit removal order.** Repair item 1 named it: *remove "runs at startup."* Para 4 still reads "I added a **startup** browser-compatibility check." The only "startup" anywhere in the sources is line 455 — the localStorage autosave-mode flag, unrelated to browser detection. One-word fix, unforced error.
4. **Discovery scene is still empty — honestly.** The prepared line "the failure surfaced through use, not through a test I designed" is inference-by-elimination (defensible), but a Bar Raiser asking "who told you, where, what did they say?" gets nothing until the candidate recalls. Correctly GAP-flagged; still a hole, not a repair.
5. **New minor overclaim: "public failure."** The LBC "accepts challenging situations despite risk of failure" bullet says the compatibility check and self-re-examination came "after a **public** failure." Nothing in the story or sources establishes an audience beyond the affected engineers — users hitting a broken file is not "public" in the career-cost sense the word invites. This bait's a probe ("how public was it?").

---

### 4. Credibility audit

| # | Claim (v2) | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | Library sizes ~8MB/~3MB/~1MB/~500KB, base64 WASM, compile script behavior | "Sourced?" | Line 411, 413, 415 — verified verbatim | **Keep** |
| 2 | "IE11 has no WebAssembly; OpenCV.js is a WASM module" | (basic fact) | Line 431 + 415 | **Keep** |
| 3 | "Never took a fleet count… one cell's machine or half the floor" | "Why not?" | Self-declared absence; matches "some had IE11" and nothing more at 431 | **Keep — this IS the repair**; honest gap, owned |
| 4 | "A **startup** browser-compatibility check" | "When does it run? Where's the code?" | Line 431 says only "added a browser compatibility check"; startup timing found only at line 455 re: localStorage; zero detection code in repo | **Soften** — delete "startup" (pass-1 order, still open) |
| 5 | "instead of a mystery" (core) / "**broken-in-silence**" (DR bullet) | "How do you know what it did before the check?" | Pre-fix UX undocumented anywhere | **Remove the bullet contrast; soften core clause to "with no explanation"** — and fix the v2 note, which claims this removal happened |
| 6 | "the engineer got an explicit, understandable 'this won't run here'"; follow-up "on the IE11 machines users got an explicit error message" | "Did an IE11 user actually see it? Confirm?" | Close paraphrase of 431 ("displays a clear error message"); user-confirmation of it working exists nowhere | **Keep at source scope; do not embellish further** — if pressed beyond "I added it so they would," that's a concession |
| 7 | Rewrite = "complete rewrite"; JS-fallback decomposition = on-the-spot estimate | "Did you scope it?" | Line 431 supports "complete rewrite"; estimate explicitly labeled | **Keep** — correctly hedged |
| 8 | Re-open condition (would pay rewrite for supported browser) | "Was that a real decision at the time?" | Stated counterfactual rule, not history | **Keep** — judgment, not fact |
| 9 | "~5s load, double-click, offline, no installs" still delivered value | "Adoption proof?" | Lines 423, 425 | **Keep** |
| 10 | BOM-parser cross-lesson | "Same lesson, specifically?" | Line 103 verified (collect real samples before building) | **Keep** |
| 11 | ET ×4, LBC ×3, DR ×1 rubric mappings | Rubric check | Verified 114/115/117, 109–110, 226/228/231, 78 | **Keep** — pass-1 mislabel fixed; third-person fixed |
| 12 | "after a **public** failure" (LBC bullet) | "Public — who knew?" | Nothing beyond affected users in sources | **Soften** to "after a failure users experienced" |
| 13 | Exclusion of 150MB telling | Consistency check | Lines 290–298 confirmed conflicting | **Keep exclusion** |

---

### 5. Follow-ups

1. **What was the actual problem?** — **SAFE.** Assumption-vs-IE11-vs-WebAssembly, fully grounded at line 431; para 2–3 answer crisp.
2. **What did you personally do?** — **PARTIAL.** Solo work unambiguous; the one fix artifact (check) exists only in line 431 and claimed recall — no code in the repo.
3. **Why this approach (gate + message)?** — **SAFE.** EOL-browser cost/benefit stated, estimate properly labeled.
4. **What alternatives did you reject?** — **PARTIAL.** Only "complete rewrite" addressed; upgrading machines, portable browser, or an IT request have no documented consideration. Do not retrofit — answer "I weighed the rewrite and the gate; the other options didn't exist under the no-install constraint" only if true.
5. **How did you measure success?** — **GAP (now honest).** Fleet count never taken; the prepared concession line is the right answer, but there is still no measurement to point at.
6. **How reliable were the results?** — **PARTIAL.** Modern-browser side grounded (423/425); the check's actual field effect — did the mystery end? — has zero evidence.
7. **What went wrong?** — **SAFE.** The core IS the answer.
8. **What was the hardest part?** — **PARTIAL.** Admitting it reads genuinely, but the human cost (did users chase you? did anyone senior know — see "public" flag) is undocumented.
9. **Did anyone disagree?** — **GAP.** No stakeholder reaction on record anywhere. Likely response remains "it was my call and nobody pushed back because it was my failure to own" — only if true.
10. **What were the trade-offs/costs?** — **PARTIAL.** Rewrite cost hedged well; the cost **paid by IE11 users** (blocked work? manual fallback?) is still absent from all sources.
11. **What happens at larger scale?** — **PARTIAL.** Environment-verify habit generalizes; v2 dropped the unsupported WebGL sweep, so the claim is now exactly as broad as its evidence. Still no post-event instance.
12. **What would you do differently?** — **SAFE.** This is now the story's spine (verify the actual machines before building) and echoes the grounded line-103 lesson.

---

### 6. Repair plan

Five highest-impact changes (credibility → ownership → impact → judgment → learning):

1. **Delete the word "startup" from para 4.** One word; pass-1 named it; line 431 does not support it; a Bar Raiser who hears an unrequested specific will ask "how do you know that's what it did?" (credibility)
2. **Make the file's repair note true.** Remove "instead of a mystery" from para 4 and "broken-in-silence" from the Deliver Results bullet; the pre-fix failure mode is undocumented. If the candidate genuinely recalls it (e.g., "the page opened but nothing worked"), that goes in labeled candidate memory — not as a bare assertion. (credibility — a provenance section that overclaims is worse than no provenance section)
3. **Drop "public" from the LBC bullet** → "after a failure the users experienced." Don't hand the interviewer a word you can't define. (credibility/register)
4. **Pre-interview recall work on the three irreducible holes** — (a) the discovery scene: who said what, where; (b) what the error message actually said and whether any IE11 user confirmed it; (c) what the blocked engineers did instead. If recall supplies nothing, the concession lines already written ("never took a fleet count," "candidate recall of code I wrote") are the answers — rehearse those verbatim. (ownership + impact)
5. **Decide once, before the interview, whether "I wrote that check code" is true.** The repo copy has no such code. If the candidate cannot recall writing it, soften follow-up #6's "code I wrote" to "I added the check per the record" — the difference matters if asked to draw it. (credibility)

---

### 7. Recommended structure

**STAR outline for v3 (essentially v2 with the three word-level fixes, ~430 words):**

- **S (15%):** Flask PCB suite; factory-floor machines — no internet, no installs, limited IT (line 401). Built standalone single-file HTML; libs base64-embedded (407, 411, 413, 415).
- **T (10%):** Success = *those specific machines* could double-click and run it.
- **A (30%):** Shipped; tested only on my own modern browser. Assumption broke: some machines ran IE11, no WebAssembly, tool didn't work on exactly the machines the build existed for. No fleet count — state that, own it (para 2 as written, minus no words). Surfaced through use, not tests (recalled scene if available).
- **R (25%):** Full IE11 fix = complete rewrite (431); judged not worth it for an EOL browser — on-the-spot estimate, said so; re-open condition stated. Added a browser-compatibility check that displays a clear error message (exact 431 scope — **no "startup," no silence contrast**). Modern-browser users got the full tool (~5s, double-click, 423/425).
- **L (20%):** Root cause = unverified environment assumption, not a bug; pattern named from the BOM parser (103); durable habit narrowed to "verify the actual target environment before building."

> **"What would still make me unconvinced as a Bar Raiser?"**
> The recovery is still a one-sentence inheritance. Line 431 says you added a check; the repo contains no such code; nobody on record ever saw the message. You've made every hole honest — that buys Earn Trust — but honesty is the floor, not the evidence. If I ask "draw me the check" or "quote me the error message" and the answer is recall you can't stand behind, your *failure* story is fully credible while your *recovery* remains a claim. A rehearsed concession is safe; a half-remembered fix is where candidates get caught. The v2 file also still asserts two things its own audit promised to delete — "startup," and the silence/mystery contrast — and at this level of hygiene, those surviving words undercut the provenance section that makes the rest of it strong.
