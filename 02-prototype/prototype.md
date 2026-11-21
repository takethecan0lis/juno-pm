# Prototype · Juno

> Module 2 · Prototype the Idea Worth Building. The working build that tests your idea, made with your build tool of choice.

## Prototype link

https://claude.ai/artifact/QLkM3emaYbruULrwMqnXBT

Built with Claude Code and published as a Claude artifact. It uses invented sample data only, never real project names.

## What it demonstrates

The one flow it proves: Juno's daily digest, a ranked queue of work that looks ready to run without me. Each item shows its WSJF score, its source file and item ID, and how many Definition of Ready criteria it meets. Opening an item shows its purpose, context, objective and risk, with a plain "safe to run" or "run with care" call. Separate sections list the actions that need me (with steps) and the spikes Juno ran (with the question and findings).

Assumption tested: I can approve or reject each item in one decision when it shows its sources and its risk. The prototype has not yet been tried by anyone but me.

This matches the skill file: Juno recommends and never edits, sends or deletes, items that need my input are separated out, and unverified or unreadable items are labelled, never shown as clean.

## Debrief

- **What worked:** Showing the source and the risk next to every item made each call easy to check. Expandable rows kept the queue short, and the "Needs you" section with a steps toggle kept the bulk hidden until wanted.
- **What broke / felt like a toy:** The first version looked like a basic template, and it was not obvious that rows could open. The data is invented, and the buttons do not save anything. Nothing is read from a real backlog.
- **What I'd change next pass:** Connect it to real backlog files, show readiness from the Definition of Ready checks, and add a way to answer an action from the page. A partner's cold read is still to come.
