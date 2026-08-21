# <Project> Agent Contract (thor-agent.md)

This is the entry point. An agent rehydrates by reading this file first.

Naming note: in a single-topic project keep the `thor-` prefix as-is. In a
multi-topic project, copy the per-topic docs once per topic and replace `thor`
with the topic name, e.g. `methods-agent.md` or `diversity-agent.md`. Keep the
project-wide `thor-document-rules.md` and `thor-glossary.md` shared across
topics and un-renamed.

## Project Config

| Setting | Value |
| --- | --- |
| Project | `<name>` |
| Topic / thread name | `<topic, or same as project for single-topic repos>` |
| Goal | `<one-sentence research goal>` |
| Max autonomous hours | `<n>` |
| Depth budget | `<n consecutive same-line studies without a conjecture update, e.g. 4>` |
| Agenda entry cap | `<n active entries, e.g. 8>` |
| Skeptic model | `<any model in a separate thread; different model/vendor encouraged, not required>` |
| Compute / infra | `<platform, e.g. local, cloud VM, cluster>` |
| Artifact store | `<where result bundles live>` |
| Results summary | `<topic>-results-summary.md` |
| Results synthesis | `<topic>-results-synthesis.md` |
| Results ledger | `<topic>-results-by-time.md` |
| Claim-evidence map | `<topic>-claim-evidence.md` |
| Human conjectures | `<topic>-conjectures-human.md` |
| Agent conjectures | `<topic>-conjectures-agent.md` |
| Experiment agenda | `<topic>-next-steps.md` |
| Study notes | `<path>/<topic>-study-*.md` |
| Document rules | `thor-document-rules.md` |
| Glossary | `thor-glossary.md` |

## Thread Registry

*Multi-topic projects only. Delete this section in a single-topic project.*

A thread is one research topic with its own agent contract and its own full
per-topic doc set. Threads run in parallel, each with its own agenda and
conjectures, and each is entered through its own contract file.

| Thread | Scope | Entry contract |
| --- | --- | --- |
| `<name>` | `<what this thread owns, and what it does not>` | `<name>-agent.md` |
| `<name>` | `<scope>` | `<name>-agent.md` |

Deferred threads — scaffold a full doc set only when unblocked:

- `<name>` — `<what must happen first>`

Rules:

- Each thread carries its own `<thread>-agent.md`, `-conjectures-human.md`, `-conjectures-agent.md`, `-next-steps.md`, `-results-summary.md`, `-results-synthesis.md`, `-results-by-time.md`, `-claim-evidence.md`, and study notes under `study-<thread>/`.
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
one owner-less shared doc and cite it. Restating a shared constant inside a
thread's docs is a drift bug, not documentation.

## Rehydration

Use this after any restart, compaction, model/vendor swap, or long pause:

1. Read this file first.
2. Read the results summary for the current best story.
3. Read document rules when editing docs or when document structure is unfamiliar.
4. Read the results synthesis when the active question matches it or when the agenda points to it.
5. Read the glossary selectively when a project-specific term is unfamiliar or when editing terminology-heavy docs. Do not load it fully by default unless needed.
6. Read the experiment agenda.
7. Read the active study note for the current experiment line, if there is one.
8. Consult the claim-evidence map when you need evidence for a claim.
9. Consult the results ledger when you need artifact coverage for a specific bundle or when appending a completed bundle.
10. Check infrastructure/auth state as needed for the project's compute and artifact store.
11. Run `git status`; assume unrelated dirty files belong to the human, another agent, or another topic unless directly conflicting.

## Sources Of Truth

- This file is the source of truth for concrete filenames, topic names, artifact stores, autonomy limits, and infrastructure workflow.
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

Do not use “shared” ambiguously. In multi-topic projects, “shared” means shared across topics/threads, not merely co-edited by human and agent.

## Research Contract

An agent working on this topic must follow this loop unless the user explicitly overrides it.

### 1. Choose Work

- Prefer the highest-ranked unblocked item in the experiment agenda.
- Bias toward experiments that could invalidate large areas of the search space or discriminate between competing conjectures.
- Until a conjecture is strongly evidenced, prefer breadth over depth.
- Do not continue a same-line chain past the depth budget without written justification in a new or amended study note explaining what conjecture-level update the next run could still produce.

### 2. Plan In A Study Note

- Before implementing or launching a non-trivial experiment, write or amend the relevant study note under the study-note path in Project Config.
- Do not launch an experiment whose study-note contract is missing or explicitly incomplete.
- The pre-run study note must include the sections required by `thor-document-rules.md`, including positive control, minimal effect of interest, detectable-effect/power honesty, success/failure/ambiguous/invalid conditions, decision impact, risks, and expected artifacts.
- The plan must neutrally state competing reads. It can name hypotheses, but it must not advocate for the result the author hopes to see.
- Any post-plan criterion change must be recorded as a dated amendment before the result it affects is interpreted.

### 3. Run Pre-Launch Skeptic Gate

- Spawn a separate skeptic thread before launch.
- The skeptic rehydrates only from version-controlled docs and artifacts it is told to read. It must not inherit this working thread's live or compacted conversation context.
- The skeptic audits whether the positive control is real, the power statement is honest, the success condition discriminates live conjectures, and the controls are adequate.
- Record findings and resolutions in the study note's Skeptic Review (pre-launch) section.
- Resolve blocking concerns or explicitly overrule them in writing before launch.

### 4. Execute And Monitor

- Run at most one VM-backed or otherwise expensive experiment at a time unless the user explicitly allows more.
- If blocked by infrastructure, model-loading, auth, queue, or artifact-store issues, either fix the blocker or record it in the study note and move to the next best unblocked experiment.
- Long-running scripts should emit progress banners with explicit counts so status checks show meaningful progress.
- Monitor according to the project's compute rules.
- After VM-backed failure, OOM, or hang, inspect and sync useful diagnostic logs before changing or deleting the VM.
- After clean completion or once diagnostics are no longer needed, delete owned compute resources; guest auto-stop is only a best-effort cost brake.

### 5. Record Results In The Study Note

- Sync the completed result bundle into the artifact store and/or local results path.
- Complete the study note's post-run sections: executive summary, run record, results, interpretation, prediction scoring, limitations, doc updates, and next read.
- Prediction scoring in the study note is an empirical record. It does not update conjectures by itself.
- Do not update conjectures, claim-evidence, or agenda before empirical findings are recorded in the study note.

### 6. Run Post-Result Skeptic Gate

- Spawn a separate skeptic thread after results land and before conjectures update or agenda reranks.
- The skeptic rehydrates only from version-controlled docs and artifacts, not this working thread's context.
- The skeptic audits interpretation, verdict, prediction scoring, overclaiming, and whether `invalid` or `ambiguous` is dodging a supported verdict.
- Record findings and resolutions in the study note's Skeptic Review (post-result) section.
- Resolve blocking concerns or explicitly overrule them in writing before router docs update.

### 7. Update Router Docs In Order

After the post-result skeptic gate passes, update docs according to `thor-document-rules.md`.

Default order:

1. Results ledger for new completed run or bundle.
2. Claim-evidence map for new or changed durable empirical claims.
3. Results synthesis for detailed empirical interpretation changes.
4. Results summary for compact current-story changes.
5. Conjecture files for speculative belief updates and prediction-streak implications.
6. Experiment agenda for reranking, completed-entry deletion, and freeze/reopen decisions.
7. Glossary if new recurring terms were introduced.

Keep empirical docs separate from conjecture docs. Conjectures may link to evidence docs, but empirical docs should not argue for speculative beliefs.

### 8. Rerank And Freeze Correctly

- Delete completed agenda entries instead of marking them complete in place.
- Keep the agenda within the configured entry cap.
- Every freeze decision must classify itself as `question answered`, `question failure`, or `instrument failure`.
- A freeze classified as `instrument failure` triggers an outside-view sweep before the next experiment: search external literature for isomorphic problems and ask what their assays did differently.
- At major consolidation checkpoints, such as a paper draft, thread pivot, or instrument-failure freeze, write a short adversarial referee report on the current story before choosing the next line.

### 9. Run Cross-Document Audit

Before stopping, compare changed documents against each other.

- Move speculative text out of empirical docs.
- Move detailed experiment history out of summary docs.
- Move durable empirical support into claim-evidence.
- Move artifact coverage into the ledger.
- Move future priority into the agenda.
- Remove duplicated paragraphs and replace with links.
- Confirm newly introduced recurring terms are defined in the glossary.

## Common Process Rules

- Prefer shared constants and plan builders over ad hoc strings.
- Prefer public or accessible assets when expanding scope.
- Never rely on a previous thread's in-memory context for a later phase; write the needed context into the appropriate doc.
- Do not silently agree with human conjectures; they are expected to be incomplete or wrong. Push back and propose alternatives.

## Guardrails

- `<resource/permission limits, credentials, machines, privacy, data, budget>`
- Trust but verify: the human reviews agent changes before publication.

## Project-Specific Context

Add project-specific scientific frame, model scope, datasets, infrastructure notes,
and foundational papers here. Keep this section concrete to the project. Keep the
portable process contract above generic enough to copy across projects.
