# ux-research-qa

**A Claude Skill that red-teams AI-generated UX research before its conclusions reach
a roadmap.**

## The failure this catches

Ask an LLM to synthesise user research and it will hand you a confident verdict, a
cited evidence list, and — if the finding touches a market or population outside the
data — a caveat like:

> *"This finding may not fully transfer to EU users."*

That sentence sounds like rigour. It isn't. In testing across **four frontier models**
run against the same evidence corpus, all four produced some version of that exact
hedge, and *none of them argued it* — no named difference between the populations, no
assessment of whether that difference actually matters, no statement of what evidence
would resolve the question. The caveat was decoration. The verdict underneath it was
unchanged, and a researcher skimming the output would read the hedge as due diligence
rather than what it actually was: an unexamined assumption wearing the costume of one.

That's the general shape of the problem this skill exists for. Not hallucination —
research synthesis tools are usually working from real evidence. The failure is
**unearned confidence**: a plausible-sounding conclusion that outruns what the
evidence in front of it actually supports, in ways that are individually easy to miss
and collectively expensive. A team that inherits a mis-framed finding doesn't get a
bad paragraph — it gets months spent on the wrong engineering workstream.

## What it does

This skill runs a QA pass on research synthesis — findings, personas, themes,
verdicts — rather than producing new research. Point it at a conclusion and the
evidence behind it, and it will:

1. **Trace provenance** — check every claim against the evidence, and flag anything
   asserted with no evidence behind it.
2. **Attempt falsification** — argue against each conclusion before accepting it,
   and name what evidence would actually overturn it.
3. **Screen for eight recurring reasoning pitfalls** — including the formulaic-hedge
   failure above, mistaking evidence volume for evidence strength, and treating a
   narrowed hypothesis as a solved problem. See
   [`references/pitfalls.md`](references/pitfalls.md).
4. **Produce a confidence-tiered readout** — STRONG / UNCERTAIN / WEAK, per finding,
   with what would change the verdict. See [`templates/readout.md`](templates/readout.md).

It evaluates reasoning. It does not generate new insight, plan studies, or write
discussion guides — see [`SKILL.md`](SKILL.md) for the full workflow and scope.

## Before / after

**Before (typical AI-generated synthesis):**

> *Users report forecast inaccuracy as a top complaint. This finding may not fully
> transfer to EU markets. Recommend investing in forecast model accuracy to address
> the trust gap.*

**After this skill's QA pass:**

> **Evidence strength: UNCERTAIN.** The "inaccuracy" framing is not well-supported —
> one cited review (R03) explicitly defends forecast accuracy while describing the
> same underlying failure others attribute to inaccuracy, which suggests a data
> freshness or caching issue rather than a model problem (**P-01 Headline
> Generality**, **P-05 Counter-Evidence Filed, Not Faced** — R03 was listed as a
> counter-signal but never argued against). The EU-transfer caveat is unexamined: no
> structural difference between US and EU users is named, and none of the cited
> evidence includes EU users at all (**P-06 Formulaic Transfer Hedge**). The decision
> support overreaches — the evidence narrows where to look, it doesn't validate that
> forecast-model investment will fix anything (**P-08 Narrowing Sold as Resolving**).
> **What would change this verdict:** telemetry on cache-hit rates during the
> reported failure moments, and any EU-market evidence at all.

Same underlying data. Very different roadmap.

## Install

**Claude Code** — clone directly into your skills directory:

```bash
git clone https://github.com/wedoux/ux-research-qa.git ~/.claude/skills/ux-research-qa
```

(Use `.claude/skills/` inside a specific project instead of `~/.claude/skills/` to
scope it to that project only.)

**claude.ai** — download this repo as a zip and upload it under
`Settings > Features > Skills` (requires code execution enabled on your plan).

Once installed, just ask naturally — "can you sanity-check these findings?", "red-team
this research readout," "are these personas actually supported by the data?" — and
Claude will pull in the skill. You can also invoke `ux-research-qa` explicitly.

## The fuller system

This skill distills the reasoning discipline from
**[SprintZero](https://github.com/wedoux/sprintzero)** — a two-agent research-QA
application with live evidence retrieval, a structured evidence registry, and an
adversarial second agent that can block a verdict outright. This skill carries the
brain: the falsification discipline, the pitfalls taxonomy, the provenance rules.
SprintZero is the body: the infrastructure that runs this discipline continuously
against a growing evidence base, with a UI built around showing its work. If this
skill is useful for a single QA pass, SprintZero is the next step up for running this
process as part of an ongoing research practice.

## License

[MIT](LICENSE)
