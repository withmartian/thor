# Next Steps (thor-next-steps.md)

Ranked, current-facing agenda. This records what to do next, not the history of
what was done. Re-rank after each meaningful result instead of appending notes.
Delete completed entries (their trail lives in the study note and results
ledger) and stay within the agenda entry cap from the agent contract's project
config — exceeding it is a doc bug.

## Ranking logic

- `<state the rules that govern ranking — e.g. prefer experiments that
  invalidate large search-space areas, or discriminate between conjectures;
  prefer breadth over depth until a conjecture is strongly evidenced>`

## Ranked queue

| Priority | Status | Next step | Information it would produce | Which belief it updates | Done when |
| --- | --- | --- | --- | --- | --- |
| 1 | Ready | `<the experiment>` | `<what we'd learn>` | `<Cxx / Axx>` | `<criterion>` |
| 2 | Blocked | `<the experiment>` | `<what we'd learn>` | `<Cxx / Axx>` | `<criterion>` |

## Frozen lines

Each freeze carries a classification (`question answered` / `question failure` /
`instrument failure`) and an explicit reopen condition. An `instrument failure`
freeze triggers the outside-view sweep from the agent contract.

- `<line>` — `<classification>`: `<one-line read>`. Reopen only `<condition>`.

## Deliberately paused

- `<tempting lines we are NOT doing, and why>`
