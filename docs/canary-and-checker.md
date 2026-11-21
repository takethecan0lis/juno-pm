# Canary and checker

Draft for the juno-pm repo; invented examples only; adapt to your team

Two controls guard the claim "this item is ready". The canary tests the digest writer. The checker tests each claim against the real files. Both exist because the writer must not grade its own work. Examples use Harbor Maps, a mapping project at the Pebble Notes team.

## The canary

The canary is an invented item planted in a test backlog that is deliberately not ready. Example: "HM-999: Add voice directions", with no beneficiary, no criteria, and the line "Open question: which languages?". It sits in a test project that real work never uses, so it cannot be mistaken for a real item.

Each run, the digest reports the canary's result. If Juno marks it ready, the digest opens with "low confidence", because the readiness judgment failed on a case with a known answer. A correct result (not ready, with the exact gaps listed) is reported in one line and nothing else changes.

## The separate checker

A second pass, run by something other than the writer (another agent, a different model, or a person), takes each ready claim and does this:

1. Open the cited file and find the cited line.
2. Compare what the claim says with what the file says.
3. Mark the item verified, or return it as "unverified" or "NEEDS CLARIFICATION" with the reason, such as "no source found" or "criterion not met".

Example: the digest says HM-014 "Save a route" has a size of 3, citing the Backlog. The checker opens the row, finds 3, and passes it. If it found "TBD", the item would return as unverified.

The bar: no item with a missing or wrong citation is shown as ready. If more than half the items fail, the digest is marked "low confidence".

## What a missing or failed check looks like

| Situation | What the digest shows |
|---|---|
| Canary shown as ready | "Low confidence" at the top |
| Canary result missing | "Canary did not run" in Not verified; never treated as passed |
| Checker did not run | Every ready claim labelled "unchecked" |
| One claim fails | That item shown "unverified", never dropped |
| File changed after the check | The claim is stale; re-check before it is trusted |

## Limits

The checker can misread a file the same way the writer did, so it lowers the risk and does not remove it. Spot-check a sample by hand. No pass bar is set until your team tests this on real items.
