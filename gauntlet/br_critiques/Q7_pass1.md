# Q7 Pass 1 — Bar Raiser Critique (original answer)

**Story under review:** `gauntlet/answers/Q7.md` — "tell me about a time you failed" (BGSW standalone HTML, IE11/WebAssembly compatibility failure)
**Verified against:** `AMAZON_INTERVIEW_PREPARATION.md` STORY 4 (lines 401–431), STORY 1 (line 103), `AMAZON_INTERVIEW_PREP.md` STORY 7 (lines 290–298), `LP_RUBRIC.md` (lines 65–79, 103–118, 215–232), `CODEBASE_DOCUMENTATION.md`, BGSW source tree (code scan for compatibility-check implementation).

---

### 1. Verdict

- **Bar Raiser readiness: 3 / 5**
- **Strongest LP:** Earn Trust — the self-criticism in paragraph 3 is genuine, specific, and non-defensive; it matches rubric bullets "Takes responsibility for shortfalls" and "Openly acknowledges mistakes" (LP_RUBRIC lines 114–115).
- **Biggest weakness:** The failure has no measured footprint. Nothing in the story or any source says how it was discovered, how many machines/users were affected, how long they were blocked, or that the compatibility check was actually shipped and worked. A failure story without discovery, impact, or resolution evidence reads as a lesson-learned essay, not a postmortem.

---

### 2. What works

1. **Root-cause ownership is excellent.** "It wasn't a tricky bug… it was an assumption about the deployment environment I never verified" and the explicit denial of the easy outs (machine age, IT setup) is exactly what Earn Trust interviews look for. No blame leakage anywhere.
2. **The "I" is unambiguous.** Solo project; every action, assumption, and decision is first-person. Zero "we" inflation.
3. **Honest partial resolution.** "I couldn't fully fix it" is far more credible than a neat recovery arc. Declining to rewrite for an EOL browser is a defensible cost/benefit call, and the story says so.
4. **Learning is concrete and cross-linked.** The BOM-parser environment-assumption callback (grounded at `AMAZON_INTERVIEW_PREPARATION.md` line 103) shows a repeated pattern being caught, not a one-off epiphany.
5. **Source hygiene in the answer file is strong.** The deliberate exclusion of the conflicting 150MB telling (`AMAZON_INTERVIEW_PREP.md` STORY 7) prevents a self-contradiction landmine if both banks were ever mined.

---

### 3. Biggest gaps

Ranked by interview risk:

1. **No impact quantification of the failure.** How many of the fleet were IE11? One machine or half the line? Who was blocked and for how long? Did anyone escalate? Every source searched contains zero numbers for the failure itself. This is the #1 probe for a "tell me about a failure" story and the answer cannot currently respond.
2. **The fix's mechanics are embellished beyond the source.** Line 431 supports only: "a browser compatibility check that displays a clear error message." The answer adds "runs at startup," "detects the missing WebAssembly support," "instead of failing silently," and "documented the minimum browser requirement." A code scan of the BGSW tree found **no WebAssembly support check in any non-vendor JS/HTML file** (only an unrelated localStorage backward-compat comment in `file_io.js:47`). "Documented the minimum browser requirement" appears in **no source document at all**.
3. **The lasting-behavior claim is unverifiable.** "I put a capability check into anything that depends on a platform feature like WebAssembly or WebGL" — WebGL appears in the sources only as an inference-accelerator, never as a gated capability. This is asserted habit-change with no demonstrated instance after this event.
4. **One rubric mapping is mislabeled.** "LBC — reacts to negative situations by focusing on how to improve for the future" is the *inverse of a Concern bullet* (LP_RUBRIC line 223), not a Strong Signal. The signal line also slips into third person ("re-examined **his** assumptions"), breaking STORY 4 register.
5. **Discovery narrative missing.** The story jumps from "distributed the file" to "They didn't" with no scene of how the failure surfaced — a complaint, a site visit, a returned USB. Bar Risers read discovery path as a proxy for how you actually stay connected to customers.

---

### 4. Credibility audit

| # | Claim | Likely challenge | Evidence needed | Verdict |
|---|---|---|---|---|
| 1 | Library sizes: OpenCV.js ~8MB, TF.js ~3MB, PDF.js ~1MB, XLSX.js ~500KB | "Where do these numbers come from?" | `AMAZON_INTERVIEW_PREPARATION.md` line 411 | **Keep** — grounded |
| 2 | "The standalone build never loaded at all — not a partial failure, a total one" | "How do you know it was total? Did the page render? Did TF.js load before OpenCV failed?" | Source only says tools couldn't work on IE11 (line 431); failure-mode detail unsupported | **Soften** to "the tool didn't work on those machines at all" or state how you know |
| 3 | "A browser-compatibility check that runs at startup, detects the missing WebAssembly support, and shows a clear, specific message instead of failing silently" | "Show me that code. What exactly did the message say?" | Line 431 supports only "displays a clear error message"; startup timing and WASM detection unverified; no such check found in codebase | **Soften** to source wording; locate the actual code or mark the mechanics as a gap |
| 4 | "I documented the minimum browser requirement" | "Where is that documentation? Can I see it?" | Not found in any source doc or codebase file | **Remove** unless real artifact exists → **GAP** |
| 5 | Rewrite "would have meant a complete rewrite — replacing the WebAssembly-dependent image pipeline with JavaScript fallbacks — and that cost wasn't justified" | "Did you actually scope the rewrite? Estimate?" | Line 431 supports "complete rewrite"; the JS-fallback decomposition is inference; cost ("weeks" in follow-ups) has no estimate behind it | **Keep as reasoning**, label explicitly as your estimate, not measured |
| 6 | "Those were exactly the machines the offline build existed to serve" | "How many machines? What fraction of the floor?" | Fleet inventory absent everywhere | **GAP** — needs a recalled number ("two of the cells," etc.) from the candidate, not invented by the builder |
| 7 | "I now verify the target environment before I build… the same lesson the BOM parser taught me" | "Give one concrete instance after this where you did it." | BOM-parser cross-reference is grounded (line 103); no post-event instance documented | **Keep** environment-verify claim tied to BOM link; **remove/soften** the "anything with WebAssembly or WebGL" sweep → **GAP** |
| 8 | "The modern-browser build shipped and worked as intended" | "Prove adoption." | Line 423–425 (25MB file, ~5s load, double-click use) | **Keep** |
| 9 | Earn Trust mappings (4 bullets) | Rubric check | LP_RUBRIC lines 110, 114–115, 117–118 | **Keep** |
| 10 | LBC mapping "reacts to negative situations by focusing on how to improve" | Rubric check | This is inverse-of-Concern (line 223), not a Strong Signal bullet | **Fix label** — remap to line 231 ("Discusses lessons learned from past setbacks") which exists |
| 11 | Excluded 150MB telling (`AMAZON_INTERVIEW_PREP.md` STORY 7) | (internal consistency) | Verified conflicting: lines 290–298 do contain 150MB / 3–5s / 4GB float16 numbers | **Keep exclusion** — correctly handled |

---

### 5. Follow-ups

1. **What was the actual problem?** — **SAFE.** Unverified modern-browser assumption; IE11 lacks WebAssembly (line 431 grounded).
2. **What did you personally do?** — **PARTIAL.** Solo work is clear, but the exact artifacts you built to fix it (check, docs) can't be pointed to.
3. **Why this approach (gate + message instead of fix)?** — **SAFE.** Cost/benefit vs EOL browser is stated and defensible.
4. **What alternatives did you reject?** — **PARTIAL.** Only "complete rewrite" is addressed. Probes for third options (upgrading the machines, portable browser, IT request) have no documented consideration — do not retrofit one that wasn't real.
5. **How did you measure success?** — **GAP.** No count of affected machines/users, no before/after of how the failure surfaced or stopped surfacing.
6. **How reliable were the results?** — **GAP.** No evidence the check shipped, worked, or ended the support issue; no user confirmed the message helped.
7. **What went wrong?** — **SAFE.** The core of the story; paragraph 2–3 answer crisply.
8. **What was the hardest part?** — **PARTIAL.** Admitting it is implied; the emotional/professional cost (were you the only one who knew? did users chase you?) is undocumented.
9. **Did anyone disagree?** — **GAP.** No stakeholder reaction on record — not even an engineer pushing back on "not supported."
10. **What were the trade-offs/costs?** — **PARTIAL.** Rewrite cost asserted but never estimated; the cost paid by IE11 users (blocked work? workaround?) is absent.
11. **What happens at larger scale?** — **PARTIAL.** Environment-inventory habit generalizes logically; no demonstrated instance after this event.
12. **What would you do differently?** — **SAFE.** Verify fleet before building; capability-gate platform dependencies (with audit-table #7 caveat on the WebGL sweep).

---

### 6. Repair plan

Five highest-impact changes, priority order (credibility → ownership → impact → judgment → learning):

1. **Restore the fix to what the source supports (credibility).** Reword paragraph 4 to line 431's exact scope: a compatibility check that displays a clear error message; remove "runs at startup," "instead of failing silently," and "documented the minimum browser requirement" unless the builder can locate the artifact. If the candidate genuinely recalls the code, that recall goes in with provenance "candidate memory, artifact to show" — never presented as documented fact.
2. **Close the impact gap with recalled (not invented) numbers (credibility + impact).** The answer must be able to say how the failure surfaced and roughly how many machines were affected. If the candidate cannot recall, mark it an explicit gap in the answer file and prepare the honest line: "I never got a fleet count — that itself was part of the failure."
3. **Fix the rubric bookkeeping (ownership/register).** Remap the mislabeled LBC signal to a real Strong Signal bullet (LP_RUBRIC line 231), and correct the third-person "his assumptions" to first person.
4. **Sharpen the judgment call (judgment).** Keep "complete rewrite" per source; explicitly frame the JS-fallback decomposition and "weeks" as the candidate's on-the-spot estimate; state the re-open condition ("if a supported browser had the same gap") in the core, not only the follow-ups.
5. **Make the learning demonstrable, not aspirational (learning).** Keep the BOM-parser link (line 103). Either attach one documented post-event instance of environment verification, or narrow the claim to exactly what is supported instead of the WebAssembly/WebGL sweep.

---

### 7. Recommended structure

**STAR outline for the repaired version (~430 words):**

- **S (15%):** Flask-based PCB suite; manufacturing engineers needed it on offline factory-floor machines — no internet, no installs, limited IT. (Source: line 401.)
- **T (10%):** Ship it as one double-clickable HTML file with all libraries embedded. Success meant *those specific machines* could run it.
- **A (35%):** Built it — compile script, base64 WASM embedding (~12.5MB libs). Shipped. Tested only on my own modern browser. **The failure:** some floor machines ran IE11; no WebAssembly; the tool didn't work on exactly the machines it was built for. State how it surfaced and roughly how many machines (recalled figures or an explicit honest gap).
- **R (20%):** Could not fix without complete rewrite — judged not worth it for an EOL browser, said so out loud. Added a browser-compatibility check that displays a clear error message (line 431 wording). Modern-browser users got the full tool; unsupported users got the truth instead of a mystery.
- **L (20%):** Root cause was an unverified environment assumption, not a bug. Pattern recognized from the BOM parser (line 103). New rule with one concrete applied instance: inventory the actual target environment before building for it.

> **"What would still make me unconvinced as a Bar Raiser?"**
> That the compatibility check exists only in the reflection sentence of a preparation document — no code, no message text, no artifact. A failure story's recovery is its evidence: if a Bar Raiser asks "what did the error message say?" or "how many people were affected?" and the answer is a shrug dressed as a lesson, the ownership reads as performance. Until discovery, impact, and the fix are grounded in recall-able fact (or honestly flagged as unknowns), this is a 3, not a 4.
