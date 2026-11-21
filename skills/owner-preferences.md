# Owner preferences note (decision digest)

Draft for the juno-pm repo; invented examples only; adapt to your team

The decision-digest skill reads this note at the start of every run. It holds the choices that shape the digest, so the skill never has to ask you anything. If the note is missing, the skill falls back to the recommended defaults below and marks each one "default" in the digest. Example owner: the product owner of Harbor Maps, a mapping project at the Pebble Notes team.

## The thirteen choices

Fill the last column with your own value. Leave it blank to accept the default. "Named" means the decision-digest or needs-you-block skill states the choice itself; the rest are completed here so the set is whole.

| # | Choice | Recommended default | Your value | Named by the skill |
|---|---|---|---|---|
| 1 | Device | Read on a phone | | Yes |
| 2 | Reading time | 5 to 10 minutes | | Yes |
| 3 | Order | Decisions first, news after | | Yes |
| 4 | Answer channel | Answer by reply to the digest | | Yes |
| 5 | Default wait | A default takes effect after 2 days of silence | | Yes |
| 6 | Cadence | One digest per run | | Yes |
| 7 | Metrics line | None | | Yes |
| 8 | Tone | Plain words, no jargon | | Yes |
| 9 | Privacy | No private names, paths or amounts in the page | | Yes |
| 10 | Reserved decision types | Money, accounts and credentials, anything sent or posted for you, deletions, and decisions that need the owner's confirmation (accepting a spike's ready call, a larger cost, a new tool, a new data source). Never given a default | | Yes |
| 11 | Theme | Follow the device setting, light or dark | | No |
| 12 | Digest naming | `YYYY-MM-DD-harbor-maps-digest` | | No |
| 13 | Where answers go | Saved beside the digest in one answers file, read at the start of the next run | | No |

## One fixed rule

Never interview the owner during a run. The skill reads this note, uses the defaults for anything blank, and records what it assumed. A question about a preference becomes a line in the digest's Needs you block, asked once.

## How to change a line

Edit the "Your value" cell, then add a row below. Never overwrite an old row; the log is how you find out why the digest changed shape.

| Date | Choice # | Old value | New value | Changed by |
|---|---|---|---|---|
| 2026-03-02 | 2 | 5 to 10 minutes | 5 minutes | Product owner |
| 2026-03-09 | 5 | 2 days | 3 days | Product owner |

Only the owner changes a line. If the digest or an agent suggests a change, it goes in the Needs you block as a question. A change takes effect on the next run, not the current one.

## What this note does not do

It does not hold secrets, names of people, or amounts. It does not grant any permission: reserved decisions stay reserved whatever you write in the other rows.
