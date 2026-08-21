# <img src="images/thor-mark.png" width="40" alt=""> thor in the wild

thor was not designed in the abstract — it was extracted from real research
projects and then fed back into them. These four are worked examples of the
templates in use — from the project where thor was born, through a mature
codebase extended in a three-day sprint, to a five-thread, months-long
exploration.

> Some of these repositories are internal and become reachable as they are made
> public. Each row sketches how far that project took thor in practice.

| Repo | What it studies | How thor was used |  
| --- | --- | --- |
| [Wayfinder](https://github.com/withmartian/wayfinder) | Comparing inference-time interpretability methods — which one actually helps *your* model on *your* task | The most exploratory case: **5 concurrent threads** over ~3 months, several conjectures disproved, several findings worth publishing — thor's positive-disagreement and skeptic gates were refined here. |
| [quanta_maths](https://github.com/PhilipQuirke/quanta_maths) | Understanding addition and subtraction in transformers (paper: [arXiv:2402.02619](https://arxiv.org/abs/2402.02619)) | We added thor to this *mature* project to extend the research. Two agents produced **35 experiments in 3 days** - delivering the desired results. |
| [intent](https://github.com/withmartian/intent) | An investigation of attention-head role claims in transformers (paper: [arXiv:2606.08292](https://arxiv.org/abs/2606.08292)) | Where thor was born and refined over many experiments and ~4 months. A valid, novel paper resulted. |
| [scaling-laws-tp](https://github.com/withmartian/scaling-law-tp) | Scaling laws for Transformer Programs — weights that decompile into human-readable Python | A multi-thread adoption example where the threads share one project-wide glossary and document-rules. |
| [scaling-laws-vt](https://github.com/withmartian/scaling-law-vt) | Scaling laws for Interpretable Models. Designing new more-interpretable transformer-like model architectures. | A WIP multi-thread example with multiple humans working on the project |
| [es7](https://github.com/amir-abdullah-thoughtworks/es7) | Proof of Erdos Szekeres mathematical conjecture. | Extends Thor to a proof-focused framework. |

## What the spread shows

**It travels.** Four projects, plus two researcher friends on entirely
different problems, have used the assets — evidence that the practice is not just personal habit.

See the [long-form write-up](docs/blog.md) for the practice behind these
projects, and the [templates](README.md) to start your own.
