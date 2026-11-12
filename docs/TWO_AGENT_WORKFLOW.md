# Two-Agent Freebuff Workflow

## Goal

Allow two Freebuff agents to make useful progress at the same time without overwriting one another's work or creating incompatible systems.

## Ownership rule

Every milestone contains exactly two work packages:
- **Package A:** one bounded task with an explicit file list.
- **Package B:** a separate bounded task with a different explicit file list.

At the beginning of each milestone, choose freely which agent owns A and which owns B. The same agent does not need to keep the same specialty across milestones.

Record the assignment in the milestone checklist or a short coordination note before implementation starts.

## Non-negotiable collaboration rules

1. **One writer per file at a time.** Never let both agents edit the same file concurrently.
2. **Define interfaces first.** If A and B need to communicate, agree on module names, function signatures, data shapes, and remote contracts before coding.
3. **Shared files have an owner.** Configs, shared types, project manifests, and central entry points belong to one package in that milestone. The other agent consumes the agreed interface but does not edit that file.
4. **Separate branches or isolated worktrees when possible.** If both agents work on the same branch, they must still respect file ownership and avoid simultaneous commits that rewrite the same paths.
5. **Small commits.** Each package should commit its completed work with a clear message and list changed files.
6. **Integrate only after both packages report ready.** One integrator reviews both outputs, resolves interface mismatches, then runs the milestone checks.
7. **No silent scope changes.** If a package needs a file owned by the other package, pause and coordinate instead of editing it.
8. **Test in Studio after integration.** A successful file write or static check does not prove the Roblox experience works.

## Milestone handoff template

For each milestone, record:
- Milestone name and goal.
- Package A scope and exact owned files.
- Package B scope and exact owned files.
- Shared interface contract.
- Acceptance criteria for A and B.
- Integration owner for the milestone.
- Test checklist and known risks.

## Recommended agent cycle

1. Read the milestone and current design docs.
2. Confirm package ownership and file boundaries.
3. Agree on interfaces before implementation.
4. Work independently only within assigned files.
5. Report changed files, assumptions, and tests.
6. Integrate and resolve any contract mismatches.
7. Run checks and playtests.
8. Mark the milestone complete only when both packages pass acceptance criteria.

## Roblox Studio and GitHub source of truth

The team must choose one authoritative path for code changes before implementation. Do not let one agent push a version to Studio while the other independently changes the same scripts in GitHub without a defined sync step.

Until a formal sync toolchain is selected:
- Keep design docs and task ownership in GitHub.
- Make code changes in clearly assigned files.
- After each package, reconcile GitHub and Studio deliberately.
- Never assume an agent's local or Studio state has automatically reached the other agent.

## Definition of done

A milestone is done only when:
- Both packages meet their acceptance criteria.
- Shared interfaces match.
- No unintended overlapping file edits remain.
- Relevant syntax and integration checks pass.
- The affected player flow has been tested in Roblox Studio.
- Documentation reflects any accepted design or API changes.
