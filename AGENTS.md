# Project instructions

This repo is the Roblox game **Hooked-n-Reeled** (existing Roblox place ID `78065626942509`; the place's legacy display name may still be different). Game design lives
in [DESIGN.md](DESIGN.md).

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
- `skills/roblox-build/assets/lighting-presets.luau` — five complete lighting presets.
- `skills/roblox-build/assets/style-bible.md` — fill-in template for palette/materials/scale.
- `skills/roblox-game-dev/assets/project/` — Rojo-ready vertical slice (typed remotes,
  session-locked DataService, round service, client HUD).
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
