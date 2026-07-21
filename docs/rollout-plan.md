# thor rollout & repo references (maintainer doc)

> **Transitional.** This is an internal checklist for moving thor into its own
> repo and wiring the other projects to it. It is deliberately **not linked from
> the public README**. Delete it once the rollout below is complete.
>
> **Prerequisite:** `withmartian/thor` exists and is public, and this repo has
> been pushed to it. Until then, do not remove anything from the other repos —
> their links would break.

---

## Part 1 — Repo cleanup checklist (coming days)

### `intent` — source of the templates and the blog drafts

This is the only repo that loses files; everything else only *gains* a reference
block.

| Action | Path | Notes |
| --- | --- | --- |
| **Delete** | `thor-templates/` | Canonical home is now the thor repo. |
| **Delete** | `docs/study-paper/draft-F-blog-1-thor.md` | Polished into `docs/blog.md` in the thor repo. |
| **Delete** | `docs/study-paper/draft-F-li-1-thor.md` | Polished into `docs/linkedin.md` in the thor repo. |
| **Delete** | `docs/study-paper/thor-reflections.md` | Source notepad; its content is folded into the thor repo blog. |
| **Keep** | `docs/thor-*.md` (agent, conjectures, results, claim-evidence, next-steps, synthesis, document-rules, glossary) | These are intent's **live research record**, not templates. Do **not** delete. |
| **Keep** | `docs/study-paper/draft-I-blog-1-intent.md`, `review-*.md` | intent-specific content, unrelated to the framework launch. |
| **Alter** | `README.md` | Add the "About thor" block (Part 2) above the existing "Research Docs" list, so a reader knows what the framework is and where it lives. The existing doc list stays. |

**Before deleting, from the intent repo root, confirm nothing else points at the
files being removed:**

```bash
grep -rn "thor-templates" . --exclude-dir=.git
grep -rn "study-paper/draft-F" . --exclude-dir=.git
grep -rn "thor-reflections" . --exclude-dir=.git
```

Expected hits are only inside the files being deleted (the blog drafts link to
`../../thor-templates/`). Fix or remove any others (e.g. `README.md`,
`AGENTS.md`, `CLAUDE.md`) before deleting.

### `quanta_maths`, `scaling-laws`, `Wayfinder` — reference only

No deletions. Each keeps its own filled-in `docs/thor-*.md`. The only change is
to **add the tailored "About thor" block (Part 2)** to the repo's `README.md`
(quanta_maths and scaling-laws lead with an intro/overview — place the block
immediately after it; Wayfinder can take it directly under its opening
paragraph).

In each repo, sanity-check for any stale copy of the templates or broken
framework links:

```bash
grep -rn "thor-templates" . --exclude-dir=.git
```

---

## Part 2 — The standard "About thor" reference insert

Goal: someone who lands on **any** of these repos first should immediately
understand what thor is, what it does for that repo, and where to learn more —
phrased consistently everywhere. Copy the block below into the repo's `README.md`
and use the matching doc list.

### Canonical block (the shared wording)

```markdown
## Research process — thor

This project's research is run with **thor** (Towards Human-Oracle Research), a
lightweight framework for doing real research with AI agents as semi-independent
assistants. thor keeps the human's and the agent's beliefs in separate,
version-controlled Markdown files, biases experiments toward ones that settle the
disagreement between them, and runs a fresh "skeptic" agent over every plan and
result. Because all project state lives in these docs, the work survives crashes,
model/vendor swaps, and a new collaborator joining by `git clone`.

New to thor? Start with the framework and templates: **https://github.com/withmartian/thor**
```

Then append the repo-specific doc list from below.

### `intent` (full framework)

intent already has a "Research Docs" section listing its docs, so add **only the
canonical block above** (without a duplicate doc list) immediately before that
section. Optionally add one line at the end of the block:

```markdown
This repo runs the **full** thor document set; `docs/thor-agent.md` is the entry point.
```

### `quanta_maths`

Append to the canonical block:

```markdown
The thor documents in this repo (`docs/`):

- `thor-agent.md` — the operating contract and rehydration entry point
- `thor-document-rules.md` — what each doc is for and how to update it
- `thor-glossary.md` — the project's canonical vocabulary

Start by reading `docs/thor-agent.md`.
```

### `scaling-laws`

Append to the canonical block:

```markdown
This repo uses the project-wide thor docs (`docs/`) for terminology and document
discipline:

- `thor-document-rules.md` — what each doc is for and how to update it
- `thor-glossary.md` — the project's canonical vocabulary
```

### `Wayfinder`

Append to the canonical block:

```markdown
The thor documents in this repo (`docs/`):

- `thor-agent.md` — the operating contract and rehydration entry point
- `thor-document-rules.md` — what each doc is for and how to update it
- `thor-glossary.md` — the project's canonical vocabulary

Start by reading `docs/thor-agent.md`.
```

---

## Part 3 — After the rollout

- Update the placeholder in `docs/linkedin.md` (`[LINK]`) and the closing link in
  `docs/blog.md` with the public `withmartian/thor` URL.
- Confirm the [EXAMPLES.md](../EXAMPLES.md) links resolve (each example repo is
  public or the row notes it is internal).
- Delete this maintainer doc.
