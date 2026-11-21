# Definition of Ready (illustrative)

Draft for the juno-pm repo; invented examples only; adapt to your team

Illustrative only. Your team signs its own. The point of a Definition of Ready is that a builder could start an item without asking anyone anything, and that the claim "ready" can be checked against files rather than felt. The examples use Harbor Maps, a mapping project at the Pebble Notes team.

## The five criteria

Each criterion has a pass test, a fail test, and the evidence the ready call must cite.

| Criterion | Pass | Fail | Evidence cited |
|---|---|---|---|
| Outcome clear | One beneficiary and one observable change | No beneficiary, or the change cannot be seen | The item's outcome line |
| Acceptance criteria | At least one Given, When, Then with a Then someone can observe | Criteria say "works well" or are missing | The item's criteria, quoted |
| Sized | A size value, or "n/a" with a reason | No size, or "TBD" | The size field |
| No input needed | No open question in the item and none waiting on the owner | A line such as "Open question: does it sync offline?" | The item text and the open asks list |
| No open dependencies | No open blocked-by link and no Blocked flag | A named item it waits for is not finished | The links field and status |

Example: "Show a saved route on the Harbor Maps home screen" fails "No input needed" because the row says "Open question: do saved routes sync?".

## The three outcomes

- **Ready.** All five met, each cited. The owner accepts it in one decision.
- **Ready after a spike.** One or two criteria fail because research could answer them, for instance size or a dependency. Recommend a spike that names the criterion it targets. A spike may recommend "ready"; only the owner accepts that.
- **Not ready.** Anything else, including a question only the owner can answer. List the exact gap. Partial passes never count as ready.

## The small autonomous lane (illustrative)

For one-session, reversible work: an outcome line, one Given and Then, and an undo line (or "no-op"). Example: fixing a stale comment in a Harbor Maps settings file passes with the Then "the comment matches the code". If the item touches data, it cannot use the lane.

## Ready calls expire

A call that is not pulled within 7 days, or whose cited file changes, is no longer ready. No citation means not ready. The 7 days is a guess until your team measures it.

## What this does not check

Whether "clear" and "observable" are met rests on a second reader's judgment. Nothing here tests whether the item is worth doing; value is scored elsewhere. It has not been tried on a real backlog.
