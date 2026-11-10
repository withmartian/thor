# Study: <name> (thor-study-<name>.md)

Read role and rules: [Study Notes](thor-document-rules.md#study-notes).

Status: pre-launch · last changed `<YYYY-MM-DD>`

Tier: gated · review policy: [Experiment Tiers](thor-agent.md#experiment-tiers)

Use this full form for a gated study. Use a shorter record only where the active
agent contract defines one; choose the form before results. Complete pre-run
sections before implementation or launch, with required pre-launch review resolved
before execution. State competing reads neutrally rather than advocating for a
preferred answer.

Copy to the study path in the active contract and name it `<topic>-study-<name>.md`.
For `docs/study-<topic>/`, change links to shared docs to `../thor-document-rules.md`
and the review-policy link to `../<topic>-agent.md#experiment-tiers` (or its canonical
project-wide location). Adjust again for deeper folders, then remove these setup instructions.

On completion, use:
`Status: complete · <outcome> (unreviewed) · ~$<cloud cost> · last changed <YYYY-MM-DD>`.
Remove `(unreviewed)` after required post-result review passes. A review exemption
is `not required` with a policy reference, never a claimed review pass.

## Executive summary

*Before results, omit this section or state `Awaiting results`. During result
recording, write a few sentences stating the finding, scope and key caveat; mark
them `unreviewed` while required review is pending, then refresh after review.
State nulls and inadequate sensitivity explicitly rather than judging whether a
result is interesting. Full rules:
[Executive Summary](thor-document-rules.md#executive-summary).*

`<what this study found, and the caveat a skim reader needs>`

`<optional: one plot carrying the main result, with a caption that states the
takeaway rather than the axes. Omit when no single plot honestly conveys the finding>`

## Pre-run (write before the experiment)

- **Question**: `<the specific empirical question>`
- **Motivation**: `<why this matters now, and the end goal it advances>`
- **Hypothesis / competing reads**: `<the live beliefs this result can distinguish, phrased neutrally>`
- **Design**: `<data, intervention, controls, metrics, sample sizes, scope.
  State the minimal effect of interest and whether the sample sizes can detect
  it; if they cannot, say so before the run>`
- **Positive control**: `<name the known-positive manipulation, pass criterion
  and check/output that will establish whether the metric can move. A flat
  result with a failed control is invalid/underpowered, never negative>`
- **Success condition**: `<result that counts as positive — defined now>`
- **Failure condition**: `<result that counts as negative — defined now.
  A negative verdict requires a passing positive control and detectable-effect
  sample sizes>`
- **Ambiguous / invalid condition**: `<what would make the run inconclusive or void>`
- **Cost estimate**: `<estimated cloud cost in dollars to complete the study, or unknown>`
- **Probability of success**: `<estimated chance of a positive or negative finding that guides
  the next steps, or unknown>`
- **Skeptic review (pre-launch)**: `<reviewer/context, reviewed source references,
  findings and resolution before launch; link the actual review. Keep pending
  until reviewed, or state not required with the policy reference>`
- **Decision impact**: `<what each outcome would change in the docs>`
- **Risks / confounds**: `<likely failure modes, missing controls>`
- **Expected artifacts**: `<files, plots, logs, and where they will land>`

## Post-run (fill in after the experiment)

- **Executive summary**: `<written at the top of this note, not here — see the
  section above. Refresh it after required post-result review>`
- **Run record**: `<command, environment, dates, artifact paths, source revision/hash;
  account for completed, failed, incomplete and missing runs>`
- **Results**: `<key quantitative and qualitative results, including observed
  control outcomes and links to the outputs supporting the verdict>`
- **Interpretation**: `<read against the pre-stated success/failure/ambiguous
  conditions — do NOT move the goalposts; add an explicit amendment if criteria
  must change>`
- **Prediction scoring**: `<score each standing conjecture-file prediction this
  result bears on: confirmed / refuted / untouched. Say so explicitly if none
  apply. This records evidence; it does not update conjectures by itself>`
- **Skeptic review (post-result)**: `<reviewer/context, reviewed source references,
  findings and resolution for interpretation, verdict and prediction scoring;
  link the actual review. State not required only with the policy reference>`
- **Limitations**: `<what this does not show>`
- **Doc updates**: `<affected docs in the canonical update order, after required
  review; human-owned conjecture revisions are proposals to the owner>`
- **Next read**: `<frozen / reopen / replicate / different assay?>`
