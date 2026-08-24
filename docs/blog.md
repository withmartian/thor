# <img src="../images/thor-mark.png" width="40" alt=""> thor: doing great research with AI agents that disagree with me

*By Philip Quirke (Martian)*

*Over the past quarter, agents have roughly tripled my research throughput.
As far as I can tell, the quality has gone up too. This is the process I currently use.
The templates are available in the [thor repository](https://github.com/withmartian/thor).*

Research is a harder setting for agents than software engineering. In software, the target
is often reasonably clear and there is usually some kind of test for whether you have reached it.
My research does not work like that. I normally begin with an area, a direction and a few clues.
The destination is unknown. My starting hypothesis is also quite likely to be wrong.

This changes the main risk. A bad piece of code is usually exposed eventually. A bad research
hypothesis can survive for weeks, especially when both the researcher and the agent want it to
be true. There is no oracle telling you whether today’s work brought you closer to an important
result or sent you further down a dead end.

I spent a fair amount of time learning this the painful way. The process I now use is called **thor**,
short for Towards Human-Oracle Research. The name is slightly grander than the thing itself. In practice,
thor is a collection of Markdown files and working habits for keeping a research project honest over many weeks.

The most important habit is to make it normal for the agent to disagree with me.

## Positive disagreement

Agents are inclined to agree with the person directing them. This is not always full-blown sycophancy.
Often it is just a mild tendency to accept the framing they were given and keep going. In research, that
is enough to waste a lot of time. If I suggest the wrong explanation, an agreeable agent can spend days
producing competent work in support of it.

People do this as well. A junior researcher or developer may assume that the more experienced person has
noticed something they have not. They suppress their own better instinct and build exactly what was requested.
A good manager has to make disagreement safe and useful. The same is true with agents.

I use a few devices to do this.

First, the human and the agent keep separate belief files: [human conjectures](https://github.com/withmartian/thor/templates/thor-conjectures-human.md) and
[agent conjectures](https://github.com/withmartian/thor/templates/thor-conjectures-agent.md). I own the first.
The agent owns the second and updates it as results arrive. The files are often inconsistent with one another.
That is fine. Their purpose is to show what each of us actually thinks, rather than produce an artificial consensus.

The expectation of disagreement also appears in the [agent contract](https://github.com/withmartian/thor/templates/thor-agent.md),
which every agent reads when it starts. The instruction is quite blunt: the human’s conjectures are likely to be
incomplete or wrong. Do not quietly adopt them. Push back and propose alternatives.

Experiments are then chosen partly for how well they distinguish between competing explanations. I would usually
rather run one experiment that could prove either of us wrong than three experiments that add weak support to the
idea we already favour.

Before anything runs, the agent writes a [study document](https://github.com/withmartian/thor/templates/thor-study-template.md).
It says what will be tested and what would count as success, failure, ambiguity or an invalid experiment.
If the experiment concerns competing conjectures, both are described neutrally. The point is to make these decisions
before seeing the result.

A fresh agent then reviews the plan. Ideally I use a different model or vendor. It reads the project documents but
does not inherit the working thread or see the conjecture files, and its job is to find problems with the design.
After the experiment, another fresh review checks whether we have overclaimed the result or scored our predictions
too generously. Only after that do the findings go back into the conjecture files and change the ranked agenda.

These skeptic reviews have probably produced the largest improvement in quality. Sometimes they catch an interpretation
that is too convenient. Sometimes they find that an experiment cannot answer the question it was meant to answer, so I
do not run it. That is the cheapest possible result.

When the whole process still feels too agreeable, I sometimes give the agent a more direct prompt:

> Ignore my hypothesis. Think deeply. What do you think the model is actually doing? Add any new ideas to your conjectures.

It is a simple intervention, but surprisingly useful.

## Write everything down

An agent loses its working memory after a crash, a compaction, a vendor change or a new thread. My own memory is not much
better after I have switched between several projects. The durable state of the research therefore lives in version-controlled
Markdown files.

This is the boring part of thor, but a reason it works. The documents survive laptop reboots and tool changes. A human collaborator
can clone the repository and see the same project the agent sees. A new model can pick up the work without relying on a long,
half-remembered conversation.

It also makes the method model-agnostic. I have used versions of it with Claude, ChatGPT and OpenCode. It also makes cross-model
criticism easy. A reviewer from another model family may have different blind spots from the agent that ran the experiment.
That does not make the review independent in any strict sense, but it is better than asking the original thread to inspect
its own reasoning.

## What is in the project

Thor uses a small set of files. Each has one job and, where it matters, one owner.

The [agent contract](https://github.com/withmartian/thor/templates/thor-agent.md) is the entry point.
Every session begins with the same instruction: read `thor-agent.md`.
It explains how to reconstruct the state of the project and sets the expectation that the agent should challenge me.

The two conjecture files hold our current beliefs.
They are deliberately separate from the empirical record.
I do not want a plausible explanation to slide into a results summary and gradually become treated as an observation.

The [ranked agenda](https://github.com/withmartian/thor/templates/thor-next-steps.md) says what should happen next.
It is updated after new evidence arrives. Individual experiments have their own pre-registered study documents.

Results are split across three files. The [results summary](https://github.com/withmartian/thor/templates/thor-results-summary.md)
gives the current story in compact form. The [chronological ledger](https://github.com/withmartian/thor/templates/thor-results-by-time.md)
records what actually ran and is append-only. The [claim-to-evidence map](https://github.com/withmartian/thor/templates/thor-claim-evidence.md)
shows which result supports which claim. These files are empirical. Conjectures belong elsewhere.

There is also one shared [glossary](https://github.com/withmartian/thor/templates/thor-glossary.md). Agents invent
compact terms as a project develops, partly because compact language saves tokens. The meaning of those terms can
drift over several weeks. A project-wide glossary keeps everyone using the same vocabulary.

The detailed ownership and update rules are in [`thor-document-rules.md`](https://github.com/withmartian/thor/templates/thor-document-rules.md).
They are dull enough that I will not reproduce them here, but explicit rules are vital when the same files are being
edited by many agents across many sessions.

## You still have to manage the research

I once let agents direct themselves for roughly a month. The results were not very good. They would find a signal
with 50% clarity, follow it to 20%, then 10%, then 1%, continuing down the same rabbit hole long after I would have stopped.

This experience changed how I think about the division of labour. Current agents can be very capable research assistants.
They are fast, inexpensive and knowledgeable about things I am weak on. They can also develop tunnel vision, and occasionally
they are blank on something I had assumed was obvious. When that happens, I write the missing prior into my conjecture file
and restart the agent.

Research taste still has to come from somewhere. For my projects, it mostly comes from the human choosing the direction,
noticing when a result is uninteresting, and deciding when a fading line of inquiry has had enough chances.

I review the agent’s changes before they are committed. I do not inspect every line of code, but I pay close attention to
the Markdown diff, especially changes to the `thor-*.md` files. That is where beliefs, claims and priorities move.
The diff is my main control surface.

The limit on my throughput is usually the number of research threads I can understand well enough to review.
I tend to run two at once and have occasionally managed five. Beyond that, adding agents reduces quality.
The relevant quantity is knowledge gained per day, rather than agents or tokens spent per day.

## Where it fails

Thor adds process, but the process can also fail.

A skeptic agent may be just as agreeable as the original one. A review that says "great experiment" and offers a few cosmetic
suggestions is low value. The reviewer needs a narrow, adversarial instruction: find why this design is wrong, or why this
conclusion is overclaimed. Using another vendor helps when the models have different failure modes.

Pre-registration does not enforce itself either. An agent may quietly loosen a success criterion after seeing the data.
Git history provides a useful defence because it shows whether the study plan predates the run.

The append-only ledger has a similarly fragile name. Agents like to tidy documents. Unless told otherwise, they may rewrite
an old entry and accidentally improve the history. The rule has to be (and is) explicit.

There is also a cost to rehydration. The chronological record grows indefinitely, so a fresh agent should not read all of it.
It reads the compact results summary and claim map. Those files can occasionally need a human to prune them.

Finally, the human remains a bottleneck. This is intentional up to a point. The bottleneck is what stops five plausible but
wrong threads from racing ahead unnoticed. Still, skeptic reviews and extra agents cost tokens and time. My current setup is
probably a little too strict. I treat the frequency of the gates as a dial and reduce it when the risk is low.

The paperwork pays for itself near the end of a project. The claim-to-evidence map and chronological record already contain
much of what is needed for a paper’s methods and results sections. They also make it much easier to audit where a result came
from six weeks later.

## Does it generalise?

The evidence is still limited. I have used the thor files on four of my own projects, including a larger project with five internal
threads with a separate thor agent for each. Two researcher friends have also found the approach useful on quite different problems.
When I revisited one older project, two agents completed 35 experiments in three days.

I have turned the documents into a small set of [project templates](https://github.com/withmartian/thor/templates). There are also
[four real examples](https://github.com/withmartian/thor/EXAMPLES.md), which may be more informative than the abstract rules.

None of this process guarantees an interesting paper. One of my projects produced sound experiments and some novel findings, but the
result simply was not very exciting. A process can keep the evidence clean and the dead ends cheap. It cannot make the world yield
a profound answer.

This is a snapshot of how I work now. The process is changing as the models change and as I become better at managing them.
If you try it, I would be especially interested to hear what breaks.
