---
title: Juno risk register and threat model (strategic view)
tags: [product-school, ai-product-management, juno, risk, threat-model]
saved: 2026-11-21
---

# Juno risk register

**What the controls unlock.** Juno can read every permitted backlog and run up to 3 spikes per run with nobody watching. The harness keeps that safe. Nothing Juno does changes a real work item, leaves the owner's files, or costs more than a set cap. Each gap below closes with a silent guard, not an extra approval step.

| Risk | What goes wrong | Likelihood / impact | Existing control | Gap | Owner |
|---|---|---|---|---|---|
| Wrong "ready" call | An unready item is approved and stalls mid-build | Medium / High | Verification: cited criteria, separate checker, "unverified" label. Permissions: Juno only recommends | The checker can misread the same file; no pass bar until the Module 5 evals | Product owner |
| Prompt injection | Text in a backlog or spike input reads like a command and is followed | Medium / High | Tools: no send, edit, delete or spend verb exists to misuse | Skill file never says project files are data, not instructions; no scan for such text | Security reviewer |
| Spike writes outside scratch | A spike changes a real file | Low / High | Tools and Permissions: scratch-only writes | Stated, not enforced; needs a path guard in the tool itself, plus a test | Engineering lead |
| Runaway cost or loop | Spike turns chain past budget | Medium / Medium | Loop: 40 calls per run, 15 turns per spike, $2.00 cap, stop after 3 failures | Caps are placeholders; the stop at the cap is untested | Product owner |
| Stale data | Old status is acted on as current | Medium / Medium | Context: live reads, 2-day stale label. Memory: expiry, corrections win | A fresh file can still be wrong; "not read" can pass for clean in a quick skim | Product owner |
| Private content leak | Restricted text reaches the digest or the public repo | Medium / High | Context: permitted list only. Memory: restricted projects never in the digest | No scan of the repo and its history for private names before publishing | Repo owner |
| Credentials | A token lands in a prompt, log or commit | Low / High | Permissions: credentials and accounts blocked | No rule that Juno runs with no token in reach; no secret scan on the repo | Security reviewer |
| Over-trust | The user stops checking | High / Medium | Verification: citations, "low confidence" banner | The hand spot-check ends at Module 5 with nothing in its place; add a sampled audit | Product owner |

## Fixed lines (never move)

1. Juno never edits a backlog, never sends or posts, and never deletes.
2. Juno never spends money or touches accounts or credentials.
3. Juno never reads restricted projects, and their content never reaches a digest or the repo.

## Not verified

- No running Juno exists. Every control is a written design.
- The scratch folder boundary, the cost caps and the checker are untested.
- GitHub token handling is an assumption. None of the documents covers how the repo is pushed or who holds the token.
- The Definition of Ready is not yet a file.
