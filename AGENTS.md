# Project instructions

This repo is the Roblox game **Hooked-n-Reeled** (existing Roblox place ID `78065626942509`; the place's legacy display name may still be different). Game design lives in [DESIGN.md](DESIGN.md), with the detailed underwater feature plan in [docs/UNDERWATER_EXPLORATION.md](docs/UNDERWATER_EXPLORATION.md).

## Two-agent coordination is mandatory

Before doing project work, read [the agent coordination hub](docs/agent-coordination/README.md) and [its current dashboard](docs/agent-coordination/CURRENT.md). The two agents coordinate asynchronously through GitHub on the active branch.

- Read both agent message logs before starting/resuming work.
- Post updates and questions only in your own log: `docs/agent-coordination/messages/AGENT_A.md` or `AGENT_B.md`.
- Follow the active milestone's package ownership. One writer per file; never edit the other agent's message log.
- Do not treat proposals as decisions. Accepted shared decisions go in `docs/agent-coordination/DECISIONS.md`.
- The integration owner updates the dashboard and records handoffs.
- All project changes for this task stay on `QynlIdeas`, unless the user explicitly changes that instruction.
- GitHub notes are asynchronous coordination, not live chat. Commit messages so the other agent can read them.
- Do not claim the other agent has seen or accepted a message until there is a response in its log.

## Visual reference images are inspiration, not finished designs

**Read [docs/visual-references/README.md](docs/visual-references/README.md) and [docs/VISUAL_REFERENCE_PLAN.md](docs/VISUAL_REFERENCE_PLAN.md) before using any image in `docs/visual-references/`. This rule applies to every image in that directory, including `Fish_IDeas.png`, boat sheets, environment asset sheets, maps, underwater concepts, and future additions.**

These images are visual idea boards and art-direction references only. They are **not** final fish designs, a confirmed fish/species roster, final boat models or prices, final world geography, approved level layouts, production-ready asset specifications, or assets to copy one-to-one. In particular, `Fish_IDeas.png` communicates the intended range of fish-art direction and rarity presentation; it does not define the actual fish that must appear in the game.

When implementing:
- Treat reference images as inspiration for style, shape language, colour, mood, variety, and possible directions.
- Create original, game-appropriate designs that fit the confirmed game design, gameplay needs, performance budget, and world layout.
- Do not assume every pictured object/species/boat/landmark must exist in the game.
- Do not infer exact names, stats, rarity odds, prices, progression order, dimensions, or mechanics from a concept image.
- A concept becomes an approved design only when the user explicitly approves that specific design or the relevant written specification confirms it.
- Even an approved concept image is still not a production Roblox model. Build and optimise the actual asset separately.
- If an image conflicts with a confirmed written design decision, follow the written decision and flag the conflict rather than silently changing the game.

Use the status meanings defined in the visual-reference README: **Inspiration → Direction approved → Design approved → Implemented**. Do not advance an image's status without evidence or user approval.

The full game includes both surface and underwater ocean exploration. The current M0 priority is still the master surface-ocean map; account for future seabed depth changes and reserve possible dive-site anchors, but do not build the full diving feature until M17. Underwater exploration must not require sonar, scanners, tracking devices, or research gadgets.

## Roblox skills — always use these

Two full skills are bundled in `skills/`. **Read the relevant `SKILL.md` before doing Roblox
work.** Do not work from memory of them, and do not skip them because a task looks small.

| Skill | Use it for | Start at |
|---|---|---|
| `skills/roblox-build/` | Anything about how the place **looks**: maps, buildings, props, terrain, lighting, materials, set dressing, Studio MCP build passes, screenshots, Creator Store assets. | `SKILL.md`, then `assets/style-bible.md` |
| `skills/roblox-game-dev/` | Anything about how the game **works**: Luau, server/client architecture, remotes, DataStores, economy, shops, UI, monetization, playtesting, Rojo, publishing. | `SKILL.md`, then `references/architecture.md` |

Reusable material that ships with them:

- `skills/roblox-build/assets/build-utils.luau` — tagged part/model helpers, grid snapping,
  provenance tagging, `Build.clearAll()`. Use before any build pass.
- `skills/roblox-build/assets/lighting-presets.luau` — five complete Lighting presets.
- `skills/roblox-build/assets/style-bible.md` — fill-in template for palette/materials/scale.
- `skills/roblox-game-dev/assets/project/` — Rojo-ready vertical slice (typed remotes,
  session-locked DataService, round service, client HUD).

The bundled Rojo project is a **generic teaching example** with a sample round loop, coin pickup, and shop. It is not the Hooked-n-Reeled game implementation. Do not copy it wholesale or leave round-based gameplay in the fishing game; reuse only the architecture patterns that fit the approved fishing design.
- `references/` in each skill — deeper craft, performance, testing and shipping detail.

A task usually needs both: build for the scene, game-dev for the systems behind it.

## Non-negotiables taken from those skills

- **The server owns state; the client owns presentation.** Currency, inventory, catches and
  roll results are decided server-side. Validate type, range, ownership, phase and cooldown on
  every remote, and rate-limit per player.
- **Verify by looking.** Every build pass ends with `screen_capture` from a deliberate camera
  position. Never describe a build as good without having seen it, and say plainly when a
  visual check was not possible.
- **Build in passes** (massing → architecture → materials/lighting → set dressing), each one
  small and reviewable, with a `ChangeHistoryService:SetWaypoint()` before big stages.
- **Tag everything created** with `AgentBuild = true` and build under a single folder so it can
  be reviewed or removed in one action.
- **Never publish or save over the place**, never delete or move instances you did not create,
  never edit gameplay scripts as part of a build pass.
- `task.wait` / `task.spawn` / `task.delay`, never legacy `wait()`/`spawn()`. `--!strict` on
  shared and service modules. Cache service references at module top.
- Test like it's multiplayer: two clients, mobile viewport, rejoin, and a remote fired with
  garbage arguments. Report what was verified and what was not.
