# thor in the wild

thor was not designed in the abstract — it was extracted from real research
projects and then fed back into them. These four are worked examples of the
templates in use, spanning the full range from "born here" to a light-touch
subset, and from a tidy three-day sprint to a five-thread, months-long
exploration.

> Some of these repositories are internal and become reachable as they are made
> public. Each row lists the thor documents that project actually adopted, so you
> can see how much of the framework a project needs in practice — from the full
> set down to just the shared glossary and document rules.

| Project | What it studies | How thor was used | thor docs adopted |
| --- | --- | --- | --- |
| [intent](https://github.com/withmartian/intent) | The **KID (Knowing / Intent / Doing)** lens for attention-head role claims in transformers (paper: [arXiv:2606.08292](https://arxiv.org/abs/2606.08292)) | Where thor was born and runs most completely. Many experiments over ~4 months, 2 threads. A valid, novel paper — and an honest data point that a disciplined process does not guarantee an *exciting* result. | full set (agent, both conjecture files, next-steps, results trio, claim-evidence, document-rules, glossary) |
| [quanta_maths](https://github.com/PhilipQuirke/quanta_maths) | Understanding addition and subtraction in transformers (paper: [arXiv:2402.02619](https://arxiv.org/abs/2402.02619)) | An *older* project re-run under thor to test whether the method travels. It did: 2 agents produced **35 experiments in 3 days** and delivered the additional results expected. | agent, document-rules, glossary |
| [scaling-laws](https://github.com/withmartian/scaling-laws) | Scaling laws for Transformer Programs — weights that decompile into human-readable Python | Light-touch adoption: the shared project-wide docs used to keep terminology and document discipline consistent across the work. | document-rules, glossary |
| [Wayfinder](https://github.com/withmartian/wayfinder) | Comparing inference-time interpretability methods — which one actually helps *your* model on *your* task | The most exploratory case: **5 concurrent threads** over ~3 months, several conjectures disproved, several findings worth publishing — the setting thor's positive-disagreement and skeptic gates were built for. | agent, document-rules, glossary |

## What the spread shows

- **It travels.** Four projects, plus two researcher friends on entirely
  different problems, have used the assets — evidence that the practice is not
  just personal habit.
- **Adoption is a dial, not all-or-nothing.** `thor-document-rules.md` and
  `thor-glossary.md` are the project-wide minimum; the per-topic conjecture,
  study, and results docs are added as a project's ambitions grow.
- **The process is honest about outcomes.** intent shipped a solid-but-not-thrilling
  paper; Wayfinder overturned several of its own conjectures. thor is built to
  make dead ends cheap and negatives trustworthy, not to manufacture excitement.

See the [long-form write-up](docs/blog.md) for the practice behind these
projects, and the [templates](README.md) to start your own.
