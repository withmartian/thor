# thor: doing great research with AI agents that disagree with me

*By Philip Quirke (Martian)*

**TL;DR:** Agents have given me a genuine level-up. This past quarter, working
with agents, I roughly tripled my research throughput — and the quality went up,
not down. This is how I do it. The reusable templates are in
[this repo](../README.md).

## 1. The skill researchers should learn now

How do I best use AI agents as research assistants to do *great* research — not
over one clever prompt, but across a messy, multi-week exploration? This is a
practitioner's guide to what I have learned.

Each month, as the models get more capable and I get better at directing them,
the benefits increase. I do not want to do research without them again.

Research is a harder place to use agents than software engineering. In software,
the goal is usually clear and you can write a test for "done." My kind of
research has no such test. I start with an area, a direction, and a few clues —
but the destination is unknown, and the best I have is a starting hypothesis that
is probably wrong. There is no oracle to tell me whether today moved me closer.

The central danger, then, is not bad code. It is over-belief in a hypothesis —
mine or the agent's — that goes unchallenged for weeks. To manage that, I need a
process that does three things:

- maximizes progress and minimizes time lost down dead ends;
- keeps agents from hallucinating, or simply agreeing with me to be pleasant;
- limits the damage from my own blind spots and wrong priors.

This was a painful curve to climb. To help you avoid that pain, I have written my
practice up as a small, reusable framework called **thor** — Towards
Human-Oracle Research. The name is about treating the agent as a real
collaborator: we bring different strengths, they shift over time, and good
working habits should be built in now. Neither of us is an oracle alone — but a
human and agents working well together get closer to the truth than either could
on their own.

The most interesting part, and the part specific to research, is how I
deliberately keep the agent *disagreeing* with me for weeks.

## 2. Positive disagreement

Agents default to being agreeable. It is less than sycophancy, but it is a bias
toward agreeing with whatever I propose. An agent that will not push back will
happily spend days, and many tokens, chasing a path I suggested. As my idea may
simply be wrong, that can be costly.

I have seen the same thing in people. A junior developer who wants to please me,
who assumes my experience gives me God-like insight (it does not), and who
therefore buries their own better instinct and builds exactly what I asked for.
Good management fixes that in people. thor tries to fix it in agents.

I want **positive disagreement** from agents. My process for this has a few
moving parts:

- **Two separate belief files.**
  [Human conjectures](../templates/thor-conjectures-human.md) and
  [agent conjectures](../templates/thor-conjectures-agent.md) live in different
  files with different owners. I own mine; the agent owns its own and updates it
  as experiment results land. They are allowed to disagree, and usually do.
- **Disagreement written into the contract.** Every agent reads
  [`thor-agent.md`](../templates/thor-agent.md) on startup, and its standing
  instruction is blunt: do not silently agree with the human's conjectures; they
  are expected to be incomplete or wrong; push back and propose alternatives.
- **Experiments that settle bets.** The agent is asked to pick a next
  experiment, with a bias toward ones that *discriminate between competing
  conjectures* — mine and the agent's — rather than pile confirmation on whoever
  spoke first.
- **Pre-registered, neutral study plans.** Each experiment gets a
  [study document](../templates/thor-study-template.md) stating what will run and
  what would count as success, failure, ambiguity, or invalidity — before the
  run. It can name the competing conjectures, but it must state them neutrally,
  not as advocacy for a particular result.
- **A skeptic reviews the plan before launch.** A fresh agent — ideally a
  different model or vendor — rehydrates *only* from the documents, not from the
  working thread's memory, and attacks the design.
- **A skeptic reviews the results.** After the experiment runs, another fresh
  thread checks whether the verdict is over-claimed or the prediction scoring was
  too generous.
- **Only then** do the results fold back into the conjecture files and re-rank
  the "next steps" agenda.

Of everything in thor, these **skeptic gates** have given me the single biggest
lift in quality. They are cheap insurance against turning a broken experiment
into a belief. In some cases they stop a proposed experiment from being run at
all — and the cheapest save is the experiment that never runs.

If I suspect the agent is still being too agreeable, or I am frustrated with
progress, I prompt it: *"Ignore my hypothesis. Think deeply. What do you think
the model is actually doing? Add any new ideas to your conjectures."*

## 3. The boring part that makes it work: write it down

An agent's working memory is wiped on every crash, compaction, vendor swap, and
reboot — and mine is degraded every time I context-switch to another thread. So
the durable state of the project lives in version-controlled Markdown files.

This is not glamorous, and it is the thing that makes the rest possible. The
documents survive agent crashes, tool upgrades, a change of vendor, a laptop
reboot, a collaborator joining by cloning the repo, and the sheer length of a
weeks-long project.

Because all state is in the documents, thor is agent- and model-agnostic. I have
run it with Claude, ChatGPT, and OpenCode. That is also what makes the
cross-vendor skeptic work: a fresh agent on a *different* model, attacking the
first one's interpretation, raises my confidence in a way a same-model reviewer
cannot — it does not share the same blind spots.

## 4. The documents

thor is a handful of Markdown files, each with one job and one owner. The two
conjecture files and the pre-registered study docs above are the heart of it. The
rest hold the project together:

- **The contract** ([`thor-agent.md`](../templates/thor-agent.md)) is the entry
  point. Every session starts the same way — "read `thor-agent.md`" — and that
  one ritual, rehydration, works only because the project state lives in the docs
  and not the session. It is also where the push-back culture lives.
- **A ranked agenda** ([`thor-next-steps.md`](../templates/thor-next-steps.md)):
  what to do next, re-ranked after every result.
- **The results trio:** a compact current-story summary, an append-only
  chronological ledger of what ran, and a claim-to-evidence map
  ([results-summary](../templates/thor-results-summary.md),
  [results-by-time](../templates/thor-results-by-time.md),
  [claim-evidence](../templates/thor-claim-evidence.md)). These are strictly
  empirical — no conjecture allowed. Keeping observed evidence and speculative
  belief in separate files is a guardrail against biasing results.
- **One glossary** ([`thor-glossary.md`](../templates/thor-glossary.md)). Agents
  invent their own compact terms in a project, partly for token efficiency, and
  over weeks those meanings drift. A single project-wide glossary forces terms to
  be defined once and used consistently everywhere.

The full role and update rules for each document live in
[`thor-document-rules.md`](../templates/thor-document-rules.md); I will not
repeat them here.

## 5. Be a manager: assistant, not scientist

The single most useful stance I have found is this: **be a manager.** Agents
cannot yet run research unguided. They are research assistants, not research
scientists. But they are fast and cheap and they know a lot.

(In one month I let agents self-direct, and the results were uninspiring. They
went down rabbit holes — 50% clarity in one experiment, then 20%, then 10% —
chasing a fading signal long after I would have given up.)

Agents are genuinely useful as semi-independent assistants, but they still need a
human in the loop. They get tunnel vision. They need occasional, deliberate
guidance to step back.

They also lack research taste. To my eye the agents are very knowledgeable junior
assistants — strong on things I am weak on, and yet sometimes surprisingly blank
on something I assumed was obvious. When that happens, I write the missing prior
into my conjecture file and restart the standard process.

I review what the agent changes before it is committed. Trust, but verify. The
documents are how I manage at a distance: they let me set direction, see what the
agent believes, and catch a wrong turn without watching every step. My control
surface is the Markdown diff, not the code line-by-line — I use "push to git" as
the review point, and I pay more attention to `thor-*.md` changes than to
individual study notes.

My day-to-day "speed limit" is not compute or the number of agents — it is how
many threads I can hold in my head. I usually run two at once, occasionally up to
five. More threads than I can review actually *lowers* quality. The goal is not
to maximize the number of threads; it is to maximize knowledge gained per day.

## 6. What it costs, and where it can go wrong

thor is not free, and it is not self-enforcing. The honest caveats:

- **The skeptic can be sycophantic too.** A reviewer that just says "great
  experiment" adds nothing. The skeptic prompt has to be explicitly adversarial —
  *find why this is wrong or over-claimed* — ideally on a different vendor whose
  failure modes don't match the worker's.
- **Pre-registration can be quietly gamed.** An agent (or I) can loosen the
  success criteria after peeking at results. The git history of the study doc is
  the defense: the criteria should provably pre-date the run.
- **Append-only isn't automatic.** Agents love to "tidy" the chronological
  ledger and quietly rewrite history. State the rule explicitly and spot-check
  the diffs.
- **Rehydration cost grows.** As the ledger lengthens, a fresh agent takes longer
  to read in. The compact summary is what keeps rehydration cheap — it has to be
  actively *pruned*, not just appended to.
- **The human is the bottleneck, by design.** Throughput is capped by my
  context-switching, not by compute or agent count. That is a feature: it is what
  keeps quality high.

And the cost is a dial, not a fixed tax. Skeptic gates and extra agents cost
tokens; right now my process is, if anything, a little over-strict. When that
happens, dial the gate frequency down rather than treat every gate as mandatory.

The upside is that the same discipline pays a dividend at the end. The
claim-to-evidence map plus the time-ordered ledger are most of a paper's methods
and results sections already — the audit trail is a deliverable, not just
hygiene. And onboarding a collaborator, human or fresh agent, is a `git clone`
and one instruction: read the contract.

## 7. It travels

There is early evidence that this approach generalizes beyond me. I have used the
thor assets on four of my own projects — one of them a larger, multi-topic effort
with five separate internal threads, each with its own thor agent — and two
researcher friends have found the approach useful on entirely different problems.
On an older project I re-ran with thor, two agents produced 35 experiments in
three days.

I have pulled the documents into a small, project-agnostic set of
[templates](../README.md), explicit enough that a new project starts from the
recommended contract rather than from oral tradition. You can see them at work in
[four real projects](../EXAMPLES.md).

This process does not guarantee an interesting result — one of my own projects
produced a technically solid, valid paper with some novel findings that simply
was not very exciting. But the process keeps me honest, keeps the agent
disagreeing, keeps quality high, and keeps the dead ends cheap.

This is my current snapshot, not a finished system; my practice and the templates
keep improving. If you try them, I would like to hear what broke.

---

**Get the templates:** [github.com/withmartian/thor](https://github.com/withmartian/thor)
· Walkthroughs on real projects coming.
