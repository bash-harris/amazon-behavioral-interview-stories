# GAUNTLET CONTEXT — Amazon Behavioral Answers (SDE1 / L4 focus)

## Objective
For each numbered behavioral question, produce ONE answer that a hiring manager / bar raiser would score as top-decile. The answer must be grounded ONLY in the real work captured in the source docs below.

## THE BAR (this is the whole trick — critic compares against it directly)
The bar is the worked STAR stories in the candidate's own prep bank, specifically:

**STYLE BAR = `AMAZON_INTERVIEW_PREPARATION.md` → "STORY 4: The Standalone HTML That Replaced a Server".**
Read it. Match its register:
- first person, spoken but precise
- concrete nouns + real numbers (library sizes, timings, file sizes, counts)
- shows the constraint, the technical reasoning, the trade-off, the measured result, and an honest reflection
- 300–500 words for the core answer, then a "Deep follow-ups" Q&A block
It must read as *natural and specific*, NOT synthetic/templated/"over-the-top buzzwordy". A reader should believe it happened.

## SOURCE OF TRUTH (read these; do not invent facts)
- LP rubric (strength/concern indicators): `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\behavioral\LP_RUBRIC.md`
- Story bank A (12 LP-mapped stories): `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\behavioral\AMAZON_INTERVIEW_PREP.md`
- Story bank B (15 deep stories; STORY 4 = style bar): `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\behavioral\AMAZON_INTERVIEW_PREPARATION.md`
- Bar raiser technical prep: `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\BAR_RAISER_TECHNICAL_PREP.md`
- BGSW image-visualization codebase (PCB Inspector Suite): `C:\Users\bkh\Downloads\bgsw\Image visualization\Image visualization\` (e.g. `CODEBASE_DOCUMENTATION.md`, `compile_tool.py`, `pcbinspector.html`, `bom_verification.html`, `model/`, `PCBvsLayoutnew/`)
- Tab Scroller extension code + docs: `C:\Users\bkh\Downloads\tab scroller\` (e.g. `PRD.md`, `EXTENSION_SUMMARY.md`, `STORE.md`, `10_project.md`, `IMPLEMENTATION_GUIDE.md`, `background.js`, `content.js`, `ai-command-ui.js`)
- Tab Scroller upgrade plan: `C:\Users\bkh\Downloads\tab scroller\Tab_Scroller_Industry_Grade_Upgrade_Plan.md`

## PROJECT FACT SHEET (verified from the docs above)

### Project 1 — BGSW PCB Inspector Suite (Bosch image visualization)
- Browser-based PCB inspection suite built as standalone HTML; also a PCB-vs-Layout comparison web app.
- Tools: BOM parser/reconciliation (MP_ prefixes, hyperlinks, DNP proximity, variant resolution), image alignment (affine → homography → TPS warping for non-rigid board deform), ML defect classification (EfficientNetV2S via TensorFlow.js; also GPT-4o VLM used as an inspection engine in one version), training pipeline (two-phase / progressive unfreezing, CLAHE preprocessing, confusion-matrix analysis), training-data collector.
- Deployment: `compile_tool.py` concatenates HTML/CSS/JS + embeds libraries as base64 (OpenCV.js ~8MB, TF.js ~3MB, PDF.js ~1MB, XLSX.js ~0.5MB; total ~12.5MB → ~25MB single HTML file; ~5s load on factory machines vs 2s server); localStorage auto-save with 5MB quota handling + GC; no server/network needed.
- Users: manufacturing engineers on restricted factory-floor machines (no internet, no installs, limited IT).
- Other: debug endpoint for manufacturing transparency; 4-signal comparison pipeline; modular refactor from a 4000+ line monolith.

### Project 2 — Tab Scroller (Chrome extension, Manifest V3)
- Hover-activated tab ribbon, `Ctrl+K` instant search, full keyboard nav, tab-group support, hover previews, themes; O(1) event-driven architecture.
- AI command layer (`Alt+Shift+T`): natural language → browser actions; Gemini + Ollama; intent recognition, context extraction, tool-calling Action Engine.
- Token-saving engine: rule-based local shortcuts for simple commands, smart pre-filter of relevant tabs, parallel metadata extraction (<1s), triplet compression ([Subject, Predicate, Object]).
- Tab Snoozing: `chrome.alarms` 1-min tick, `chrome.storage.local` snoozedTabs {url,title,wakeTime}, auto-resume as inactive tabs, survives browser restart (PRD.md, 3 iterations: alarm/storage engine, message handler, context-menu UI).
- Other features: tab sorting (title/domain/last-active), tab analysis (duplicates/inactive), batch ops, tab expiration & declutter, emoji favicon replacement, context-aware hibernation, "AI privacy shield" boss key, multi-tab scrape & copy, zero-trust tab quarantine (anti-phishing), workspace auto-scaffolding.
- Positioning target: "AI research workspace / browser OS / knowledge workspace" (10_project.md).

## RULES (hard)
1. **No fabrication.** Only use facts in the sources. If you need a number that isn't documented, either use a qualitative statement or pull the real value from the code/docs. Never invent a metric.
2. **Reuse first.** Prefer an existing story from the banks; adapt its framing to the exact question. You may combine facts from 2 stories/2 projects if the question demands it, but keep facts consistent with the docs.
3. **Answer the exact question** — including hard framings ("a time you failed", "gave someone wrong information", "implemented a direction you didn't agree with"). Do not dodge.
4. **Cover strong signals, avoid concern signals** for the mapped LP (see rubric).
5. **Natural register.** No "I leveraged synergies". No buzzword padding. It should sound like the existing stories.

## OUTPUT FORMAT (builder writes to `gauntlet\answers\Q{n}.md`)
```
# Q{n} — <question verbatim>
**Mapped LP(s):** <...>
**Story used:** <existing story name, or "synthesis of X + Y facts">

## Answer (core, ~300–500 words)
<STAR narrative, first person, real metrics>

## Strong signals covered
- <LP strength indicator> → <where in the answer>
...

## Deep follow-ups (likely bar-raiser probes)
**Q:** ... 
**A:** ...
(4–6)

## Fact provenance
- <claim> → <source file>
```

## LESSONS FROM EARLIER ROUNDS (avoid these; they cause FAILs)
1. **Never blend two conflicting source tellings.** The story banks contain overlapping retellings with different numbers (e.g. the VLM result appears as ~85% in PREPARATION.md STORY 8 and a "100 board pairs / 92%" set in PREP.md STORY 3). Pick ONE telling, use ONLY its numbers, and cite that exact source. Do not merge.
2. **Every number gets a source.** Add its file (and line if possible) in Fact provenance. If you cannot source a number, cut it.
3. **Do not overclaim.** If the docs say "expected performance gains", do not present them as measured. Anchor productivity/impact claims in documented outcomes (workflow removed, real measured result) or label honestly as projected.
4. **Attribute external idea-gathering concretely** (name the actual external tools/models/ecosystems evaluated or adopted, and the internal people whose feedback shaped the design) — Invent and Simplify requires this.
5. **Show the "scalable" half of Invent and Simplify** where relevant, not just simplicity.

## CRITIC RUBRIC (critic writes to `gauntlet\critiques\Q{n}.md`)
Judge the answer against the bar. Output EXACTLY:
```
VERDICT: PASS | FAIL
SCORE: x/10
BIGGEST GAP: <one sentence>
SPECIFIC FIX: <one concrete instruction>
Coverage: <LP> strength indicators hit/missed
Style match vs STORY 4: <same | better | worse>
Fabrication check: <clean | suspicious: ...>
```
PASS only if: every Strength indicator for the mapped LP is evidenced; zero Concern indicators triggered; style is as natural/specific as STORY 4; no fabricated facts; the exact question is answered head-on.
Praise is not useful. If it is not as good as the bar, FAIL it.

**REUSE RULE (user instruction): reusing an existing documented story for a new question is ALLOWED.** Do NOT fail an answer merely for reusing a story already used by another question. Only fail for: (a) fabrication/unsupported facts, (b) a mapped-LP strength left unevidenced or a concern triggered, (c) failing to answer the exact question, or (d) the answer being a near-verbatim copy that does not reframe/adapt to the new question. A distinct re-frame of a known story is a PASS if (a)-(d) are satisfied.
