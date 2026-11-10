# Document Rules (thor-document-rules.md)

Read role and rules: [Document Rules](#document-rules-thor-document-rulesmd).

Project-wide. One per repo, not one per topic. This is the portable document
contract for research repos that use the Thor doc structure. It defines each
document's job, the update workflow, and the anti-drift rules.

Project-specific or topic-specific docs link to the relevant role here
instead of repeating these rules.

## Role Catalog

These are document roles. A repo may have multiple topics, multiple summaries,
or prefixed filenames. Put the concrete file mapping, including the default
study-note location, in the topic-specific agent contract.

| Role | Purpose | Scope |
| --- | --- | --- |
| Agent Contract | Operating contract and rehydration entry point; a multi-topic repo also has a shared router. | per-topic, plus repo-wide router as needed |
| Document Rules | This file: document roles, update workflow, terminology discipline, and anti-patterns. | project-wide |
| Glossary | Canonical project vocabulary. | project-wide |
| Results Summary | Compact current-state synthesis. | per-topic |
| Results Synthesis | Mid-level empirical synthesis for a primary results theme. | per-topic or topic-index |
| Results Ledger | Append-only chronological record of completed result bundles. | per-topic |
| Claim-Evidence Map | Durable empirical claims and the evidence/caveats attached to them. | per-topic |
| Experiment Agenda | Ranked, current-facing planned next experiments. | per-topic |
| Conjectures | Human-owned or agent-owned speculative beliefs and predictions. | per-topic, owner-specific |
| Study Notes | Individual study plans, methods, artifacts, results, interpretation, skeptic gates, and immediate next read. | per-study |

## Terminology Discipline

- Use stable project vocabulary from `thor-glossary.md`.
- Define terms that recur, affect interpretation, appear in artifacts, or could drift across threads before spreading them through docs, code, plots, or artifact names.
- In reader-facing docs, link project-specific glossary terms on first important use and use plain English when a term would make prose opaque.
- Do not create near-synonyms for existing terms. If a synonym is unavoidable, add it as an alias to the canonical glossary term.
- Define terms that shape process or verdicts. At minimum: `assay`, `study`, `skeptic gate`, `freeze decision`, `agenda`, `streak`, `empirical doc`, `conjecture doc`, `claim`, `thread`, `agent session`, and `workstream`.
- Do not let agent-defined jargon drift without a glossary entry.

## General Rules

- Keep empirical docs separate from conjecture docs.
- Prefer current-state language in synthesis docs and chronological language only in ledgers or study notes.
- Keep claims fewer than experiments.
- Link out instead of duplicating long evidence, artifact trails, or update rules.
- Start each concrete doc with a one-line role pointer to this file:
  `Read role and rules: [Role](thor-document-rules.md#role-anchor).`
  Resolve the path from the document's actual directory: a note in `study-<topic>/`
  uses `../thor-document-rules.md`; a note one level deeper uses `../../thor-document-rules.md`.
- Clarify a document's purpose with its role pointer rather than a copied rule block.
- Record enough context for a fresh agent or skeptic to rehydrate without a previous session's memory.

### Writing Operating Instructions

- Start obligations with a direct action, its object and its timing or scope.
  “Record every completed bundle in the ledger” is clearer than describing what
  a good ledger might contain.
- Preserve real conditions and exceptions. Use scoped headings or decision tables
  for branching workflows; replacing `if` with `when` alone does not improve a rule.
- Distinguish requirements, permissions and preferences. Keep “Prefer” for advice
  and “may” for permission; keep explicit prohibitions for ownership and other boundaries.
- Give each policy one canonical home. Link to it and state scoped overrides
  explicitly. Resolve conflicting rules before rewriting their sentences.
- Add a brief reason when it explains a non-obvious failure mode. Reasons are not
  required on every instruction.
- Name observable completion evidence: a study section, artifact field, command
  result or diff. Describe only what a check actually proves. A checked box or
  self-reported pass does not replace its evidence.
- Keep that evidence in the existing study or run record; add no separate receipt
  or approval step merely to prove that an instruction was read.

## Thread Isolation And Phase Boundaries

Thor uses separate work phases to prevent conjectures, private reasoning, or stale in-memory context from bleeding into empirical records. A research thread is a topic; reviewer independence requires a separate conversation/context, not merely a different role in the same conversation.

Select the applicable tier and study form from the agent contract before launch.
For gated studies, use this order and perform the reviews that tier requires:

1. **Plan**: rehydrate from docs, select ranked unblocked work, and complete the study note's pre-run sections.
2. **Pre-launch review**: have a skeptic in a separate context read the declared version-controlled docs and artifacts and audit the plan. Record findings and resolutions before launch.
3. **Execute**: resolve or explicitly overrule blocking review concerns in the study note, then run and monitor within the approved resources.
4. **Record results**: sync artifacts and complete the run record, results, interpretation, limitations and prediction scoring. Write the executive summary, marked `unreviewed` while a required post-result review is pending.
5. **Post-result review**: have a skeptic in a separate context audit interpretation, verdict and prediction scoring. Resolve or explicitly overrule blocking concerns in the study note.
6. **Update router docs**: after required reviews pass, refresh the executive summary and follow [Router-Doc Update Order](#router-doc-update-order).
7. **Audit**: compare changed docs for duplicated detail, conjecture bleed, stale agenda entries, conflicting policy and terminology drift before stopping.

Exploratory runs use the lightweight record and permitted result uses in the agent
contract. They may guide the next experiment without a skeptic gate. Keep their
observations traceable and labelled `exploratory / unreviewed`; do not promote
them into reviewed findings.

Prediction scoring records evidence in the study note; it does not itself revise
conjectures. Under the default policy, gated results update conjectures, claims
and agenda rankings only after post-result review. Exploratory agenda changes are
the explicit exception. Projects with other provisional-update rules state them
in the agent contract, including which uses still require review.

## Evidence And Verdict Rules

- Include a known-positive control in every new assay to demonstrate that its metric can move under this harness. Record the observed control result, not just its planned presence.
- State the minimal effect of interest and whether the sample sizes can detect it before running the study. State inadequate sensitivity explicitly.
- Assign `negative` only with a passing positive control and enough sensitivity to detect the stated effect. Otherwise use the applicable `ambiguous`, `underpowered` or `invalid` verdict; a flat result with a failed positive control is never `negative`.
- Record missing, failed and incomplete runs as such. Missing artifacts are not evidence of success or zero failures.
- Score each standing conjecture-file prediction a completed study bears on as `confirmed`, `refuted` or `untouched`. State explicitly when none apply.
- Record a streak of refuted or untouched predictions in the agent conjecture file after the required post-result gate. Propose changes to human conjectures to their owner. A stale streak is a reason to revisit the frame.
- Every freeze decision classifies itself as `question answered`, `question failure`, or `instrument failure`.
- `question answered` means the study line has answered the intended question well enough under its stated scope.
- `question failure` means the question was ill-posed or unanswerable as stated.
- `instrument failure` means the assay class, unit of intervention, metric, data, or harness was the limiting factor. It triggers the outside-view sweep defined in the agent contract.

## Proportionate Process

Process exists to make results trustworthy. A step that protects no result is removed. A project that
prefers speed says so in its agent contract, and that preference governs older, stricter wording.

- **Match gates to stakes.** Exploratory work runs at the project's lowest cost tier, without gates,
  within its configured limit, and may guide the next run. Rerun at a gated tier before a claim,
  conjecture update, cross-thread evidence handoff or freeze rests on it. The agent contract
  defines the tier boundaries and any scoped overrides.
- **Each gate is one review.** Inside an approved budget, add no separate receiving reviews,
  acknowledgements, finance acceptances or admission records.
- **Bound runs by cost and the cloud stop, not by internal clocks.** Missing a self-set time window
  is not a reason to refuse.
- **Fix and continue.** A refusal from the team's own bookkeeping or guards is a defect to repair
  within the same budget, not a new approval round. Only a budget breach, a failed control the
  verdict depends on, or a safety guardrail stops a run.
- **Size a run to settle its question.** Prefer one decisive run to several narrow ones.
- **Record what rebuilding the result needs.** Do not keep readiness, dispatch or accounting receipts
  as separate records.

## Skeptic Gates

Role: independent adversarial review at the points required by the agent contract's tier policy. The portable default is two gates for gated studies and none for configured exploratory work.

Rules:

- Run the skeptic in a separate review context that reads the declared version-controlled docs and artifacts: the study note, relevant conjectures, document rules and supporting evidence. It must not inherit the working session's live or compacted conversation.
- This keeps review independent of the author's framing and continuously tests whether docs are self-sufficient for rehydration.
- A different model or vendor is encouraged but not required; a separate context is required. A self-check in the working session does not pass a gate.
- Gate 1, pre-launch: before an experiment launches, the skeptic audits the study-note pre-run sections. Is the positive control real? Is the minimal-effect and power statement honest? Does the success condition discriminate live conjectures rather than admit a gameable pass? Are controls adequate?
- Gate 2, post-result: audit interpretation, verdict and prediction scoring before using gated results in router-doc updates. Is the verdict over-claimed? Is `invalid` or `ambiguous` dodging a supported verdict? Is prediction scoring generous? Apply any explicit provisional-use exception from the agent contract.
- Blocking concerns must be resolved before passing the gate, or explicitly overruled with a one-line written justification in the study note.
- The working thread owns the final call; unresolved disagreement is recorded, not hidden.
- Record the reviewer/context, reviewed source references, findings and resolution in the study note's Skeptic Review sections. Keep the actual review or a durable link to it; a bare `passed` checkbox is insufficient.
- An overrule records a decision, not a changed measurement. A failed control still limits the verdict under [Evidence And Verdict Rules](#evidence-and-verdict-rules).

## Agent Contract

Role: topic-specific operating contract for autonomous agents.

Rules:

- Keep project configuration, rehydration steps, tier boundaries and review applicability, infrastructure workflow, autonomy limits, document mapping, thread names, and cleanup permissions here.
- Link to this document for portable document structure and terminology rules.
- Do not use the agent contract as the results summary, results ledger, or claim map.
- Update when process, guardrails, infrastructure, autonomy limits, or operating workflow changes.

## Results Summary

Role: compact current-state synthesis.

Use it to orient a human or agent quickly to:

- the current best empirical story
- the most important and insightful claims
- the strongest live caveats
- weak, stale, or mostly exhausted lines
- open questions that should shape near-term experiment choice

Rules:

- Include an executive summary.
- Cover only the current top claims, not all claims and not all experiments.
- Prefer current-state language over historical process language.
- Remove stale rejected frames instead of preserving them as findings.
- Link outward to the claim-evidence map, results synthesis, results ledger, and agenda for detail.
- Update only when a result changes the current story.
- Use at most a few anchor numbers, only when they change the present-state read.
- Prefer claim labels, role labels, and links over experiment, bundle, or artifact lists.
- If a paragraph names several runs, bundles, cells, metrics, or controls, move the detail to results synthesis, claim-evidence, a study note, or the ledger.

## Results Synthesis

Role: mid-level empirical synthesis for a primary results theme.

Use it to answer:

- which findings in the primary empirical line currently matter
- which figures are decision-relevant rather than merely recorded
- which caveats should constrain the next experiment
- where the story is strong, weak, or still ambiguous

Rules:

- Organize by empirical question, not by experiment chronology.
- Keep only figures that change interpretation or priority.
- Include qualitative reads for table rows, such as `strong`, `modest`, `negative`, `control-sensitive`, `method caveat`, or `decision-critical`.
- Do not duplicate the ranked experiment agenda or the claim-evidence map.
- Update when results change the synthesis, even if they do not yet justify a durable claim.
- If a repo accumulates multiple large empirical themes, keep the results synthesis doc as the integrative synthesis or index and move detailed theme-specific material into theme-specific synthesis docs.
- This is the normal home for detailed mechanism interpretation that would overload the results summary.

## Results Ledger

Role: append-only chronological record of completed result bundles.

Rules:

- Add new completed bundles to the end.
- Preserve experiment order.
- For concurrent writers, the agent contract may specify one dated file per bundle
  and an index/rendering convention. Keep the append-only ledger for single-writer projects.
- Record bundle coverage, artifacts, upload links, and caveats, not the current best story.
- Mark exploratory or pending-review bundles explicitly; recording a bundle does not promote its conclusions.
- Do not turn this file into a claim-evidence map.
- Do not rewrite old entries merely because later terminology improved unless the old entry is misleading or blocks navigation.

## Claim-Evidence Map

Role: durable empirical claims and evidence.

Rules:

- Add a new claim only when an experiment produces a genuinely new useful insight.
- If a result strengthens, weakens, narrows, or broadens an existing claim, update that claim instead of adding a near-duplicate.
- Link the supporting study and its required review outcome. Confidence describes evidence strength, not whether a review happened; keep those distinct.
- Keep fewer claims than experiments.
- Do not organize this file by experiment chronology.
- Link all relevant bundles and artifacts under the claim without emphasizing discovery sequence unless the sequence itself matters.
- Keep conjecture arguments in the conjecture files.

Suggested confidence labels:

- **High**: repeated across models or methods, with a direct artifact trail.
- **Medium**: supported, but dependent on interpretation, a limited assay, or partial replication.
- **Low**: suggestive, but not stable enough to lean on.

## Experiment Agenda

Role: ranked planned next experiments agenda.

Use it to answer:

- what experiment should run next
- which belief that experiment would update
- what result would change priorities
- which tempting lines are deliberately paused

Rules:

- Keep it ranked and current-facing.
- Do not preserve completed experiment plans here as history.
- The post-run doc update deletes completed entries from the agenda instead of marking them `completed` in place; completed trails belong in study notes and the results ledger.
- Keep the agenda within the entry cap defined in the agent contract. Exceeding the cap is itself a doc bug to fix before the next run.
- Every freeze decision must classify itself as `question answered`, `question failure`, or `instrument failure`.
- Move completed artifact trails to the results ledger.
- Keep durable claim updates in the claim-evidence map.
- Keep high-level synthesis in the results summary and detailed empirical synthesis in results synthesis.
- Prefer decisive discriminators over incremental cleanup.
- Rerank after each meaningful result once its required review passes. Exploratory
  results may guide the next run under the agent contract's tier policy; link their
  record and retain the `exploratory / unreviewed` label.
- Each entry states why it is next, the end goal it advances, its estimated cloud cost in dollars
  and probability of success (`unknown` if not estimable), and its status with the date of its last
  real status change. Success is a positive or negative finding that guides the next steps. For a
  blocked entry, estimate as if the blocker clears. Once its study note exists, keep the estimates
  there and link to it.

## Study Notes

Role: individual study plans, methods, artifacts, results, skeptic gates, and interpretation.

Create the study note before implementing or launching a gated experiment. It is
both the pre-registration-lite plan and final record. The sections below are the
full form; use a project-defined short form or exploratory record only where the
agent contract permits it. Select the tier and form before seeing results.

Required pre-run sections:

- **Question**: the specific empirical question.
- **Motivation**: why this question matters now, and the end goal it advances.
- **Hypothesis / Competing Reads**: what live beliefs the result can distinguish, written neutrally rather than as advocacy.
- **Design**: model, data, intervention, controls, metrics, sample sizes, and scope. State the minimal effect of interest and whether the stated sample sizes can detect it; if they cannot, say so before the run.
- **Positive Control**: a known-positive manipulation included in the assay that demonstrates the metric can move under this harness.
- **Success / Failure / Ambiguous Conditions**: what result would count as positive, negative, inconclusive, or invalid before seeing the data.
- **Cost Estimate**: estimated cloud cost in dollars to complete the study, or `unknown`.
- **Probability Of Success**: estimated chance the study yields a positive or negative finding that guides the next steps, or `unknown`.
- **Skeptic Review (pre-launch)**: reviewer/context, source references, findings and resolution before launch, or `not required` with the applicable policy reference.
- **Decision Impact**: what each outcome would change in results summary, results synthesis, claim-evidence map, conjectures, or agenda.
- **Risks And Confounds**: likely failure modes, missing controls, implementation risks, and interpretation traps.
- **Expected Artifacts**: planned output files, plots, tables, logs, and where they should land.

Required post-run sections:

- **Executive Summary**: skim-reader summary at the **top** of the study note, written once results are in, marked `unreviewed` while required review is pending, then refreshed to the reviewed verdict.
- **Run Record**: command, environment, local/VM status, dates, artifact paths, upload links, commit or hash if relevant.
- **Results**: key quantitative and qualitative results.
- **Interpretation**: actual read against the pre-stated success, failure, ambiguous, and invalid conditions.
- **Prediction Scoring**: score each standing conjecture-file prediction this result bears on as `confirmed`, `refuted`, or `untouched`. A run that scores no predictions should say so explicitly.
- **Skeptic Review (post-result)**: reviewer/context, source references, findings and resolution before reviewed result use, or `not required` with the applicable policy reference. Follow the agent contract's permitted result uses.
- **Limitations**: what the result does not show.
- **Doc Updates**: which docs were updated or intentionally left unchanged.
- **Next Read**: what should happen next, including whether the line is frozen, reopened, needs replication, or needs a different assay.

Study-note rules:

- Write the pre-run sections before launching the experiment.
- Keep a `Status:` line below the title and role pointer: the study's current state and the date of its last real status change.
  When the study completes, add its outcome and its cloud cost (`~$` if estimated), e.g.
  `Status: complete · underpowered (unreviewed) · ~$1.21 · last changed 2026-10-26`. Outcomes are
  `positive`, `negative`, `mixed`, `ambiguous`, `underpowered`, `invalid`, `incomplete`, or `delivered`
  for a non-experiment output; add `(unreviewed)` while required post-result review is pending.
- State the tier and link its review policy. A policy exemption is `not required`,
  not a passed review; exploratory records remain `exploratory / unreviewed`.
- Create new study notes in the topic-specific study-note path from the agent contract.
- Do not move the goalposts after seeing results; if criteria change, add an explicit amendment with timing.
- Prefer `positive`, `negative`, `ambiguous`, `underpowered`, and `invalid` over vague `success`.
- A negative result is useful when the study note states what it rules out.
- Preserve detailed methods, artifacts, raw numerical tables, run records, and implementation notes in the body.
- Keep raw logs and exhaustive artifact detail out of summary docs; link to them from the study note.
- Move durable claim changes to the claim-evidence map, bundle coverage to the results ledger, and priority changes to the agenda.

### Executive Summary

Role: let a skim reader learn what this study found without reading the body.

- Place it at the **top** of the study note, after the role pointer and status/tier lines, before `Question`.
- Write it during result recording, mark it `unreviewed` while required review is pending, and refresh it after review. Before results, omit the section or state `Awaiting results`; do not present a predicted finding as observed.
- Keep it short: a few sentences. State a null result and its scope, for example `No effect above the preregistered threshold was detected; the passing control and sensitivity analysis support a negative verdict within this assay.` Use that wording only when those conditions hold; report inadequate sensitivity as `underpowered` instead.
- State the takeaway, not the method. Give at most a few anchor numbers, and only where the number *is* the takeaway.
- Do not restate detail already in `Results` or `Interpretation`. Link down to them instead.
- Name the most important caveat when one would change how a skim reader uses the result.
- Use the study's verdict vocabulary (`positive`, `negative`, `ambiguous`, `underpowered`, `invalid`) so the summary and the interpretation cannot drift apart.
- If the summary is later overtaken by a subsequent study, prepend a short dated correction rather than silently rewriting the original read.

Optional graphic:

- Where one plot carries the main result, embed it in the executive summary.
- Choose the single most legible figure for a non-expert skim reader; a busy diagnostic panel belongs in the body.
- The caption states the takeaway, not the axes: `Treatment lifts held-out accuracy on all five seeds` beats `Accuracy by seed`.
- Omit the graphic when no single plot honestly conveys the finding. A plot showing a well-bounded null can be useful too.

## Conjectures

Role: explicitly speculative beliefs, priors, and predictions.

Rules:

- Keep conjecture docs separate from empirical docs.
- For empirical belief revisions, record findings and pass the required post-result gate before updating conjectures; follow any explicit provisional-use exception in the agent contract. Literature- or reasoning-led ideas may be added with that origin stated, without inventing an experiment gate.
- Update only the conjecture file you own. Agents record disagreement and proposed revisions in their own file; edit human-owned conjectures only with explicit authorization.
- State uncertainty plainly.
- Use conjectures to generate experiment ideas, not to backfill claims into evidence docs.
- Human-owned and agent-owned conjectures can disagree; that tension is useful and can influence agenda rankings.
- Do not list metrics, artifact filenames, bundle histories, or long experiment chains unless a specific cell anchors a belief, prediction, or alternative.
- Use evidence documents as backlinks, not copied summaries.
- Phrase content as beliefs, predictions, falsifiers, and alternatives. If the prose mainly says “we observed”, move it to an empirical doc.
- If a conjecture needs detailed support, link to results synthesis or claim-evidence rather than restating the result.

## Glossary

Role: canonical project vocabulary.

Rules:

- Define terms that recur, affect interpretation, appear in artifacts, or could drift across docs.
- Prefer stable definitions over experiment chronology, next-step planning, or bundle summaries.
- Do not create near-synonyms for existing terms.
- If a synonym is unavoidable for readability, link it to the canonical term or add it as an alias.
- Multi-topic projects still use one project-wide glossary to prevent rival meanings.

## Naming Convention

- Framework docs use `<prefix>-<role>.md`.
- Single-topic project and templates: prefix is `thor`.
- Multi-topic project: copy per-topic docs once per topic and replace `thor` with the topic name, e.g. `diversity-agent.md`, `ensemble-next-steps.md`.
- Project-wide docs keep the `thor-` prefix: `thor-document-rules.md`, `thor-glossary.md` and the master `thor-study-template.md`. Multi-topic projects retain `thor-agent.md` as their shared router and keep topic-specific contracts alongside it.
- Project-wide docs exist once per project and are never duplicated per topic. A forked copy is how two threads acquire rival definitions of the same term.
- Declare the active topics, their scope boundaries, and their entry contracts in a thread registry in the agent contract. State what each topic does not own; overlapping scope is how two threads silently run the same experiment.
- A cross-topic schema, threshold, or interface that several topics must agree on gets one shared doc and is cited, not restated inside each topic's docs.

## When To Update What

Apply this table to authorized changes. For experiment-derived updates, first
apply the tier's review and result-use rules; routine document maintenance does
not require a research gate.

| Change | Update |
| --- | --- |
| New completed run or artifact bundle | Results ledger |
| New or changed durable empirical claim | Claim-evidence map |
| Changed current best story | Results summary |
| Changed primary empirical interpretation | Results synthesis |
| Changed next experiment priority | Experiment agenda |
| New recurring term | Glossary |
| Speculative belief update | Conjectures |
| Skeptic pass at a gate | Study note, Skeptic Review section |
| Experiment plan, methods, artifacts, or detailed result | Study note |
| Agent operating workflow or infrastructure contract | Agent contract |
| Portable doc structure or doc roles | Document rules |

### Router-Doc Update Order

Record the results in the study note and finish the required post-result review
first. Then update only the affected docs in this order:

1. Results ledger: new completed bundle and artifact coverage.
2. Claim-evidence map: new or changed durable empirical support.
3. Results synthesis: detailed interpretation of the empirical theme.
4. Results summary: compact current-story changes.
5. Agent conjectures: belief revisions and prediction streaks; propose human-file changes to its owner.
6. Experiment agenda: rerank, remove completed entries, and record supported freeze/reopen decisions.
7. Glossary: new recurring terms, defined before they spread to other docs or artifacts.

For exploratory runs, retain the run record in a study or ledger, then update the
agenda as permitted by the agent contract. Keep detailed results in their record;
do not use this route to update claims or conjectures. A project may define a
different order explicitly in its contract.

## Post-Update Cross-Document Audit

After changing project docs, compare the changed documents against each other before stopping.

Ask:

- Is this paragraph mainly speculative? It belongs in conjectures.
- Is this paragraph empirical detail from one experiment? It belongs in a study note.
- Is this paragraph bundle chronology or artifact coverage? It belongs in the results ledger.
- Is this paragraph assigning evidence support to a durable claim? It belongs in the claim-evidence map.
- Is this paragraph detailed mechanism interpretation or comparison? It belongs in results synthesis.
- Is this paragraph the compact current-state answer? It belongs in results summary.
- Is this paragraph about future priority? It belongs in the agenda.

Then remove repetition:

- If the same result appears in multiple reader-facing docs, keep detail only in the most specific useful document.
- Higher-level docs should keep conclusions and links downward.
- Lower-level docs should keep evidence and avoid repeating project-level framing.
- If two documents contain near-identical paragraphs, delete one and replace it with a pointer.

Finally verify the operating contract:

- Check changed instructions against their canonical rules and scoped exceptions.
- Match review labels to the actual review record and the tier's permitted uses.
- Check role pointers, relative links and anchors from each file's actual location.
- Preserve ownership, mandatory versus optional meaning, and meaningful conditions.
- Check that examples and validators demonstrate the outcomes they claim to check.

Drift smells:

- A conjecture section reads like “we observed...” instead of “we expect...”
- A synthesis section repeats the claim index rather than interpreting patterns.
- A study section tries to settle the whole project instead of its own question.
- An agenda section preserves completed plans as history.
- A glossary term appears in artifacts before being defined.

## Anti-Patterns

- Do not turn results summary into a result ledger.
- Do not turn results synthesis into a chronological bundle list.
- Do not put experiment chronology in the claim-evidence map.
- Do not put speculative conjecture in empirical docs.
- Do not put results-summary or results-synthesis paragraphs in conjecture docs.
- Do not promote the latest mechanism chain into the results summary unless it changes the compact current-state story.
- Do not let the agenda preserve completed plans as history.
- Do not promote a flat result to `negative` without a passing positive control and adequate detectable effect size.
- Do not run the skeptic in the working session's own context.
- Do not treat prediction scoring as permission to bypass the active contract's review and conjecture-ownership rules.
- Do not duplicate long document-purpose sections across docs; link to this file.
- Do not create method-specific top-level synthesis docs unless results synthesis has become too large to serve as the primary synthesis.
- Do not create a glossary per topic; there is exactly one `thor-glossary.md` per project.
- Do not add approval steps, receipts or deadlines that protect no result. Ceremony that delays work without making a result more trustworthy is a process failure.
