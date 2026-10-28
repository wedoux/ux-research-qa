# QA Readout Template

Fill in every section for each finding under review. Keep the structure — it's what
makes the readout auditable — but write in plain language, not telegraphic labels.
If a section genuinely doesn't apply (e.g. no transfer claim is being made), say so
explicitly rather than deleting it; a silently-skipped section is indistinguishable
from a forgotten one.

The readout checks whether each interpretation is **defensible**: grounded in
evidence, placed in its context, and argued. It does not measure whether the
interpretation is right. The four question headings below group the checks by what
they ask of a finding; don't add framework names to them.

Rules that keep the readout honest:
- Replace every bracketed placeholder. Never copy a placeholder line back unfilled.
- Every CK ID (CK-01 to CK-06) appears exactly once per finding, in its question
  group, with exactly one result: **FIRES**, **CLEAR** or **NOT RUN**. A missing row is
  not a pass.
- Results appear only in the CK rows. Don't restate results in the Declared upstream
  table.
- When a check fires, start its "What triggered it" cell with the check's user-facing
  wording from `references/checks.md`, then quote the triggering text.

```markdown
## Declared upstream

[Once per readout, before the findings. List what the user declared, exactly as they
wrote it. Never add to it.]

| Record | Status | Items used | Feeds |
|---|---|---|---|
| Belief register | [Declared / None declared / Incomplete — what's missing] | [belief IDs used, or "none"] | CK-01 part (a), CK-04 |
| Study record: questions | [Declared / None declared / Incomplete — what's missing] | [question IDs, or "none"] | CK-06 |
| Study record: limits | [Declared / None declared / Incomplete — what's missing] | [each `cannot_claim`, quoted, or "none"] | CK-02 |

## Finding: [state the conclusion under review, verbatim, unedited]

**Evidence strength:** [one of: STRONG, UNCERTAIN, WEAK]
[One sentence, plain language, stating the verdict as you'd say it to a stakeholder —
not a hedge, a position.]

**Claim matches its evidence:** [Yes or No] — [one-line reason]
[Yes means the claim says no more, and no more surely, than its evidence allows. A
hedged claim on thin evidence is Yes: that is correct practice, not a flaw. If CK-01,
CK-02, CK-03, CK-04 or CK-05 fires, or P-01, P-04, P-05, P-06, P-07 or P-08 is
triggered, this is No: each of those describes a claim saying more than its evidence.]

### Is it true for these people?

**Falsification pass**
- **Strongest counter-hypothesis:** [the best alternative explanation for the same
  evidence — not a token objection, the one that would actually worry you]
- **What would overturn this finding:** [a specific, checkable piece of evidence —
  not "more data" but the actual data]
- **Where the evidence underdetermines the claim:** [name the specific gap, if any —
  or state that the evidence base is unusually complete for this claim]

**Counter-evidence:** [each contradicting piece of evidence, and the specific reason it
doesn't overturn the finding — or say the finding should change]

**Unsupported claims:** [any part of the finding with no evidence behind it, from the
provenance table below — or "none"]

| Check | Result | What triggered it | Conflicts with |
|---|---|---|---|
| CK-03 People treated as validated | [result] | [quoted text, or why clear, or what's missing] | [declared item, or "n/a"] |
| CK-04 Product finding without a human story | [result] | | |
| CK-05 Scope and certainty inflation | [result] | | |

| Pitfall | Triggered? | What triggered it |
|---|---|---|
| P-01 Headline Generality | Yes/No | |
| P-03 Transcript Literalism | Yes/No | |
| P-04 Volume Mistaken for Strength | Yes/No | |
| P-05 Counter-Evidence Filed, Not Faced | Yes/No | |
| P-08 Narrowing Sold as Resolving | Yes/No | |

### Where does it apply?

**Scope:** [who, where and when the evidence covers, and whether the claim stays
inside that]

| Check | Result | What triggered it | Conflicts with |
|---|---|---|---|
| CK-02 Beyond declared limits | [result] | | |

| Pitfall | Triggered? | What triggered it |
|---|---|---|
| P-06 Formulaic Transfer Hedge | Yes/No | |

### Could someone retrace it?

**Provenance**
| Claim | Source | Observed or inferred | Traceable? |
|---|---|---|---|
| [specific claim in the finding] | [quote, excerpt, or "not cited"] | Observed / Inferred | Yes / No — [why not, if no] |

State explicitly if any claim in the finding has no supporting evidence at all —
don't let it pass silently because the rest of the row looks fine.

**Checked against:** [the declared beliefs, questions and limits this finding was
checked against — or "nothing declared"]

| Check | Result | What triggered it | Conflicts with |
|---|---|---|---|
| CK-06 Drift | [result] | | |

| Pitfall | Triggered? | What triggered it |
|---|---|---|
| P-02 Context Blindness | Yes/No | |
| P-07 Trust Without Process | Yes/No | |

### Is it theirs or ours?

**Beliefs and evidence:** [which parts of the claim come from what participants did or
said, and which come from what the team already believed or someone senior said]

| Check | Result | What triggered it | Conflicts with |
|---|---|---|---|
| CK-01 Borrowed conviction | [result] | | |

### Tacit-knowledge prompt (optional — ask only if a researcher who ran the sessions is available)
[A specific question tied to the actual ambiguity above — not "anything else to
add?" Anchor it to the exact moment or contradiction that's unresolved.]

### Decision boundary
- **Supports:** [what the evidence does let the team say]
- **Doesn't support:** [what it doesn't, in plain words]
- **What would close the gap:** [The single most useful next piece of evidence someone
  could go get. Not a wish list — the one thing that would move this from UNCERTAIN to
  settled, or from apparently-STRONG to revealed-as-WEAK.]

**Safe to act on:** [Yes or Not yet] — [one reason]
```

## Safe to act on

Combine the two judgments and the checks:

| Evidence strength | Claim matches its evidence | Any check fired or not run | Safe to act on |
|---|---|---|---|
| STRONG | Yes | None | **Yes** — [reason] |
| WEAK or UNCERTAIN | Yes | — | **Not yet** — the claim is honest, but the evidence is thin. |
| Any | No | — | **Not yet** — the claim says more than its evidence: [reason] |
| Any | — | Any NOT RUN | **Not yet** — [missing input] wasn't declared, so [check] couldn't run. |

A check that didn't run can't support "Yes". Name the missing input in the reason.

A claim labelled as a hypothesis is never "Yes": it isn't a finding yet. Say "Not
yet", and let the reason say it's ready to be tested.

Pitfalls feed the same decision:
- P-01, P-04, P-05, P-06, P-07 and P-08 describe overclaiming. If any is triggered,
  "Claim matches its evidence" is No, so the finding is "Not yet".
- P-02 and P-03 are about process. "Yes" is still possible when one is triggered, but
  the reason must say why it doesn't weaken the decision.

## Rolling up multiple findings

When QA-ing more than one finding in the same pass, precede the individual readouts
with a one-line summary table so the reviewer can triage at a glance:

```markdown
| Finding | Evidence strength | Matches its evidence | Checks that fired | Checks that didn't run | Safe to act on |
|---|---|---|---|---|---|
| [short label] | [STRONG, UNCERTAIN or WEAK] | [Yes or No] | [IDs, or "none"] | [IDs, or "none"] | [Yes or Not yet] |
```
