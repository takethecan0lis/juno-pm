# Permitted projects

Draft for the juno-pm repo; invented examples only; adapt to your team

Juno reads only projects on a permitted list. A project not named there is never opened, even if its folder is next door. This page shows an example list and how it changes. Examples use the Pebble Notes team.

## Example lists

| Project | List | Why |
|---|---|---|
| Harbor Maps | Permitted | Active product work, no sensitive data |
| Pebble Sync | Permitted | Shared roadmap, public notes |
| Pebble Labs | Permitted | Experiments, scratch work only |
| Harbor Payroll | Restricted | Holds staff pay data |
| Pebble Legal | Restricted | Contracts under review |

A restricted project is never read, and its content never reaches a digest, a spike or the repo. Its name may appear in the coverage line only as "restricted, not read".

## Adding or removing a project

1. The product owner writes the change in the list file, with the date and a one-line reason.
2. A project is added only by the owner, never by a spike, a digest or an agent suggestion. A suggestion goes into the Needs you block.
3. A restricted project moves to permitted only after the owner confirms in writing that its files hold nothing private.
4. Removing a project takes effect at once, on the next run.

When in doubt, a project is restricted.

## How "not read" shows in a digest

The coverage line reads, for example: "4 of 5 permitted projects read; 1 not read." Each unread project gets a reason word:

| Reason word | Meaning |
|---|---|
| missing | A journal file does not exist |
| unreadable | The file exists but could not be opened |
| stale | Read, but not edited for more than 2 days (labelled, not dropped) |
| capped | The run hit a call, time or cost cap before reaching it |
| restricted | On the restricted list, never opened |

A project that was not read never shows as clean, and a run that hit a cap starts the digest with an "Incomplete" line naming the cap. A "not read" project can hide ready work, so treat a quiet digest with several of them as unknown, not as good news.
