# Glossary (thor-glossary.md)

Read role and rules: [Glossary](thor-document-rules.md#glossary).

Project-wide. There is exactly one glossary per project, not one per topic, so
different topics cannot invent rival terms for the same idea.

Canonical project vocabulary. Agents tend to coin compact terms for token
efficiency; without a shared glossary those meanings drift. Define recurring
terms here, and use glossary terms consistently in code, study notes, plots, and
artifacts across every topic.

Follow [Terminology Discipline](thor-document-rules.md#terminology-discipline).
Keep definitions here and operating requirements in the agent contract or
Document Rules, so the glossary does not become a second policy manual.

## Process Terms

### `agenda`

The ranked, current-facing list of planned next experiments for a topic. The agenda is not a history log; completed entries are deleted during post-run reranking and recorded in the study note and results ledger.

### `assay`

The concrete measurement harness used by a study: data, intervention or manipulation, controls, metrics, and verdict criteria. A failed assay can make a result `invalid` or cause an `instrument failure` freeze even when the scientific question remains live.

### `claim`

A durable empirical statement in the claim-evidence map, with linked evidence, confidence, and caveats. Claims are fewer than studies and should not be speculative.

### `conjecture doc`

A document containing speculative beliefs, priors, predictions, falsifiers, and alternatives. Conjecture docs are allowed to disagree with each other and must not be used as empirical evidence.

### `empirical doc`

A document whose job is to record observations, results, evidence, claims, artifacts, or current empirical synthesis. Study notes, results summaries, results synthesis, results ledgers, and claim-evidence maps are empirical docs.

### `freeze decision`

A documented decision to stop or pause an experiment line. Each freeze decision is classified as `question answered`, `question failure`, or `instrument failure`, and includes reopen conditions.

### `instrument failure`

A freeze classification where the assay class, unit of intervention, metric, data, or harness was the limiting factor. This triggers the outside-view sweep required by the agent contract.

### `question answered`

A freeze classification where the study line has answered the intended question well enough under its stated scope.

### `question failure`

A freeze classification where the question was ill-posed, unanswerable as stated, or no longer maps cleanly to a useful experiment.

### `skeptic gate`

An adversarial review in a separate agent context, using declared docs and artifacts
rather than the working session's conversation. The pre-launch gate audits the plan;
the post-result gate audits interpretation, verdict and prediction scoring. Gate
applicability comes from the active agent contract; review mechanics live in
[Skeptic Gates](thor-document-rules.md#skeptic-gates).

### `streak`

A repeated pattern in prediction scoring, such as several consecutive `refuted`
or `untouched` predictions, that may indicate a stale conjecture frame. Belief
updates follow the active contract's review policy.

### `study`

One planned experiment or research audit and its record. Its tier determines the
record's form and required reviews; see [Study Notes](thor-document-rules.md#study-notes).
An exploratory run can use the lighter record defined in the agent contract.

### `thread`

A research topic with its own scope, contract, agenda and evidence docs, as listed
in the project's thread registry. A topic may have several workstreams and agent
sessions; the topic name does not establish ownership of another agent's work.

### `agent session`

One agent conversation or execution context. A skeptic needs a separate review
context from the working session; changing roles within one conversation does
not isolate its context.

### `workstream`

An owned unit of work within a topic, with identified files, resources and source
state. Several workstreams can share a topic without sharing edit or resource
ownership.

### `tier`

A pre-run classification specifying cost/resource limits, required records,
reviews and permitted result uses. The active agent contract is authoritative;
the portable defaults distinguish exploratory runs from gated studies.

### `unreviewed`

A result or interpretation that has not passed post-result skeptic review.
Permitted uses depend on the tier policy. It is a review state, not a confidence
level or a substitute for reporting the measured result plainly.

## Project Terms

### `<term>`

`<plain-English definition a newcomer or fresh agent can understand>`

### `<term>`

`<definition>`
