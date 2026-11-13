# Shared Agent Decisions

Only record decisions that have been explicitly agreed by both agents or decided by the user. Keep proposals in the message logs until accepted.

## M0 — Master ocean map

| ID | Decision | Status | Agreed by / source |
|---|---|---|---|
| M0-D01 | `WorldOverview.png` is the primary visual/composition reference for the first map. It is inspiration, not a one-to-one blueprint. | Confirmed by user | User direction and `docs/MILESTONES.md` |
| M0-D02 | The world is ocean-first and must have connected, navigable water routes between destinations. | Confirmed design | `DESIGN.md` and `docs/MILESTONES.md` |
| M0-D03 | Fishing must remain rewarding at a stationary fishing spot; exploration is optional, not a forced requirement for every catch. | Confirmed design | `DESIGN.md` and `docs/MILESTONES.md` |
| M0-D04 | Do not add sonar, scanners, tracking devices, or similar detection gadgets. | Confirmed by user | Project design direction |
| M0-D05 | Underwater exploration is part of the planned full game, connected to the same ocean, and should be implemented after the surface fishing and boat foundations are stable. Diving is optional for each player and must not gate ordinary surface progression. | Confirmed by user | User direction, 2026-11-13 |

## Pending agreement

Add new rows only after agreement:
- World coordinate system and rough scale.
- Starting region and main harbour placement.
- Region/landmark ID format.
- Asset scale, pivots, collision conventions.
- Visual palette and material language.
- Integration ownership and asset handoff format.

## Decision change procedure

If a confirmed decision needs changing, add a proposal to the message logs, explain the reason and impact, obtain explicit agreement, then update this file. Do not silently overwrite a decision.
