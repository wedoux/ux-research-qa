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

What's being checked is **defensibility**, not whether an interpretation is right: is
it grounded in evidence, placed in its context, and argued? Don't write "bias
detected", don't call findings about people "validated", and don't describe the
material as themes that "emerged" — themes are written by someone, and that someone
can be asked why.

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
- [ ] Step 0: Gather declarations — belief register and study record
- [ ] Step 1: Confirm there's a conclusion to evaluate (not raw notes)
- [ ] Step 2: Provenance pass — trace every claim to evidence
- [ ] Step 3: Falsification pass — try to break each conclusion
- [ ] Step 4: Pitfalls check — screen against references/pitfalls.md
- [ ] Step 5: CK pass — run CK-01 to CK-06 from references/checks.md
- [ ] Step 6: Produce the readout using templates/readout.md
```

**Step 0 — Gather declarations.** Before reading the claims, find what the team
declared up front: a **belief register** (what they believed before the study, how
sure they were, and why) and a **study record** (the decision it informs, the
questions it asked, and what its limits rule out).
- **If they're in the material,** use them exactly as written. Don't correct, complete
  or reword them. A missing field, or a value the template doesn't allow (such as
  confidence "medium"), is missing input: name it, and let the checks that need it
  report NOT RUN.
- **If the material says none exist** ("none declared"), that is the user's choice.
  Proceed, and report the checks that depend on them as NOT RUN.
- **If the material doesn't mention them at all,** ask once whether they exist. If
  not, point to [templates/belief-register.md](templates/belief-register.md) and
  [templates/study-record.md](templates/study-record.md) and say the user should write
  their own: beliefs and questions are only useful when written by the people who
  hold them. You may ask questions that help them write it ("What did you expect to
  hear before the sessions? How sure were you, high or low? Where did that come
  from?"). Proceed without them only if the user chooses to.
- **Never draft, infer or fill in** a belief, question or limit — not from the claims,
  not from the evidence, not when asked.

Checks that depend on each record: belief register → CK-01 part (a) and CK-04 ·
study record `limits` → CK-02 · study record `questions` → CK-06.

**Step 1 — Confirm there's a conclusion to evaluate.** This skill QAs conclusions that
already exist — findings, personas, themes, verdicts. If the user has only raw notes,
transcripts, or reviews and no conclusions yet, say so: this skill evaluates
conclusions, it doesn't write them. Ask the user to state the claims they want
checked, in their own words, and stop there.

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

**Step 5 — CK pass.** Read [references/checks.md](references/checks.md). Run CK-01 to
CK-06 on every claim under review, against the declarations from Step 0. Each check
gets exactly one result:
- **FIRES** — quote the text that triggered it and name the declared item it
  conflicts with (a belief ID, a limit's `cannot_claim`, or the question IDs it misses).
- **CLEAR** — the check ran on complete input and found nothing.
- **NOT RUN** — the input it needs is missing or incomplete. Name what's missing.

A check that fires on the part of its input it could see reports FIRES. CLEAR needs
all of its input. If unsure between CLEAR and NOT RUN, report NOT RUN — a check that
didn't run is never reported as passed. When CK-05 and P-01 both fire, report both.

**Step 6 — Produce the readout.** Use
[templates/readout.md](templates/readout.md) to write up the result: what was
declared upstream, then for each finding its evidence strength, whether the claim
matches its evidence, the four questions, and the decision boundary ending in "Safe
to act on". Recall over precision applies here — a flagged weak conclusion is this
skill succeeding, not failing. Never soften a WEAK or UNCERTAIN verdict into
something more comfortable, and never present a hedge as if it were an argument (see
P-06 in the pitfalls file for exactly this failure mode). An honestly hedged claim on
thin evidence is correct practice, not a flaw: say so.

## Reference files

- [references/checks.md](references/checks.md) — checks CK-01 to CK-06, which audit
  claims against the declared belief register and study record, with worked examples.
- [references/pitfalls.md](references/pitfalls.md) — the eight-pitfall taxonomy this
  skill screens against. Self-contained; no prior context needed.
- [references/principles.md](references/principles.md) — the reasoning discipline
  behind the workflow (why falsification-first, why recall over precision, why weak
  isn't a failure).
- [templates/readout.md](templates/readout.md) — the output template. Always structure
  the final readout this way; it's what makes the QA pass auditable rather than just
  a stated opinion.
- [templates/belief-register.md](templates/belief-register.md) and
  [templates/study-record.md](templates/study-record.md) — blank records for the user
  to fill in. Offer them; never fill them in.
