---
title: Juno product breakdown and business hypothesis
tags: [product-school, ai-product-management, juno, jtbd, hypothesis]
saved: 2026-11-21
---

Numbers in this file come from the PRD or the prototype unless the text says "assumption". The prototype's items, projects and figures are sample data, not measurements.

# 1. The value of a product like Juno

A product leader who runs many projects has a queue problem, not a work problem. Items that already meet the Definition of Ready sit untouched because nobody has the hours to open every backlog and check. Items that are one question short of ready stay that way for the same reason. The cost is idle capacity: a team that could start on Monday starts three weeks later, and the leader never sees the delay because it is made of things that did not happen.

Juno removes the checking. It reads every permitted backlog on each run, says which items are ready and why, runs small scratch-only spikes on the near misses, and hands back one digest ranked by WSJF. The leader's job shrinks from searching to deciding.

What does not solving this cost? Three things, in order of size:
- Time to start. Ready work waits for a human to notice it.
- Attention. The leader spends scarce hours on the scan instead of the calls only they can make.
- Wrong starts. When the scan is rushed, an item that was not ready gets approved and stalls mid-build.

A general chatbot could answer "what is ready?" if you pasted every backlog into it. It would be less valuable for four reasons, and the PRD builds each one in on purpose:
1. It cannot be trusted to read live. Juno fetches files on every run, labels anything older than 2 days as stale, and lists an unreadable project as "not read" rather than clean.
2. It cannot show its work to a standard. Every Juno "ready" call cites a source file and each Definition of Ready criterion, and a separate checker compares those claims to the files. Anything that fails is shown as "unverified", never dropped and never called ready.
3. It cannot be given safe autonomy. Juno's spikes run unattended because the harness caps them (15 turns, 3 per run, about $0.50 each, scratch folder only). A chatbot has no such edge, so the human has to supervise every step, and the time saving disappears.
4. It cannot be wrong cheaply. Juno has no edit, send, delete or spend verbs. A bad call costs one rejected line in a digest and changes nothing in the real backlog.

My position: the value is in the bounds, not the model. A leader will hand a bounded assistant the first pass over every backlog. They will not hand it to a free-roaming one, and the free-roaming one is the only kind that saves no time.

# 2. Who it is for

**Primary user: the portfolio product leader.** They own priorities across several projects and approve what starts. They are expert in their own domain and short of hours, so they will not read raw backlogs at scale but will read a ranked list with reasons. They are skeptical of AI output because they have been burned by confident wrong answers, and they trust only what they can trace to a file. They want to say yes or no quickly, in one place.

**Downstream beneficiaries**

| Who | What they get |
|---|---|
| Delivery teams | Ready work reaches them sooner, and items arrive with purpose, context and objective already stated |
| Project owners | A named reason when an item is held back (for example, acceptance criteria are missing), so they know what to fix |
| An approver, where the leader is not the final one | A single page with risk and rollback stated, so the decision is faster |
| The leader's future self | The last 4 digests and the spike log, so the same question is not asked twice |

The primary user buys the value. The teams and approvers feel it as less waiting.

# 3. Jobs to be done for the primary user

I have written the jobs that occur in a normal week, and I have not padded them to match each other. Functional jobs are the largest group because the product is a work tool; the emotional and social jobs are fewer and, I think, matter more to adoption.

**Functional**

1. When a new week starts and I have many backlogs I have not opened, I want to see which items are ready to start without me, so I can release work to teams today instead of next sprint.
2. When I look at a ready-looking item, I want to see why it counts as ready, with each criterion tied to a file, so I can approve it in one decision without re-reading the backlog.
3. When two or more items compete for the next slot, I want them ranked by economic value, so I can pick the order without running the arithmetic myself.
4. When an item has no WSJF score, I want an estimate with its inputs shown, so I can correct a number instead of building one from nothing.
5. When an item is one question short of ready, I want that question investigated in a safe sandbox, so I can learn the answer without anyone touching the real work.
6. When Juno cannot finish something without me, I want the exact action and its steps in one list, so I can clear a blocker in minutes.
7. When a call looks wrong, I want to say "this was not ready" once and have Juno remember it, so the same mistake does not come back next run.
8. When I run this on a schedule, I want to know what it cost and how long it took, so I can keep it inside a budget.

**Emotional**

9. When I hand a first pass to an assistant, I want to know it cannot edit, send, spend or delete, so I can stop worrying about what it did while I was away.
10. When I open the digest, I want a clear count of what needs me and what does not, so I can end the review feeling finished rather than behind.
11. When a source could not be read, I want that said plainly, so I never mistake silence for "all clear".

**Social**

12. When I tell a team or an approver that something is ready, I want to point to evidence, so my call holds up when someone challenges it.
13. When I explain why one item went ahead of another, I want a ranking with visible inputs, so the order reads as reasoned and not as preference.

**Pains**
- Backlogs are many and each is only partly current.
- "Ready" is judged by feel, and the criteria are applied unevenly.
- Spikes are cheap to run but expensive to remember to run.
- A confident wrong answer from an AI costs more trust than no answer.
- Every hand-off to a human adds a wait.

**Gains**
- Ready work starts sooner.
- One decision per item, with the reason attached.
- The leader's time goes to calls that need judgment.
- A visible record: what was read, what was not, what it cost.
- Confidence that nothing was changed behind their back.

# 4. Product breakdown

| Capability | What it does | Job served | Harness surface |
|---|---|---|---|
| Ranked digest | One page: ready items ranked by WSJF, a "Needs you" list, spikes, "Not read" notices, run footer | 1, 3, 10, 13 | Tools (draft_digest); Memory (last 4 digests) |
| Readiness check | Tests each item against the 5 criteria shown in the prototype (outcome clear, acceptance criteria, no open dependencies, sized, no input needed) | 1, 2, 12 | Context (backlog, journal, decisions); Verification |
| Item card | Purpose, context, objective and a risk note with rollback, expanded on demand | 2, 12 | Tools (draft_digest) |
| WSJF estimate | Uses the recorded score if present; otherwise scores value, time criticality and opportunity or risk reduction over job size, labelled an estimate with inputs | 3, 4, 13 | Tools (estimate_wsjf) |
| Spikes | Scratch-only research, analysis or prototype on near-ready items; findings labelled evidence or guess; can only recommend, never mark ready | 5 | Tools (recommend_spike, start_spike, write_spike_report); Loop (15 turns, 3 per run); Permissions |
| Actions that need you | Numbered actions with steps, for example a missing file or an open spike question | 6, 10 | Loop (escalation after 3 failed calls or questions only the user can answer) |
| Verification and labelling | Separate checker compares claims to files; failures show as "unverified" or "NEEDS CLARIFICATION"; "not read" for unreachable projects; "low confidence" if over half fail | 2, 9, 11, 12 | Verification |
| Corrections memory | The user's "not ready" overrides stored output for 90 days | 7 | Memory |
| Run limits and footer | 6 calls per project, 40 per run, under 10 minutes, under $2.00, actual cost printed | 8, 9 | Loop; Permissions |
| Hard refusals | No backlog edits, sends, deletes, spend or account access | 9 | Permissions (write and send blocked) |

Where the rows are thin: the PRD states the 5 criteria only through the prototype, and the Definition of Ready text itself is not yet a file. The breakdown assumes the prototype's list until it is.

# 5. Business hypothesis statement

**Hypothesis**

We believe that Juno, a harness-bounded associate PM that reads permitted backlogs and delivers one ranked, cited digest of ready work, will deliver faster starts on ready work and fewer leader hours spent scanning backlogs for a portfolio product leader, and earlier, better-stated work for the teams and approvers downstream. We will know we are right when the leader accepts most digest items as truly ready, in one decision each, and the wait between "ready" and "started" shrinks.

**Value:** Time to start falls, and the leader's attention moves from searching to deciding.

**Beneficiary:** The portfolio product leader first. Delivery teams, project owners and approvers second.

**Key assumptions to test**

| # | Assumption | How to test |
|---|---|---|
| A1 | Ready work does sit idle because nobody checks, rather than because it is blocked for other reasons | Count ready items found in the first run and ask the leader how long each had been waiting |
| A2 | The 5 criteria in the prototype match how the leader actually judges ready | Compare Juno's "ready" calls to the leader's own verdicts on a golden set |
| A3 | A cited, checked call is enough for the leader to decide without opening the backlog | Observe whether the leader opens source files before accepting |
| A4 | Scratch-only spikes produce findings that change a call often enough to justify their cost | Track how many spikes move an item to ready or rule it out |
| A5 | A run stays inside 10 minutes and $2.00 across the real number of projects | Read the digest footer on each run |

**Leading indicators.** Every figure below is an assumption unless the cell names a file. No baseline has been measured yet; the first digest run sets it.

| Indicator | Baseline | Target | Source |
|---|---|---|---|
| Share of digest "ready" items the leader accepts | None recorded (the PRD says "most" without a number) | At least 80% (assumption) | Human rubric, Module 5 |
| Decisions per accepted item | Not measured (assumption: more than 1, because the leader re-reads the backlog) | 1 | Observation |
| Leader minutes per review | Not measured (assumption: 60 or more by hand) | Under 15 (assumption) | Self-report |
| Days from "ready" to "started" | Not measured | Falls against the first-run baseline (assumption) | Backlog dates |
| Run time and cost | None; targets are set | Under 10 minutes and $2.00 per run | PRD |
| Items shown "ready" without a full citation | None | 0 | PRD verification bar |
| Items the leader later reverses as "not ready" | Not measured | Under 10% (assumption) | Corrections memory |

**What would prove it wrong**
- Acceptance stays under about half after two rounds of tuning the skill file and criteria (assumption: the threshold). Then Juno's readiness judgment is not good enough to save any checking.
- The leader opens the source file for most accepted items. The citations are not buying trust, so the time saving is not real.
- Ready work was never idle. If A1 fails, the problem Juno removes is not the problem.
- Spikes rarely change a call. Then the supervised-agent half of the split archetype costs more than it returns, and the product should reduce to a copilot digest.
- A single unverified item is shown as ready and the leader acts on it. That is a trust failure, not a metric miss.

# 6. Risks and open questions

| # | Item | Owner |
|---|---|---|
| 1 | Where the Definition of Ready lives, and whether the 5 prototype criteria match it. The PRD marks it "draft, not adopted". | Drew |
| 2 | No baseline exists for the success measure, so the hypothesis cannot be scored. Set a target accept rate and take a first measurement. | Drew |
| 3 | Spike limits and the $2.00 cap are placeholders until Module 4. Turns multiply cost, so spikes are the cost risk. | Drew, with Module 4 results |
| 4 | Keep the skill file aligned with the PRD: spikes are allowed only inside scratch-only limits, and the hard refusals and the citation rule are stated. | Drew |
| 5 | Before submission, search the public repo and its history for private names and for references to rules the public cannot see. | Drew |
| 6 | A wrong "ready" call that survives the checker, because the checker misreads a file. A second checker is not specified. | Drew, via the Module 5 evals |
| 7 | Spikes run unattended on a permission change made on 2026-11-21. If the scratch boundary leaks, the "never changes a real item" promise breaks. Test the boundary before shipping. | Drew; a security review before any real use |
| 8 | Stale and partial data: a file under 2 days old can still be wrong, and a "not read" project hides its ready work. The leader may over-trust a clean-looking digest. | Drew |
| 9 | The prototype has no cold-read debrief from a second person, which the course brief requires. | Drew |
| 10 | The three PDFs and the rubric text were not read for this file, so the criteria for grading this hypothesis are unchecked. | Drew |

Recommendation: fix items 1 and 2 first. Without a Definition of Ready file and a baseline accept rate, the hypothesis is a claim with no test.
