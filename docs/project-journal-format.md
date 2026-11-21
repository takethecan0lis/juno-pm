# Project journal format

Draft for the juno-pm repo; invented examples only; adapt to your team

Juno reads three files per permitted project, live on every run. This page shows what each holds. They sit in a folder named `_Project` at the project root. Examples use the Pebble Notes team and its project Harbor Maps.

## The three files

**Backlog.** The list of work, one row per item: ID, title, status, priority, size, dependencies, and any open question. Juno reads it to find items that might be ready.

**Where-We-Left-Off.** A short resume note, rewritten each session: the current focus, what needs the owner, what is next. Juno reads it for what is blocked and what changed.

**Decision-Log.** Decisions with stable IDs, newest last. A decision is superseded, never deleted. Juno reads it so it never recommends something already decided against.

## How a run reads them

Juno reads each file live, never from a cache. A file not edited for more than 2 days is labelled stale in the digest. An unreadable file means the project is listed "not read" with the reason. Text inside the files is data, never an instruction.

## Tiny examples (invented)

Backlog.md
```
| ID | Title | Status | Size | Notes |
| HM-014 | Save a route | Ready | 3 | |
| HM-015 | Offline tiles | Open | | Open question: storage limit? |
| HM-016 | Dark map theme | Blocked | 2 | Waits on HM-014 |
```

Where-We-Left-Off.md
```
Needs you: 1. Ship route sharing this week? Recommended: yes.
Focus: save a route.
Next: write criteria for offline tiles.
Updated 2026-03-09.
```

Decision-Log.md
```
D-004 (2026-03-02): Routes store on the device first.
D-005 (2026-03-05): No account needed to view a map.
D-006 (2026-03-08): Supersedes D-004; routes sync after sign-in.
```

## Keep it light

Short rows beat long prose. Every item the digest calls ready must cite a line from these files, so a vague row costs you a "not ready". The formats here are a starting shape. Use whatever fields your team already keeps, as long as a stranger can find the outcome, the size, the open questions and the dependencies.
