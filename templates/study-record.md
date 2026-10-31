# Study record (lite)

**What this is for.** Write down what the study was for, what it asked, and what it
gave up. The QA pass checks your findings against this record: does each one answer a
question you asked, and does it stay inside what the study can show?

**How to fill it in**
- **Write your own.** The people who planned the study fill this in. This skill won't
  draft it — it may ask questions that help.
- **Decision informed:** the decision this research is meant to help someone make. If
  you can't name one, say so.
- **Questions:** what you set out to learn, one per line, each with who asked it and
  whether it's about `people` (how users live, act or feel) or the `product`. A finding
  that answers none of these isn't wrong, but it should be labelled "unexpected
  finding (not asked)".
- **Evidence sources:** what was gathered — method, number of participants, and the
  prefixes used to label each piece of evidence (R reviews, INT interviews, SV
  surveys, TK tickets).
- **Limits:** every study gives something up — time, budget, who you could reach. For
  each one, say which part of the study it affected (`objective`, `sample`, `method`
  or `output`), what was cut, and, in plain words, **what you can no longer claim**
  because of it. This is the line the QA pass holds findings to.

Leave a field blank rather than guess. A record with no limits or no questions means
the checks that need them are reported as not run, never as passed.

```markdown
study_name:
decision_informed:
questions:
- Q-01 · [question] · [author] · [people / product]
evidence_sources:
limits:
- [component] · what was cut: [ ] · cannot claim: [ ]
```

**Example — delete before use:**

```markdown
study_name: Holds and collection check-in
decision_informed: Whether to rebuild the reserve-and-collect flow this quarter.
questions:
- Q-01 · How do members decide which branch to collect a reserved book from? · Sam (designer) · people
- Q-02 · Can members change their collection branch without help? · Priya (product manager) · product
evidence_sources: 6 remote moderated sessions (INT-01 to INT-06); 40 app store reviews (R-01 to R-40).
limits:
- sample · what was cut: members over 70 (recruited through the app only) · cannot claim: how older members, or members who don't use the app, collect books.
- method · what was cut: in-branch observation (remote sessions only) · cannot claim: what members do at the collection desk.
```
