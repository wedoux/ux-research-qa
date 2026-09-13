# Governing Principles

The reasoning discipline behind the QA pass. These principles are distilled from a
working two-agent research-QA system; this file carries the reasoning rules forward
without the infrastructure (no corpus retrieval, no scoring engine, no registry — just
the judgment calls a careful reviewer applies by hand).

## Contents

- The core question
- Evaluate, don't generate
- Assume an error exists
- Recall over precision
- Provenance is not optional
- Falsification before commitment
- Weak is not a failure
- Trust comes from transparency, not confidence

---

## The core question

Every piece of research synthesis is implicitly answering one question: **is this
finding significant enough, specific enough, and well-evidenced enough to justify
someone acting on it?** QA is the discipline of pressure-testing that answer before
the acting happens, not after.

A verdict of STRONG should mean: a competent team should change a decision based on
this. WEAK should mean: the pattern may be real, but it's too generic, too
unactionable, or too thin to justify priority. UNCERTAIN should mean: the signal exists
but can't be evaluated without more data — and the missing data should be named
specifically, not gestured at.

## Evaluate, don't generate

This is the identity of the QA pass, not a style preference. A synthesis tool produces
findings. A QA pass tests whether those findings are warranted by the evidence behind
them. These are different jobs, and doing both in the same pass collapses the check:
you cannot adversarially review reasoning you just produced, because you already
believe it.

If no synthesis exists yet, producing one is a legitimate but secondary task (see
`SKILL.md`) — the QA pass is the headline. When both are needed, do the synthesis
first, then genuinely change hats before QA-ing it: read the synthesis as if someone
else wrote it.

## Assume an error exists

Default to adversarial, not confirmatory. Before evaluating anything, assume that at
least one of the following is true of the conclusion under review, and look for which
one:
- A behavioural signal has been misclassified.
- A surface-level label has been substituted for a causal mechanism.
- The conclusion overgeneralises from a thin evidence base.
- An assumption has been carried from one population, market, or context to another
  without being checked.

If a genuinely careful pass turns up nothing wrong, say so explicitly, and say why the
evidence is unusually clean — don't manufacture a finding to look thorough, and don't
skip the check because nothing jumped out immediately.

## Recall over precision

Flagging a weak or shaky conclusion is the system succeeding, not failing. In a
research-QA context, missing a real reasoning error is far more expensive than raising
a false alarm about a conclusion that turns out to be fine — a missed error becomes a
product team solving the wrong problem for months, while a false alarm costs one extra
review cycle. When genuinely uncertain whether something is a problem, surface it —
but always with named evidence for why, never as a vague hedge.

## Provenance is not optional

Every claim in a finding must trace to a specific piece of evidence: a quote, a review,
a transcript excerpt, an observation. Distinguish explicitly between what was
**observed** (stated directly by a participant or visible in the data) and what was
**inferred** (a conclusion drawn from the observation). A claim with no evidence behind
it — even if it sounds plausible — must be flagged as unsupported, not waved through
because it fits the narrative.

Pasted or summarised research text has no built-in citation IDs. Don't invent
precise-looking references (unit numbers, participant IDs) that aren't actually present
in the material you were given — cite by describing the evidence itself if no
identifier exists.

## Falsification before commitment

A conclusion that has not been actively challenged is a summary, not an evaluation.
Before treating any finding as settled, do the work of trying to break it:
- What is the strongest evidence *against* this conclusion, using only material
  actually provided?
- What specific piece of evidence — if it existed — would overturn this finding?
- Where does the current evidence simply run out, such that the claim is
  underdetermined rather than wrong?

A finding that survives this pressure is stronger for having been tested. A finding
that doesn't survive it needed to be caught before it reached a roadmap.

## Weak is not a failure

Evidence strength (STRONG / UNCERTAIN / WEAK) and review outcome (the finding holds up
to scrutiny / it doesn't) are independent axes. A WEAK classification that is
well-reasoned and well-evidenced is a successful piece of research — it tells the team
something is not yet worth prioritising, which is valuable. Don't treat a WEAK or
UNCERTAIN verdict as evidence that the underlying reasoning was flawed; judge the
reasoning that produced the classification, not how exciting the classification is.

## Trust comes from transparency, not confidence

Given how ambiguous "is this insight good" genuinely is, a QA pass cannot rely on being
right — it can only rely on showing its work. Value comes from exposing the reasoning,
naming the contradictions, and making uncertainty visible, not from sounding
authoritative. A confident-sounding verdict with no visible reasoning chain is worth
less than an uncertain one that shows exactly where the evidence runs out.
