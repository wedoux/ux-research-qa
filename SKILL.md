---
name: ux-research-qa
description: Runs a rigorous QA pass on UX research synthesis — findings, personas, themes, and conclusions — to catch reasoning errors before they drive a product decision. Built especially for AI-generated research output, where confident-sounding claims can outrun the evidence behind them. Traces every claim to its evidence, attempts to falsify each conclusion, and screens for recurring reasoning pitfalls (unsupported claims, formulaic hedges, mistaking evidence volume for evidence strength). Use when asked to sanity-check, QA, stress-test, red-team, peer-review, or get a second opinion on research findings, personas, themes, or conclusions; to check whether a finding is supported by the interviews, reviews, usability tests, or surveys behind it; to verify citations or evidence traceability; or to surface counter-hypotheses for a pattern in the data. Not for generating new research, writing discussion guides, or synthesizing raw notes into themes — evaluates conclusions that already exist, does not produce new ones.
---

# UX Research QA

Red-team research conclusions. Evaluate reasoning; don't generate new insight.

## Stance

This skill's identity is **evaluate, don't generate**. The default posture toward any
finding under review is adversarial, not confirmatory: assume at least one reasoning
error is present and go looking for it. If a genuinely careful pass finds nothing
wrong, say so explicitly and say why the evidence is unusually clean — don't
manufacture a finding, and don't skip the check.

Read [references/principles.md](references/principles.md) before running the workflow
below if this is the first time using this skill in the conversation — it explains the
reasoning behind each step, not just the mechanics.

## Before starting: get a clean pass

The critic should not watch itself reason. If the synthesis being reviewed was just
produced earlier in *this same conversation*, tell the user directly: **run this QA
pass in a fresh conversation**, pasting in only the synthesis and the underlying
evidence (interview excerpts, review text, survey data — whatever the claims cite).
A model reviewing its own immediately-prior output is grading its own homework. This
matters most when the stakes are high; for a quick gut-check the user can decide the
tradeoff themselves, but say this once so they can make that call.

## Workflow

Copy this checklist and track progress through it:

```
QA Progress:
- [ ] Step 1: Confirm there's a conclusion to evaluate (not raw notes)
- [ ] Step 2: Provenance pass — trace every claim to evidence
- [ ] Step 3: Falsification pass — try to break each conclusion
- [ ] Step 4: Pitfalls check — screen against references/pitfalls.md
- [ ] Step 5: Produce the readout using templates/readout.md
```

**Step 1 — Confirm there's a conclusion to evaluate.** This skill QAs conclusions that
already exist — findings, personas, themes, verdicts. If the user has only raw notes,
transcripts, or reviews and no synthesis yet, see "If there's no synthesis yet" below.

**Step 2 — Provenance pass.** For every claim in the material under review: does it
trace to a specific piece of evidence? Mark each as **observed** (stated directly in
the source material) or **inferred** (a conclusion drawn from it). Flag any claim with
no evidence behind it, even a plausible-sounding one. Do not invent citation IDs or
unit numbers that aren't present in what you were given — cite by describing the
evidence itself when no identifier exists.

**Step 3 — Falsification pass.** For each conclusion: what is the strongest argument
against it, using only the material provided? What specific evidence — if it
existed — would overturn it? Where does the evidence simply run out, making the claim
underdetermined rather than wrong? A conclusion that hasn't been actively challenged
is a summary, not an evaluation.

**Step 4 — Pitfalls check.** Read
[references/pitfalls.md](references/pitfalls.md) and test every conclusion against
all eight pitfalls. This is the skill's bundled knowledge base — it's written to be
self-contained, so read it in full rather than skimming for familiar terms. Note which
pitfalls fire and which specific text triggered them.

**Step 5 — Produce the readout.** Use
[templates/readout.md](templates/readout.md) to write up the result: evidence
strength, provenance table, falsification pass, pitfalls triggered, and what would
change the verdict. Recall over precision applies here — a flagged weak conclusion is
this skill succeeding, not failing. Never soften a WEAK or UNCERTAIN verdict into
something more comfortable, and never present a hedge as if it were an argument (see
P-06 in the pitfalls file for exactly this failure mode).

## If there's no synthesis yet

If the user has raw notes, transcripts, or reviews but no synthesis to QA, you may
produce a **minimal** first-pass synthesis — themes and a one-line finding per theme,
nothing more elaborate — and then immediately QA it using the workflow above. Keep the
synthesis step genuinely minimal: this skill's job is the QA pass, and a first-pass
synthesis exists only to give the QA pass something to test. Do not treat this skill
as a synthesis tool; if the user wants full research planning, discussion guides, or
deep synthesis, that's a different task.

## Reference files

- [references/pitfalls.md](references/pitfalls.md) — the eight-pitfall taxonomy this
  skill screens against. Self-contained; no prior context needed.
- [references/principles.md](references/principles.md) — the reasoning discipline
  behind the workflow (why falsification-first, why recall over precision, why weak
  isn't a failure).
- [templates/readout.md](templates/readout.md) — the output template. Always structure
  the final readout this way; it's what makes the QA pass auditable rather than just
  a stated opinion.
