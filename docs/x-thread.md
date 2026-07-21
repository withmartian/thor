# thor — X thread

*Draft thread for launch on X. Companion to the [long-form write-up](blog.md) and
the [LinkedIn teaser](linkedin.md). Swap `github.com/withmartian/thor` for the
final URL before posting.*

---

**1/**
This past quarter, using AI agents as research assistants, I roughly tripled my
research throughput — and quality went *up*, not down.

Here's how I do it: a thread on doing great research with agents that disagree
with you. 🧵

**2/**
Research is a harder place for agents than coding. In software you can write a
test for "done." In research there's no oracle — my first guesses are usually
wrong and nothing tells me so.

So the real risk isn't buggy code. It's over-believing my own hypothesis.

**3/**
My fix: *positive disagreement.*

The human and the agent keep their beliefs in **separate** files, and are
expected to disagree. Then I pick experiments that discriminate between the two —
not ones that pile confirmation on whoever spoke first.

**4/**
Left alone, agents are agreeable. One will happily burn days (and a lot of
tokens) chasing a path I suggested, even when I'm wrong.

Writing the disagreement into the contract — *push back, propose alternatives* —
is what stops that.

**5/**
The single biggest quality win: **skeptic gates.**

A fresh agent — ideally a different vendor — reviews each experiment twice:
before launch (is the plan sound?) and after (is the verdict over-claimed?),
reading only the docs.

Cheap insurance against believing a broken result.

**6/**
None of this works without the boring part: **write it down.**

All project state lives in version-controlled Markdown. It survives crashes,
compaction, vendor swaps and reboots — and it makes the whole thing
model-agnostic. I've run it on Claude, ChatGPT and OpenCode.

**7/**
And stay a manager, not a bystander.

Agents are brilliant, fast, cheap junior *assistants* — but they lack research
taste and get tunnel vision. Set direction, review the diff, keep a human in the
loop.

**8/**
It travels: 4 of my projects, plus 2 friends on entirely different problems. One
re-run did 35 experiments in 3 days.

I've open-sourced the whole practice as templates — **thor** (Towards
Human-Oracle Research):

🔗 github.com/withmartian/thor

I'd love to hear what breaks.
