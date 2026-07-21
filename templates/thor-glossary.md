# Glossary (thor-glossary.md)

Read role and rules: [Glossary](thor-document-rules.md#glossary).

Project-wide. There is exactly one glossary per project, not one per topic, so
different topics cannot invent rival terms for the same idea.

Canonical project vocabulary. Agents tend to coin compact terms for token
efficiency; without a shared glossary those meanings drift. Define recurring
terms here, and use glossary terms consistently in code, study notes, plots, and
artifacts across every topic.

Rules:

- Define terms that recur, affect interpretation, or appear in artifacts.
- Define process terms that affect verdicts, phase order, or document updates.
- Prefer stable definitions over chronology or planning.
- Do not create near-synonyms; if a synonym is unavoidable, alias it to the canonical term.
- In reader-facing docs, link glossary terms on first important use.
- Multi-topic projects share this one file.

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

An independent adversarial review in a separate thread. The pre-launch gate audits the study plan before execution. The post-result gate audits interpretation, verdict, and prediction scoring before conjecture updates or agenda reranking.

### `streak`

A repeated pattern in prediction scoring, such as several consecutive `refuted` or `untouched` predictions. A stale streak is a signal to revisit the conjecture frame after the post-result skeptic gate.

### `study`

One planned experiment or audit with a study note. A study contains pre-run sections, amendments, run record, results, interpretation, prediction scoring, skeptic reviews, limitations, doc updates, and next read.

### `thread`

A separate agent conversation or execution context. Thor uses separate threads for the working phase and skeptic phases so in-memory context cannot bleed across planning, review, interpretation, and document updates.

## Project Terms

### `<term>`

`<plain-English definition a newcomer or fresh agent can understand>`

### `<term>`

`<definition>`
