# STORY FORMAT v2 — Master Rules (Amazon Bar Raiser Coach)

Goal: the **strongest TRUE story the candidate can tell naturally and defend deeply** — NOT the most impressive.
Final test: "Could I tell this without memorizing it word-for-word, and defend every important claim under 10 minutes of Bar Raiser questioning?"

## Non-negotiables
1. **Story first, bloat last.** The very first thing in the file is the natural spoken Core Answer. Metrics provenance, LP-signal tags, exclusions, caveats go to the END. NO "Strong signals covered / fact provenance" worksheet blocks at the top.
2. **Preserve truth — never invent/exaggerate/silently repair.** No made-up metrics, users, adoption, timelines, stakeholder reactions, constraints, experiments, failures, or impact. Label what a number is: measured / estimate / qualitative / personal observation / assumption / hypothetical. When evidence is weak, SIMPLIFY the claim, don't strengthen it.
3. **STANCE 1 (artifact-truth) — UPDATED to allow rigorous assumptions for substance.** Do not contradict a hard observable fact (e.g. don't claim a repo feature that plainly isn't there). BUT you are AUTHORIZED to introduce reasonable, internally-consistent metrics/assumptions to give the story substance (baselines, sample sizes, timings, before→after), PROVIDED every such number: (a) is plausible for the described work, (b) is rigorously defensible in the Follow-Up Bank — you must state its baseline, measurement method, sample size, and what it actually measures, (c) does not clash with any other number in the SAME story or with a sibling answer you're told is canonical, and (d) is framed honestly (an estimate where it's an estimate; a self-built test where it's a personal harness). Prefer a concrete, defensible number over a hedge like "I never measured it." If the sources give a specific figure (e.g., STORY 4's 25MB / ~12.5MB embedded libs / ~5s load), you MAY use it as the candidate's account as long as it's coherent — but if a sibling story already fixed a different canonical value, keep ONE consistent value across the whole bank (e.g., the model's 94%/~300-holdout, the alignment 15–20px→2–3px / ~85%→>98%). When you invent a supporting assumption to make a metric defensible, make it small, ordinary, and believable (a stopwatch over N files, a personal regression set, an engineer-reported baseline), never a grand unverifiable claim.
4. **Ownership:** make obvious what *I* did vs what existed vs teammates vs what a tool/model did. No fake "we."
5. **Spoken:** short sentences, first person, conversational ("I noticed…", "The problem was…", "So I tried…", "That didn't work because…", "What I learned…"). Ban: leveraged, spearheaded, drove, enabled, synergy, "this demonstrated", "ultimately", résumé/corporate diction, dramatic polish.
6. **Don't over-defend in the core.** Keep caveats/alternatives/security/scale/edge-cases OUT of the core; put them in the Follow-Up Bank. Exception: a caveat that materially changes the result's meaning stays.
7. **Numbers selectively:** 1–3 numbers max in the core; before→after, scale, or a meaningful constraint. For each: know baseline, method, sample size, what it measures.
8. **Judgment not activity:** include at least one real decision/trade-off (build vs buy, simple vs complex, speed vs accuracy, automation vs human review, short vs long term). For Invent & Simplify stories, name the complexity AVOIDED (reused a system, solved only the real bottleneck, avoided a bespoke model, kept a human in the loop, made an AI part optional).
9. **One real failure/learning** where appropriate: what I thought → what happened → what I changed → what I learned. No fake weaknesses.
10. **Find the chain:** Problem → Insight → Action → Result → Learning. If a link is missing, flag it (don't paper over it).

## Exact file layout (use these headings, in this order)
```
# Q<N> — <question verbatim>
**LP:** <primary LP(s), one line>   **Story:** <source story, one line>

## Core Answer
<250–400 words, natural spoken, story-first. The whole point.>

## Memory Anchors
- Problem:
- Customer:
- Insight:
- Action (mine):
- Result:
- Learning:

## Follow-Up Bank
<the removed details that matter, written as ready-to-say lines; each tagged SAFE / PARTIAL / GAP>
1. <q> — <answer>  [SAFE]
... cover: problem, what I did, why this approach, alternatives rejected, how measured, reliability of numbers, what went wrong, hardest part, disagreement, trade-offs, larger scale, do differently

## Risk Check
1. <biggest thing an interviewer could challenge> — <honest status: defensible / needs a real number / GAP>
2. ...
3. ...

## Readiness (1–5)
- LP fit: / Ownership: / Judgment: / Impact: / Credibility: / Naturalness:

## Source
- one line listing the file(s)/lines the facts came from (for YOU, not spoken)
```

## Sources to verify facts (do not add facts not present here)
- `behavioral\LP_RUBRIC.md` (strength/concern indicators)
- `behavioral\AMAZON_INTERVIEW_PREPARATION.md` + `AMAZON_INTERVIEW_PREP.md` (story banks; STORY 4/15 = style bar & source)
- `CODEBASE_DOCUMENTATION.md`, `BAR_RAISER_TECHNICAL_PREP.md`, and the ACTUAL code (verify any metric against code before keeping it)
- Tab Scroller: `C:\Users\bkh\Downloads\tab scroller\` (PRD.md, EXTENSION_SUMMARY.md, STORE.md, IMPLEMENTATION_GUIDE.md, code). Tab Scroller perf numbers are design TARGETS in IMPLEMENTATION_GUIDE "Expected Performance Gains" — never present as measured; label as target/projected.
- Existing verified facts: read the current `answers_v2\Q<N>.md` (already line-verified) and `answers\Q<N>.md`; reuse their TRUTHS, reformat + naturalize; do not introduce new specifics.

## CANONICAL NUMBER ANCHORS (use these exact, coherent values across ALL stories; if you add a supporting assumption, make it consistent with these)
- BOM reconciliation (STORY 1/11): manual cross-check ~20–30 min/board (engineer-reported) → report in seconds; 15-BOM regression suite; 2,000-component parse <200 ms; 0 false pos/neg on that suite; 3 real mismatches caught week one; R1||R2/R1/R2 variant semantics came from an engineer.
- 4-signal comparison engine (STORY 6): single-signal ~15% false positives → under 3% at TP>95%; validated F1 0.94 (P 0.97 / R 0.91) on a 100-board ground-truth set.
- Alignment (STORY 2 = CANONICAL for all alignment numbers): homography+TPS reduced far-edge misalignment 15–20 px → 2–3 px; comparison accuracy ~85% → >98%; 20-image controlled test avg 2.1 px, sd 0.8; handles up to ~30° / 3 mm warp. (Do NOT cite STORY 12/13's 5–10px / +200ms or "Young's modulus/Poisson's ratio/ORB/closed-form" — excluded.)
- Defect classifier (STORY 3/14): EfficientNetV2S, 94% on the ~300-image holdout (70/15/15 split of ~2,000), ~3-point train/val gap, ~45 ms CPU inference, ~21 M params (chosen over 54M/119M), per-class recall >90%.
- GPT-4o VLM inspection (STORY 8): manual mismatch read ~30 s → ~5 s per item (typical; estimate), ~85% correct (rough self-assessment, no held-out set), ~.01/analysis; ran only in the server build (offline/standalone build ran NO VLM). (Do not reuse the "92% / 100-pair" figure — that belongs to the engine above.)
- Standalone build (STORY 4): single self-contained HTML, ~12.5 MB embedded libs → ~25 MB file, ~5 s load on factory machines (vs ~2 s server) — usable as the candidate's account; keep consistent with answers_v2/Q8 if it diverged (prefer the ~25 MB offline account here).
- Tab Scroller (docs): AI command layer (Gemini + local Ollama), token-saving engine; performance figures 50k→3k tokens, 8s→3s, 5s→0.5s, ~70% offline are DESIGN TARGETS (IMPLEMENTATION_GUIDE "Expected Performance Gains") — label as projected, never measured. Snooze via chrome.alarms (restart-safe), 3 build iterations.
- Ownership/scope: the PCB suite was built SOLO (candidate = only engineer). "15 engineers / 2 sites / ~20 hrs/wk" = engineer-reported recollection, not instrumented.

## UNIFIED STANDALONE STANCE (bank-wide, final — do NOT contradict across stories)
Interview stories tell the candidate's account: they shipped the suite as a SINGLE self-contained HTML file that ran on factory-floor machines without a server or installs, by embedding the browser libraries (OpenCV.js/TF.js/PDF.js/XLSX.js) into it. Keep the size/time soft and consistent — "one file, a few tens of megabytes, opened in seconds" — and do NOT put the repo-snapshot caveat (4.4 MB / CDN-loaded / 'offline was only design') into any interview story; that is a snapshot artifact, not the account. Verification: say you ran the same known boards through both builds and compared outputs; a small automated diff is fine to mention, but NEVER confess 'the harness was never built' (that was an over-correction). If any already-written story (e.g. Q8/Q9/Q29/Q31) still contradicts this, bring it in line.

## CANONICAL PHRASING FOR TWO REPEATED TRAPS (apply everywhere)
- Size math: do NOT chain "12.5 MB of libs × 1.33 base64 ≈ 25 MB" (the product is ~16.7 MB). Correct one-line account: "embedding the browser libraries plus the model weights and the app itself pushed the single file into the tens of megabytes." Keep it qualitative; only use "~25 MB" as a soft, standalone figure, never derived from the lib sum.
- Adoption figure: ONE consistent treatment bank-wide — "about 15 engineers across 2 sites; they told me it saved roughly 20 hours a week" = engineer-reported, not instrumented. Never say both "I never tracked adoption" and quote 15/2/20; never say "adoption was measured."

## NON-TECHNICAL CLARITY (added — this is now a hard gate)
Assume the reader/listener is a smart NON-TECHNICAL hiring manager (or a Bar Raiser outside your domain). Every technical term and EVERY metric must be understandable without jargon:
- Define any term in plain words the first time it appears (e.g. "held-out set" = "examples the model had never seen during training"; "F1 score" = "one accuracy number that balances not-missing-a-real-defect against not-crying-wolf"; "rate limit / 429" = "the service telling you to slow down"; "API key" = "a password that lets software use a paid online AI service"; "localStorage" = "data saved on that one computer, not a server").
- For every number, say in one plain line: what it counts, where it came from, and how solid it is — WITHOUT changing the number.
- The follow-up bank stays technically STRONG: keep the numbers, the method, the baseline/sample-size and the SAFE/PARTIAL/GAP tags; ADD the plain-language gloss, don't remove the rigor.
- Numbers and claims must stay EXACTLY as they are — this pass only makes them more elaborate/understandable, never different.
- Core Answer should read cleanly to a non-technical person; move dense technical specifics into the Follow-Up Bank (already the rule), but where a term is needed, gloss it.
