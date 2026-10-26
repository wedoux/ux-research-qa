# UX Research Pitfalls Taxonomy

Eight recurring ways AI-generated (and human-generated) UX research synthesis goes wrong
between "the data is real" and "the conclusion is trustworthy." Each pitfall names the
failure, shows what it looks like, and gives a concrete test for catching it. Run every
conclusion under review against this list.

None of these require access to the original interviews or the full corpus — only the
synthesis and the evidence excerpts it cites.

## Contents

- P-01 — Headline Generality
- P-02 — Context Blindness
- P-03 — Transcript Literalism
- P-04 — Volume Mistaken for Strength
- P-05 — Counter-Evidence Filed, Not Faced
- P-06 — Formulaic Transfer Hedge
- P-07 — Trust Without Process
- P-08 — Narrowing Sold as Resolving

---

## P-01 — Headline Generality

**The failure:** A finding is stated as a surface label instead of an observable
behaviour. Labels feel like insights because they're confidently worded, but a label
has no trigger and no consequence — there's nothing underneath it for a product team to
act on.

**What it looks like:**
- "Users distrust the app."
- "Onboarding is confusing."
- "People want more control."

**What it should look like:** a named behaviour, what triggers it, and what it costs.
- "Users open a second weather app before committing to outdoor plans when the forecast
  contradicts what they can see out the window."

**Detection test:** For each finding, ask three questions. If any answer is missing or
vague, the finding is a label, not an insight.
1. **Behaviour** — is there an observable action? (Not a feeling or attitude — could you
   watch this happen in a session recording?)
2. **Trigger** — is the cause specific and falsifiable? (Could you design a test that
   would disprove it?)
3. **Consequence** — does it point at a specific decision, feature, or workstream? (Or
   would this sentence read the same in a report about any other product?)

A finding that fails the "any other product" test — where swapping the product name
changes nothing — is a label.

---

## P-02 — Context Blindness

**The failure:** The synthesis treats every finding as if it's being discovered for the
first time, ignoring what the team already knows. This causes two specific problems:
re-presenting an established finding as new, and missing a contradiction with prior
research that should have been flagged.

**What it looks like:** A report that confidently "discovers" something a 2024 study
already established, or that contradicts a previously established finding without
mentioning the conflict.

**What it should look like:** Explicit acknowledgment of prior research status —
confirmed, novel, or contradicting — for every finding that touches ground the team has
covered before.

**Detection test:** For each finding, ask: has this or something adjacent to it been
studied before? If prior research exists (even a sentence of it, supplied by the
researcher) and the synthesis doesn't reference it, that's a gap — flag it rather than
silently accepting the finding as novel. If you don't have visibility into prior
research, say so explicitly rather than assuming the finding is new.

---

## P-03 — Transcript Literalism

**The failure:** Treating the transcript or the review text as the complete record of
what happened, when it structurally cannot be. Written text drops hesitation, tone,
timing, and the things a participant chose not to say. A synthesis that never
acknowledges this gap is over-trusting its own source material.

**What it looks like:** A verdict presented with total confidence when the underlying
signal is genuinely ambiguous, with no acknowledgment that a researcher who was in the
room might know something the text doesn't capture.

**What it should look like:** A synthesis that flags exactly where tacit knowledge
would matter — not "is there anything else?" in general, but a specific question tied
to a specific ambiguity.

**Detection test:** For any UNCERTAIN or CONFLICTED finding, is there a specific,
answerable question a researcher who ran the session could resolve? If the synthesis
has no mechanism for capturing what isn't in the transcript, or the question it asks is
generic enough to apply to any study, this pitfall applies.

Bad prompt: "Is there anything else from the session that might be relevant?"
Good prompt: "R03 defends forecast accuracy while every other signal points to a data
freshness problem. Was there a moment in that session — a pause, a correction, a
qualifier — that would help you tell whether R03 is a genuine outlier or a
misclassified signal?"

---

## P-04 — Volume Mistaken for Strength

**The failure:** Confidence is inflated by counting more evidence units from the same
source type, rather than by evidence that actually corroborates from an independent
angle. Ten App Store reviews saying the same thing is one data point repeated ten
times, not ten data points.

**What it looks like:** A STRONG or high-confidence verdict resting entirely on one
source type (all reviews, all interviews, all support tickets), with the source
homogeneity unmentioned.

**What it should look like:** Confidence explicitly discounted when evidence is
single-source, and explicitly increased only when independent source types
(interviews + reviews + analytics, for example) corroborate each other.

**Detection test:** List the distinct source types behind each corroborating claim.
If there's only one, the verdict should read UNCERTAIN or EMERGING, not STRONG or
STABLE — and the synthesis should say so, not just imply it through a numeric score.
Ask: would this verdict survive if nine of these ten units vanished and only one
remained? If yes, you have one real signal, not ten.

---

## P-05 — Counter-Evidence Filed, Not Faced

**The failure:** Contradicting evidence is listed in a "counter-signals" or
"limitations" section but never actually argued against in the reasoning that produces
the verdict. It's noted for the record, then the analysis proceeds as though it doesn't
exist.

**What it looks like:** A report that names a contradicting review or data point, then
delivers a verdict that reads exactly as it would if that evidence weren't there at all.

**What it should look like:** Every piece of counter-evidence gets a specific reason,
in the reasoning itself, for why it doesn't overturn the verdict — or the verdict
changes.

**Detection test:** For each counter-signal named in the synthesis, find the sentence
that explains why it doesn't change the conclusion. If you can't find one — if the
counter-signal appears once, in a list, and never again — it was filed, not faced. This
is the single most common failure in AI-generated research synthesis: models are good
at surfacing contradictions and bad at resolving them.

---

## P-06 — Formulaic Transfer Hedge

**The failure:** A finding based on one population (one market, one platform, one user
segment) is extended to a different population with a caveat that sounds rigorous but
argues nothing. The hedge is decoration; the verdict underneath is unchanged.

**What it looks like:** "This finding may not fully transfer to EU users." Full stop.
No explanation of what's actually different about EU users, no assessment of whether
the difference matters, no statement of what would need to be true to trust the
transfer.

This is not a hypothetical. In testing across four frontier models on the same corpus,
**all four** flagged a US-to-EU transfer with some version of this sentence, and *none
of them argued it* — they named the caveat and moved on as if it had been resolved.

**What it should look like:** A named structural difference, an assessment of whether
it matters, and a statement of what evidence would be needed to trust the transfer.
"EU users have lower Personal Weather Station density than the US and have credible
national meteorological services (MeteoSwiss, DWD, Météo-France) as free alternatives —
the trust dynamic this finding depends on may not exist there. Confirming this would
require EU-market reviews or interviews; none exist in this evidence set."

**Detection test:** Read the sentence right after the hedge. Does it name a specific,
checkable structural difference between the two populations? Does it say what would
need to exist to resolve the uncertainty? If the sentence would still make sense with
the geography or population swapped out for a different one, it's formulaic.

---

## P-07 — Trust Without Process

**The failure:** A verdict is stated with its conclusion but not its reasoning — the
classification is asserted rather than derived. This makes the verdict impossible to
audit: you can agree or disagree with the label, but you can't tell whether the
thinking that produced it was sound.

**What it looks like:** "Classified as WEAK because the evidence does not support the
theme." That's the conclusion restated, not an argument.

**What it should look like:** "Classified as WEAK because the only two supporting
reviews describe a UI confusion, not a trust failure — the theme as submitted
conflates 'confusing' with 'untrustworthy,' and no evidence in the set supports the
trust framing specifically."

**Detection test:** Try to reconstruct the classification from the stated reasoning
alone, without seeing the label. If the reasoning is specific enough that you'd arrive
at the same classification independently, it passed. If the reasoning just restates
the label in different words, it's an assertion, not an argument. Apply this same test
to any stated counter-argument: does it explain why the counter-evidence fails to
overturn the verdict, or does it just acknowledge the counter-evidence exists and move
on?

---

## P-08 — Narrowing Sold as Resolving

**The failure:** Evidence that narrows a hypothesis space gets presented as evidence
that resolves the underlying problem. Reclassifying a complaint from "forecast is
inaccurate" to "cache is stale" tells a team *where to look* — it does not guarantee
that fixing the cache will fix user trust. Narrowing is real progress; treating it as a
solved problem is overreach.

**What it looks like:** "The team can now fix the trust problem by addressing cache
invalidation." This is a causal claim — it asserts the fix will work — when the
evidence only supports an investigative claim.

**What it should look like:** "The team can now investigate cache invalidation as the
likely proximate cause, rather than investing in forecast model accuracy." This claims
only that the search space narrowed, which is what the evidence actually supports.

**Detection test:** For every claim about what a finding "enables" or "lets the team
do," check whether the verb is causal (fixes, resolves, solves) or investigative
(narrows, points to, suggests investigating). If it's causal, ask whether the evidence
actually demonstrates the fix works — usually it doesn't, it just identifies a more
specific place to look. Also check the stated limitation ("what this evidence cannot
support"): if it's a limitation nobody would have tried to violate anyway, it's
decorative, not a real constraint.
