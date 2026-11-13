# Two-Agent GitHub Collaboration Workflow

## Goal

Allow two Freebuff agents to work in parallel while sharing decisions, questions, progress, and handoffs without overwriting one another.

**The shared communication workspace is [docs/agent-coordination/](agent-coordination/README.md).** Read its README and CURRENT dashboard first. This file explains the collaboration rules; the coordination folder is where the actual conversation and status are recorded.

## GitHub is the asynchronous shared workspace

This is not live chat. Each agent posts a committed update and the other agent reads and replies on its next pass.

- Agent A writes only to `docs/agent-coordination/messages/AGENT_A.md`.
- Agent B writes only to `docs/agent-coordination/messages/AGENT_B.md`.
- Append entries; do not rewrite or delete earlier messages.
- Use dated headings and the message types `UPDATE`, `QUESTION`, `PROPOSAL`, `BLOCKER`, or `HANDOFF`.
- Always state what response/action is needed and whether work can continue meanwhile.
- The integration owner maintains `CURRENT.md`, accepted decisions in `DECISIONS.md`, and handoff reports.
- Use separate proposal files for decisions that need a longer comparison.

## Ownership rule

Every milestone contains exactly two work packages:
- **Package A:** one bounded task with an explicit file list.
- **Package B:** a separate bounded task with a different explicit file list.

At the beginning of each milestone, choose freely which agent owns A and which owns B. The same agent does not need to keep the same specialty across milestones. Record the agreed assignment and exact file ownership in the coordination dashboard before implementation.

## Non-negotiable collaboration rules

1. **One writer per file at a time.** Never let both agents edit the same file concurrently.
2. **Define interfaces first.** If A and B need to communicate, agree on module names, function signatures, data shapes, coordinate conventions, and remote contracts before coding.
3. **Shared files have an owner.** Configs, shared types, project manifests, central entry points, and the coordination dashboard belong to one named owner for that milestone.
4. **Use the active branch.** For this project, work on `QynlIdeas` unless the user explicitly changes it.
5. **Separate branches/worktrees when practical.** If both agents work on one branch, respect the exact file ownership list and avoid simultaneous commits that rewrite the same paths.
6. **Small commits.** Each package should commit completed work with a clear message and list changed files.
7. **Integrate only after both packages report ready.** One integrator reviews both outputs, resolves interface mismatches, then runs the milestone checks.
8. **No silent scope changes.** If a package needs a file owned by the other package, pause and coordinate instead of editing it.
9. **Test in Studio after integration.** A successful file write or static check does not prove the Roblox experience works.
10. **Do not claim communication succeeded until the other agent has replied.** A posted note is pending until acknowledged.

## Recommended agent cycle

1. Read `AGENTS.md`, the coordination hub README/dashboard, both message logs, the active milestone, and relevant design/skill documents.
2. Post a check-in in your own message log. Read the other agent's latest check-in.
3. Agree on package ownership, exact file boundaries, shared interfaces, and an integration owner.
4. Record accepted shared decisions in `DECISIONS.md`.
5. Work independently only within assigned files.
6. Post progress/blockers in your own log. Respond to the other agent in your own log.
7. Submit a package handoff using [the template](agent-coordination/handoffs/TEMPLATE.md).
8. Integrate, test, and update the dashboard.
9. Mark the milestone complete only when both packages pass the acceptance gate.

## Roblox Studio and GitHub source of truth

The team must choose one authoritative path for code changes before implementation. Do not let one agent push a version to Studio while the other independently changes the same scripts in GitHub without a defined sync step.

Until a formal sync toolchain is selected:
- Keep design docs, package ownership, decisions, and communication in GitHub.
- Make code changes in clearly assigned files.
- After each package, reconcile GitHub and Studio deliberately.
- Never assume an agent's local or Studio state has automatically reached the other agent.
- Store screenshots or clips as links/evidence in the handoff; do not claim Studio verification without it.

## Definition of done

A milestone is done only when:
- Both packages meet their acceptance criteria.
- Shared interfaces match.
- No unintended overlapping file edits remain.
- Relevant syntax and integration checks pass.
- The affected player flow has been tested in Roblox Studio.
- Documentation reflects accepted API/design changes.
- The dashboard and handoff report are updated.
