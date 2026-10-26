# Checks CK-01 to CK-06

Six checks that audit each claim against what the team declared up front: the
belief register ([templates/belief-register.md](../templates/belief-register.md)) and
the study record ([templates/study-record.md](../templates/study-record.md)). They add
to the pitfalls in [pitfalls.md](pitfalls.md); they don't replace them.

## Contents

- The checks
- When a check can run
- Clarification: agreement is attributed opinion (CK-01)
- Worked examples, one that fires and one that stays clear, for each check

---

## The checks

Each check runs on the claims under review, together with the declared records. Every check has three possible results: **FIRES**, **CLEAR** or **NOT RUN** (input missing). A fired check names the triggering text and the declared item it conflicts with.

The **user-facing wording** below is what the readout shows.

**People-side evidence** (referenced under CK-04): any evidence unit describing what
people did, said, needed or experienced, including observed behaviour in usability
sessions. Stakeholder or designer opinion does not count.

| ID | Needs | Fires when | Does not fire when | User-facing wording |
|---|---|---|---|---|
| CK-01 Borrowed conviction | belief register (claims alone for part b) | (a) A claim restates or depends on a belief rated `high` whose source is `authority`, `proxy` or `own_experience`, and the claim cites no evidence unit that supports it. (b) A claim's support is an attributed opinion ("the PM says", "our founder believes", "stakeholders agree") rather than evidence from participants | The high-confidence belief is backed by `internal_research` or `third_party_study` with a `source_ref`; or the authority is mentioned only as context and the claim cites evidence units | "This confidence comes from who said it, not from evidence." |
| CK-02 Beyond declared limits | study record `limits` | A claim covers a population, context, method or output listed under `limits.cannot_claim` (e.g. the sample cut bank managers, but a claim states what lenders think; the study was remote-only, but a claim describes home routines as observed) | The claim stays within limits, or is explicitly labelled as a hypothesis for a future study | "This claims more than the study was designed to show." |
| CK-03 People treated as validated | claims | A claim about **people** (behaviour, need, attitude, feeling) is presented as validated, confirmed or proven; or participants are judged ("good users", "bad participants") | A **product** is checked against a standard ("4 of 5 participants completed checkout") | "This treats what we learned about people as proven. Only a product can be validated." |
| CK-04 Product finding without a human story | belief register (for agreed assumptions) | A claim about the **product** (a design should do X, feature Y works) cites no people-side evidence (see definition above) **and** rests on no belief with `agreed_by_all = yes` | Either people-side evidence or an agreed assumption is present | "This product finding has no evidence about people behind it, and no assumption the team agreed to." |
| CK-05 Scope and certainty inflation | claims + evidence | The claim's scope is wider than its evidence (3 interviewees become "users"), or its certainty is stronger than the evidence type allows (one signal becomes "the cause", a hope becomes "will") | Calibrated wording ("3 of 8 participants", "likely", "in this sample") | "This says more, or says it more surely, than the evidence allows." |
| CK-06 Drift | study record `questions` | A claim answers none of the declared questions and isn't labelled as an unexpected finding | It maps to at least one question, or is labelled "unexpected finding (not asked)" | "This insight doesn't answer any question the team asked." |

**Relationship to the existing pitfalls (P-01 to P-08).** The CK checks add to the pitfalls; they don't replace them.
- CK-05 overlaps P-01 (headline generality). When both fire, report both, with CK-05 naming the scope or certainty gap.

---

## When a check can run

A check that didn't run is never reported as passed. Treat a record that says "none
declared", a record with only a header, a blank field, or a value the template doesn't
allow (such as confidence "medium") as missing.

| Check | Can report CLEAR only when | Otherwise, when its input is missing |
|---|---|---|
| CK-01 | A belief register is declared, the beliefs the claim relies on have `confidence` and `source_type` filled in (and a `source_ref` where the source is research), and neither part fires | FIRES if part (b) fires on the claim alone; NOT RUN if it doesn't, because part (a) couldn't run |
| CK-02 | The study record declares at least one limit, every declared limit has a `cannot_claim`, and the claim stays inside every one | FIRES if the claim crosses a limit whose `cannot_claim` is filled in; otherwise NOT RUN, naming the limits with no `cannot_claim` |
| CK-03 | Always runs: it needs only the claim | — |
| CK-04 | The claim cites people-side evidence (no register needed), **or** the register is declared and a belief the claim rests on has `agreed_by_all = yes` | With no people-side evidence: FIRES if the register is declared and no agreed belief supports the claim; NOT RUN if there is no register, or `agreed_by_all` is blank on the beliefs the claim rests on |
| CK-05 | Evidence was supplied, and the claim's scope and certainty stay within it | NOT RUN if no evidence was supplied at all (the provenance table marks the claim untraceable) |
| CK-06 | The study record declares at least one question, and the claim maps to one or is labelled "unexpected finding (not asked)" | NOT RUN — including when the claim maps to none of the written questions but a declared question has no text |

A check fires on whatever part of its input it can see. CLEAR needs all of it. When
unsure between CLEAR and NOT RUN, report NOT RUN, and name what's missing.

CK-04's boundary: people-side evidence makes it CLEAR with or without a belief
register; with no people-side evidence and no register, it is NOT RUN, never CLEAR.

"Claim matches its evidence" is No whenever CK-01 to CK-05 fires or P-01, P-04, P-05,
P-06, P-07 or P-08 is triggered; P-02 and P-03 leave it open, but a "Yes" to act on
must say why they don't weaken the decision.

When a check fires, the readout's "What triggered it" cell starts with the check's
user-facing wording from the table above, then quotes the triggering text.

Name declared items by the IDs the user gave them (B-01, Q-02). Limits have no IDs:
quote the limit's `cannot_claim` instead. Never invent an ID.

---

## Clarification: agreement is attributed opinion (CK-01)

"Stakeholders confirmed it", "the team agreed", "leadership signed off" and "no one
objected" count as attributed opinion under CK-01 part (b). Not being rejected is not
confirmation.

This sits alongside CK-04 as follows:
- A belief with `agreed_by_all = yes`, presented as a **declared working assumption**
  ("Working assumption B-04, agreed by the whole team: …"), keeps CK-04 clear and does
  not fire CK-01.
- Team agreement presented as **evidence for a claim about people** ("Visitors want
  shorter clips — the team agreed in the review") fires CK-01 part (b).

---

## Worked examples

All examples use a museum's audio-guide app. They're illustrations, not a test set.

### CK-01 Borrowed conviction

Belief register: `B-02 | Visitors want shorter audio clips. | people | high | Our
director says nobody listens past a minute. | authority | | no | Lee: the long
tracks get the best feedback.`

- **Fires.** "Visitors want clips under a minute, so we'll cut every track to 60
  seconds." It restates B-02, a high-confidence belief whose source is authority, and
  cites no evidence. *Conflicts with:* B-02.
- **Fires (part b).** "Stakeholders confirmed that visitors want shorter clips." The
  support is who agreed, not what visitors did.
- **Clear.** "In 5 of 8 sessions, participants skipped tracks after about a minute
  (INT-01, INT-03, INT-04, INT-06, INT-08); our director had expected this." The
  director is context; the claim rests on cited evidence.

### CK-02 Beyond declared limits

Study record limit: `sample · what was cut: school groups · cannot claim: how
teachers or school groups use the guide.`

- **Fires.** "Teachers find the guide too slow to use with a class." *Conflicts
  with:* the sample limit (no school groups).
- **Clear.** "Adult visitors in this sample found the guide quick to start." Or:
  "Hypothesis for a future study: teachers may find the guide too slow for a class."

### CK-03 People treated as validated

- **Fires.** "The sessions confirmed that visitors feel lost without a map." A feeling
  is presented as proven.
- **Clear.** "6 of 8 participants started a tour without help." The product is
  checked against a standard.

### CK-04 Product finding without a human story

Belief register declared; no belief about the 'next stop' button has
`agreed_by_all = yes`.

- **Fires.** "The 'next stop' button should move to the bottom of the screen." No
  evidence about what visitors did, and no agreed assumption behind it.
- **Clear.** "The 'next stop' button should move to the bottom of the screen: in
  INT-02 and INT-05, participants reached for the bottom edge twice before finding it
  at the top."

### CK-05 Scope and certainty inflation

Evidence: two of eight participants said the audio was hard to hear in the main hall.

- **Fires.** "The audio is too quiet for visitors." Two participants in one room
  become all visitors everywhere.
- **Clear.** "2 of 8 participants found the audio hard to hear in the main hall."

### CK-06 Drift

Study record questions: `Q-01 · How do visitors choose a tour?` and `Q-02 · Can
visitors replay a track without help?`

- **Fires.** "Visitors want the guide in more languages." It answers neither question
  and isn't labelled as unexpected. *Conflicts with:* Q-01, Q-02.
- **Clear.** "Unexpected finding (not asked): two participants asked whether the guide
  came in Spanish; worth a question in the next round."
