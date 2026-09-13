# QA Readout Template

Fill in every section for each finding under review. Keep the structure — it's what
makes the readout auditable — but write in plain language, not telegraphic labels.
If a section genuinely doesn't apply (e.g. no transfer claim is being made), say so
explicitly rather than deleting it; a silently-skipped section is indistinguishable
from a forgotten one.

```markdown
## Finding: [state the conclusion under review, verbatim, unedited]

**Evidence strength: STRONG / UNCERTAIN / WEAK**
[One sentence, plain language, stating the verdict as you'd say it to a stakeholder —
not a hedge, a position.]

### Provenance
| Claim | Source | Observed or inferred | Traceable? |
|---|---|---|---|
| [specific claim in the finding] | [quote, excerpt, or "not cited"] | Observed / Inferred | Yes / No — [why not, if no] |

State explicitly if any claim in the finding has no supporting evidence at all —
don't let it pass silently because the rest of the row looks fine.

### Falsification pass
- **Strongest counter-hypothesis:** [the best alternative explanation for the same
  evidence — not a token objection, the one that would actually worry you]
- **What would overturn this finding:** [a specific, checkable piece of evidence —
  not "more data" but the actual data]
- **Where the evidence underdetermines the claim:** [name the specific gap, if any —
  or state that the evidence base is unusually complete for this claim]

### Pitfalls checked
Run every finding against `references/pitfalls.md`. List only the ones that fire —
cite the pitfall code, name what triggered it, and what fixing it would look like.
If none fire, say so and say why (what makes this finding specific/well-evidenced
enough to clear all eight).

| Pitfall | Triggered? | What triggered it |
|---|---|---|
| P-01 Headline Generality | Yes/No | |
| P-02 Context Blindness | Yes/No | |
| P-03 Transcript Literalism | Yes/No | |
| P-04 Volume Mistaken for Strength | Yes/No | |
| P-05 Counter-Evidence Filed, Not Faced | Yes/No | |
| P-06 Formulaic Transfer Hedge | Yes/No | |
| P-07 Trust Without Process | Yes/No | |
| P-08 Narrowing Sold as Resolving | Yes/No | |

### What would change this verdict
[The single most useful next piece of evidence someone could go get. Not a wish
list — the one thing that would move this from UNCERTAIN to settled, or from
apparently-STRONG to revealed-as-WEAK.]

### Tacit-knowledge prompt (optional — ask only if a researcher who ran the sessions is available)
[A specific question tied to the actual ambiguity above — not "anything else to
add?" Anchor it to the exact moment or contradiction that's unresolved.]
```

## Rolling up multiple findings

When QA-ing more than one finding in the same pass, precede the individual readouts
with a one-line summary table so the reviewer can triage at a glance:

```markdown
| Finding | Evidence strength | Pitfalls triggered |
|---|---|---|
| [short label] | STRONG / UNCERTAIN / WEAK | [codes, or "none"] |
```
