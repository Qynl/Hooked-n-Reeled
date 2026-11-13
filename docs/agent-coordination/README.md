# Agent Coordination Hub

This folder is the shared asynchronous workspace for the two development agents working on Hooked-n-Reeled.

**Start here before doing any work:** read this file, then `CURRENT.md`, the active milestone in `docs/MILESTONES.md`, and your own message log under `messages/`.

## What this is

GitHub is the shared memory and handoff point for the agents. It is not live chat: each agent posts a note, commits it, and the other agent reads and responds on its next pass. Keep messages concise, specific, and actionable.

## Folder map

- `CURRENT.md` — active milestone, assignments, blockers, and next action. This is the dashboard.
- `DECISIONS.md` — decisions both agents have agreed on. Only accepted decisions belong here.
- `messages/AGENT_A.md` — Agent A's append-only communication log.
- `messages/AGENT_B.md` — Agent B's append-only communication log.
- `proposals/README.md` — how to propose changes that need agreement.
- `handoffs/TEMPLATE.md` — package completion and integration report template.

## Communication protocol

1. Read the latest dashboard and both message logs before starting or resuming work.
2. Write messages only to your own log. Do not edit the other agent's log.
3. Add a dated entry with a clear type: `UPDATE`, `QUESTION`, `PROPOSAL`, `BLOCKER`, or `HANDOFF`.
4. If you need the other agent, state exactly what you need, why, and whether work can continue meanwhile.
5. The other agent replies in its own log and references the original entry date/heading.
6. Never treat a proposal as an accepted decision. Accepted shared decisions are copied into `DECISIONS.md` by the integration owner after both agents agree (or after the user decides).
7. Update `CURRENT.md` when ownership, status, blockers, or the next action changes. Avoid editing it simultaneously; the integration owner owns the dashboard for the current milestone.
8. Commit communication updates so the other agent can see them. Include a useful commit message.

## File ownership and conflict prevention

- One writer per file at a time.
- Agent A owns only `messages/AGENT_A.md`; Agent B owns only `messages/AGENT_B.md`.
- The milestone package assignment defines production-file ownership.
- The integration owner maintains `CURRENT.md`, `DECISIONS.md`, and final handoff records.
- If two agents need the same file, stop and agree on an owner or split the interface into separate files. Never race edits to one file.
- Do not use this folder to bypass the milestone scope or to silently change confirmed game design.

## Message format

Use this format in your own log:

```md
## YYYY-MM-DD HH:MM UTC — TYPE — Short subject

**To:** Agent A / Agent B / Both

**Context:** What happened?

**Message:** The specific update, question, proposal, or blocker.

**Needed from the other agent:** Exact response/action, or "None".

**Can work continue?** Yes / No / Partially
```

## Escalation

Ask the other agent first for implementation/interface questions. Ask the user when a decision changes the game direction, player experience, economy, visual identity, or confirmed scope. Do not invent an answer just to keep moving.

## Current starting point

The active task is **M0 — Create the master ocean map**. The primary visual reference is `docs/visual-references/01-world/WorldOverview.png`. Read the detailed M0 instructions in `docs/MILESTONES.md`. The agents must coordinate the map scale, coordinate system, region names, landmark list, asset scale, and handoff before building in parallel.
