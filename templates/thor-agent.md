# <Project> Agent Contract (thor-agent.md)

Read role and rules: [Agent Contract](thor-document-rules.md#agent-contract).

Read this file first, then follow Rehydration for the assigned topic and task.

Naming note: in a single-topic project keep the `thor-` prefix as-is. In a
multi-topic project, copy the per-topic docs once per topic and replace `thor`
with the topic name, e.g. `methods-agent.md` or `diversity-agent.md`. Keep the
project-wide `thor-document-rules.md`, `thor-glossary.md` and master
`thor-study-template.md` shared and un-renamed. In a multi-topic project, retain
`thor-agent.md` as the repo-wide router; topic contracts link to its shared policy.

## Project Config

| Setting | Value |
| --- | --- |
| Project | `<name>` |
| Topic / thread name | `<topic, or same as project for single-topic repos>` |
| Goal | `<one-sentence research goal>` |
| Autonomy / resource limits | `<approved scope, budget and resources; any explicit human-set session limit>` |
| Exploratory budget | Not configured. Set a per-run cost/resource ceiling to enable the exploratory tier below. |
| Depth budget | `<n consecutive same-line studies without a conjecture update, e.g. 4>` |
| Agenda entry cap | `<n active entries, e.g. 8>` |
| Skeptic model | `<any model in a separate review context; different model/vendor encouraged, not required>` |
| Compute / infra | `<platform, e.g. local, cloud VM, cluster>` |
| Cloud resource labels | `<labels your organization requires on every VM the project creates, e.g. owner, project, environment, data classification>` |
| Artifact store | `<where result bundles live>` |
| Results summary | `<topic>-results-summary.md` |
| Results synthesis | `<topic>-results-synthesis.md` |
| Results ledger | `<topic>-results-by-time.md` |
| Claim-evidence map | `<topic>-claim-evidence.md` |
| Human conjectures | `<topic>-conjectures-human.md` |
| Agent conjectures | `<topic>-conjectures-agent.md` |
| Experiment agenda | `<topic>-next-steps.md` |
| Study notes | `docs/study-<topic>/<topic>-study-*.md` (use `thor` for a single-topic project) |
| Document rules | `thor-document-rules.md` |
| Glossary | `thor-glossary.md` |

## Thread Registry

*Multi-topic projects only. Delete this section in a single-topic project.*

A thread is one topic with its own agent contract and applicable per-topic docs.
Research threads run in parallel, each with its own agenda and conjectures, and
each is entered through its own contract file.
An agent session is one conversation; a workstream is an owned unit of work
within a topic. Sharing a topic does not grant ownership of another workstream.

| Thread | Scope | Entry contract |
| --- | --- | --- |
| `<name>` | `<what this thread owns, and what it does not>` | `<name>-agent.md` |
| `<name>` | `<scope>` | `<name>-agent.md` |

Deferred threads — scaffold a full doc set only when unblocked:

- `<name>` — `<what must happen first>`

Rules:

- Each research thread carries its own `<thread>-agent.md`, `-conjectures-human.md`, `-conjectures-agent.md`, `-next-steps.md`, `-results-summary.md`, `-results-synthesis.md`, `-results-by-time.md`, `-claim-evidence.md`, and study notes under `study-<thread>/`. Non-experiment topics use only the roles their work needs.
- State what each thread does **not** own. Overlapping scope is how two threads silently run the same experiment.
- A thread that owns no experiments and only reads evidence, such as a paper thread, says so explicitly and is read-only over other threads' docs.
- Do not create a thread before it has a question of its own. Threads are cheap to add and expensive to keep coherent.

### Project-Wide Shared Docs

One instance each, project-wide. **Never duplicate these per thread** — a forked
copy is how two threads end up with rival definitions of the same term.

| Doc | Purpose |
| --- | --- |
| `thor-document-rules.md` | Portable document roles, update order, skeptic gates, anti-patterns |
| `thor-glossary.md` | Canonical vocabulary across all threads (anti-drift) |
| `thor-study-template.md` | Study-note template; copy per experiment into `study-<thread>/` |
| `<project cross-thread contract>` | `<schemas, thresholds, interfaces that several threads must agree on. Divergence here breaks integration silently.>` |

Where several threads must agree on a schema, threshold, or interface, give it
one project-wide doc with named coordinating owners and cite it. Restating a
shared constant inside a thread's docs is a drift bug, not documentation.

## Rehydration

Use this after any restart, compaction, model/vendor swap, or long pause:

1. Read this file and the assigned topic's contract from the registry, if separate.
   For multi-topic research, ask for the assignment when the task does not identify one.
2. Run `git status` before edits, experiments or infrastructure work. Leave
   unrelated changes with their owner; a dirty checkout alone is not a blocker.
3. Read the results summary, experiment agenda and active study note for research
   work. For a scoped documentation task, read the affected docs and their rules.
4. Before planning or running an experiment, read [Experiment Tiers](#experiment-tiers)
   and Document Rules' [phase order](thor-document-rules.md#thread-isolation-and-phase-boundaries),
   [evidence rules](thor-document-rules.md#evidence-and-verdict-rules) and
   [skeptic gates](thor-document-rules.md#skeptic-gates).
5. Before editing docs, read their roles and the [update workflow](thor-document-rules.md#when-to-update-what).
6. Read results synthesis for mechanism detail, claim-evidence for claim support,
   and the ledger for bundle coverage. Read the relevant conjecture entries for
   experiment selection; read full conjecture sets for a full rerank.
7. Consult the glossary for unfamiliar terms and before introducing terminology.
8. Check the project's infrastructure/auth rules before the corresponding remote
   action. Local documentation work requires no cloud authentication or VM inspection.

## Sources Of Truth

- This file is the source of truth for concrete filenames, topic names, artifact stores, autonomy limits, and infrastructure workflow.
- The Experiment Tiers section defines local gate applicability. Put explicit
  project overrides here and link them from affected docs; do not leave rival defaults.
- `thor-document-rules.md` is the source of truth for portable document roles, update order, terminology discipline, skeptic gates, and anti-patterns.
- `thor-glossary.md` is the source of truth for canonical vocabulary across all topics.
- Study notes are the source of truth for individual experiment plans, amendments, run records, results, skeptic reviews, and immediate next read.
- Results ledger is the source of truth for chronological bundle coverage.
- Claim-evidence map is the source of truth for durable empirical claims.
- Conjecture files are speculative and must not be used as empirical evidence.

## Ownership

- Human-owned: this agent contract, document rules, human conjectures.
- Agent-owned: agent conjectures and study notes it writes, subject to human review.
- Coordinated topic docs: agenda, results summary, results synthesis, results ledger, claim-evidence map.
- Project-wide cross-topic docs: `thor-document-rules.md` and `thor-glossary.md`.

Edit human-owned docs only with explicit authorization. Record disagreements
with human conjectures in the agent conjecture file; proposing a revision does
not authorize changing the human's beliefs. A required review or source snapshot
does not itself grant permission to commit or push.

Do not use “shared” ambiguously. In multi-topic projects, “shared” means shared across topics/threads, not merely co-edited by human and agent.

## Experiment Tiers

Select the tier before launch from the intended use and the configured budget.
These are the portable defaults; a project may replace this table with explicit
cost tiers, study forms and review requirements. Keep one project-wide policy and
link to it from topic contracts, recording any scoped exceptions there.

| Tier | Applies to | Record | Pre-launch review | Post-result review |
| --- | --- | --- | --- | --- |
| `exploratory` | Preliminary experiments within the configured exploratory budget, used only to choose the next experiment | Question, limit and applicable controls in the agenda or an existing study before launch; run/artifact references, results and limitations in a study or ledger at completion | None | None |
| `gated` | All other non-trivial experiments, including any intended to support a durable claim, conjecture update, cross-thread evidence handoff or freeze | Full study note | Required | Required |

- An unset exploratory budget enables no ungated experiments. Use `gated` for
  non-trivial experiments until the project sets that budget.
- Exploratory results may rerank the agenda and motivate a gated study. Mark them
  `exploratory / unreviewed`; rerun at the gated tier before using them for a claim,
  conjecture update, cross-thread evidence handoff or freeze. Do not relabel a
  completed pilot as a preregistered gated study.
- Routine documentation maintenance and deterministic software checks that make
  no empirical research claim need no study note or research review.
- Tier changes process, not reporting honesty, control requirements, ownership
  or resource permissions. A project-defined short form names its required fields;
  choose it before results, not to suit the outcome.

## Research Contract

Follow the [phase order](thor-document-rules.md#thread-isolation-and-phase-boundaries)
and [skeptic rules](thor-document-rules.md#skeptic-gates) for the selected tier,
unless the user explicitly overrides them. The portable workflow and update order
live in Document Rules; the local choices and infrastructure steps live here.

### Choose Work

- Prefer the highest-ranked unblocked item in the experiment agenda.
- Bias toward experiments that could invalidate large areas of the search space or discriminate between competing conjectures.
- Until a conjecture is strongly evidenced, prefer breadth over depth.
- Before continuing past the depth budget, write a justification in the next
  study note explaining what conjecture-level update the run could still produce.
  Otherwise pause same-line work and record the freeze decision once its evidence
  and required review are available. Stopping a run never waits for a review.

### Plan And Review

- Complete the selected tier's pre-run record before implementation or launch.
  Use the [study-note requirements](thor-document-rules.md#study-notes) for a gated study.
- State competing reads neutrally. Record a dated amendment for any criterion
  change, including whether the affected results were already seen.
- Complete each required review in a separate context using declared docs and
  artifacts. Record its findings and resolution in the study note; a self-check
  is preparation, not the skeptic gate.

### Execute And Monitor

- Run at most one VM-backed or otherwise expensive experiment at a time unless the user explicitly allows more.
- Resolve infrastructure blockers within the authorized scope. Record unresolved
  blockers in the study or agenda and select the next ranked unblocked experiment.
- Emit progress banners with explicit counts from long-running scripts so status
  checks show meaningful progress.
- Monitor according to the project's compute rules.
- After VM-backed failure, OOM, or hang, inspect and sync useful diagnostic logs before changing or deleting the VM.
- After preserving outputs and diagnostics, stop and clean up owned compute under
  the project's resource permissions. Delete resources when that authority permits;
  guest auto-stop is only a best-effort cost brake.

### Record And Update

- Sync the completed result bundle into the artifact store and/or local results path.
- Record findings and limitations in the tier's required record before updating
  other docs. Mark results `unreviewed` until their required post-result gate passes.
- Follow the [router-doc update order](thor-document-rules.md#router-doc-update-order).
  Record prediction scores as evidence before revising beliefs; preserve human ownership.

### Rerank And Freeze

- Maintain the agenda under [Experiment Agenda](thor-document-rules.md#experiment-agenda),
  including the entry cap, completed-entry removal and freeze classification.
- A freeze classified as `instrument failure` triggers an outside-view sweep before the next experiment: search external literature for isomorphic problems and ask what their assays did differently.
- At major consolidation checkpoints, such as a paper draft, thread pivot, or instrument-failure freeze, write a short adversarial referee report on the current story before choosing the next line.

### Cross-Document Audit

Before stopping, run the [cross-document audit](thor-document-rules.md#post-update-cross-document-audit)
on changed docs, including role boundaries, applicable policy, review state and links.

## Common Process Rules

- Prefer shared constants and plan builders over ad hoc strings.
- Prefer public or accessible assets when expanding scope.
- Write context needed by a later session or reviewer into the appropriate doc.
- Challenge unsupported human conjectures and propose alternatives. They are
  hypotheses to test, not empirical evidence.

## Guardrails

- `<resource/permission limits, credentials, machines, privacy, data, budget>`
- Trust but verify: the human reviews agent changes before publication.

## Project-Specific Context

Add project-specific scientific frame, model scope, datasets, infrastructure notes,
and foundational papers here. Keep this section concrete to the project. Keep the
portable process contract above generic enough to copy across projects.
