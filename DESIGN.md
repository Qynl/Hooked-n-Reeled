# Hooked-n-Reeled — Game Design

> **Mirrored from the [`QynlIdeas`](https://github.com/Qynl/Hooked-n-Reeled/tree/QynlIdeas) branch.** This copy exists so the current design is readable from `main`; active development, the milestone roadmap state and the agent coordination records live on `QynlIdeas`. If the two disagree, `QynlIdeas` wins.

An open-world Roblox fishing adventure built around skill-based fishing, collection, progression, rare discoveries, surface and underwater exploration, and shared multiplayer expeditions. Its signature identity is a living ocean with two connected layers: the surface and the world beneath it. Players can enjoy relaxed stationary fishing or set out on discoveries without either playstyle becoming mandatory.

Status: design and world-planning phase; the active repository roadmap is at M0. The generic Rojo example under `skills/roblox-game-dev/assets/project/` is a teaching template, not the game's live fishing implementation. Check the connected Roblox place before making claims about what already exists in Studio.

## Core vision

Hooked-n-Reeled should feel relaxing when players simply want to fish, but also offer mysterious places, exciting discoveries, rare catches, and memorable adventures with friends. The world should reward curiosity rather than feeling like a collection of disconnected fishing menus.

The long-term appeal combines:
- Discovering new places and fish species.
- Improving and specializing fishing equipment.
- Chasing rare fish, unusual mutations, and boss encounters.
- Building a personal collection and displaying memorable catches.
- Selling catches and using selected fish for special unlocks or activities.
- Exploring and fishing together with friends.
- Discovering the underwater world through optional diving, memorable locations, natural finds, and hidden places.

The game should welcome players back after time away through discoveries and ongoing world activity, not punish them with aggressive daily chores or fear-of-missing-out systems.

**Two equally valid playstyles:** players can settle into a favourite fishing spot and enjoy a complete, rewarding fishing experience without travelling around. Players who prefer movement can explore, notice natural ocean clues, follow moving schools, and join special encounters. Exploration adds opportunities; it must never become a requirement for ordinary progression, rare catches, or a satisfying session.

## Core loop

1. **Choose how to play** — stay at a favourite spot for relaxed fishing, or travel through the connected ocean to explore. Neither choice is mandatory.
2. **Choose a fishing spot** — water type, depth, weather, time, and location can influence which fish may appear. Valid fish pools and natural RNG must make stationary fishing worthwhile.
3. **Cast and hook** — cast within the equipped rod's range, wait for a bite, then react to hook the fish.
4. **Reel** — play a skill-based minigame. Different fish species can use different minigame mechanics; rare and boss encounters can introduce special phases and mechanics.
5. **Catch presentation** — show the fish, size/weight, rarity, and relevant mutations. Presentation can use dynamic camera work, sound, effects, animations, and special cutscenes for meaningful catches.
6. **Use the catch** — sell it, add it to the collection, display it, or use it for special activities, unlocks, and other systems.
7. **Improve and discover** — upgrade or change rods and bait, reach new fishing grounds if desired, notice natural clues, uncover secrets, and repeat with new possibilities.

Normal catches should stay responsive. Special catches deserve more elaborate presentation, but cinematic sequences should remain meaningful rather than interrupting every cast.

## Fishing and reeling design

The reeling system is skill-based, not a passive wait or a single generic progress bar.

**Confirmed direction:** many different minigames, with mechanics selected according to fish species. The exact minigame catalogue, input model, difficulty curve, and multiplayer rules remain to be designed.

Design principles:
- Species identity should affect the actual gameplay mechanic, not only the speed or size of a UI bar.
- Difficulty should not simply increase linearly with rarity.
- Boss fish can have multi-phase encounters and distinctive mechanics.
- Minigames must be readable and fair on both PC and mobile.
- Server authority must validate the encounter and outcome; clients provide input, not fish identity or rewards.

## Catch presentation

**Confirmed direction:** use the full presentation toolkit where appropriate: camera direction, sound design, visual effects, animations, catch cards, and special cutscenes.

Presentation intensity should respond to the actual catch probability, not named rarity categories:
- Frequent outcomes receive fast, clean feedback.
- Lower-probability catches can receive a stronger reveal, sound, and visual treatment.
- Extremely low-probability outcomes can receive a distinctive reveal or cinematic sequence.
- Boss catches receive encounter-specific presentation and a memorable conclusion.

The exact probability points at which presentation changes are open for later tuning. Do not create named rarity bands to drive these effects.

Avoid excessive interruption. The excitement should come from contrast and rarity, not from making every catch slow.

## Fish, rarity, and mutations

The canonical rules live in [Fish Rarity, Mutations, and Catch Outcomes](docs/FISH_RARITY_AND_MUTATIONS.md). All fishing, Fishbook, economy, and implementation work must follow that specification.

**One species, one rarity value.** Every fish species has exactly one numerical species catch-odds value, such as `1/2`, `1/200`, or `1/8,500`. Do not use named rarity tiers. A mutation never changes, replaces, or adds another rarity value to the species.

A mutation changes an individual fish while preserving its species identity. For example, a Golden Crystalfin is still a Crystalfin, has the same species odds as a normal Crystalfin, and carries the Golden mutation as an additional individual attribute. Golden may change the appearance and server-calculated sale value through a configured multiplier, but it does not create a new species or rarity.

Keep these concepts separate:
- **Species and its one odds value:** what fish it is and its defining rarity.
- **Mutation:** an optional individual trait, such as Golden, with its own mutation roll configuration and compatible species.
- **Size and weight:** individual random attributes and records.
- **Conditions:** determine eligible fish and any explicitly approved contextual modifiers without rewriting the species' canonical rarity.

Mutation chance is not a second fish rarity. Mutation compatibility, value effects, and presentation are configured separately. The initial implementation should support zero or one mutation per fish instance; stacking is a future decision, not an assumption.

The server owns species selection, mutation rolls, size/weight generation, value calculation, and fish-instance creation. Exact odds semantics, mutation rates, multipliers, and balance values remain open until explicitly configured and tested. Example numbers are not approved balance values.

## Fish use and collection

**Confirmed direction:** fish can be sold, collected, displayed, and used for special purposes.

These roles should complement one another:
- **Sell:** turn catches into currency for progression.
- **Collect:** register discovered species, mutations, and records.
- **Display:** show off memorable catches in personal or shared spaces.
- **Special uses:** selected fish can contribute to unlocks, activities, discoveries, or other systems.

The detailed economy, display spaces, collection UI, and special-use systems remain open design work. Avoid making every fish valuable only as a coin amount.

## Rods, bait, and fishing equipment

**Confirmed direction:** a combination of multiple rods, upgrades, specializations, and unique abilities/effects. Fishing equipment should support fishing itself and boat customization. Do not add sonar, tracking devices, scanning gadgets, or research equipment as a required or defining part of ocean discovery.

Possible dimensions:
- Different rods with distinct identities and designs.
- Rods specialized for particular species, environments, or fishing styles.
- Upgrade paths that improve or modify a rod.
- Distinctive abilities, effects, animations, and handling.
- Bait that interacts with fishing locations or fish pools.

Balance principle: equipment should create meaningful choices rather than making every older rod obsolete. Luck is only one possible stat and should not be the entire progression system.

## Open world and the Living Ocean

The world should be large, connected, and ocean-centric, with both the surface and underwater spaces forming part of its long-term identity. Surface travel and fishing are the first development priority. Underwater exploration is a planned second layer of the same world, introduced after the surface fishing and boat foundations are enjoyable and reliable. Land exists as supporting geography (islands, ports, beaches, docks, landmarks, and occasional points of interest), but should not become the main gameplay focus.

### Two equally supported playstyles

**Relaxed stationary fishing**
- Players can choose a favourite spot, stay there, and fish for as long as they like.
- Stationary fishing has a complete loop: ordinary catches, rare RNG opportunities, mutations, records, collection progress, and useful progression rewards.
- Fishing-area conditions, weather, time, depth, and bait can influence catches without requiring players to move.
- No essential fish, progression gate, or core reward should require constant travel or participation in a temporary event.

**Exploration and expeditions**
- Players can travel between fishing areas, discover landmarks, notice unusual natural activity, follow moving schools, and encounter temporary opportunities.
- Exploration can reveal additional fish pools, clues, secret locations, unusual encounters, and optional rewards.
- These opportunities add variety and excitement without making stationary fishing inferior or incomplete.

### The Living Ocean

The ocean should feel alive through its environment and creature behaviour, not through a layer of scanning gadgets. Players discover things by looking, listening, fishing, experimenting, remembering, and exploring.

Natural signals can include:
- Birds gathering or circling above a patch of water.
- Distant splashes, jumping fish, unusual wave patterns, bubbles, or ripples.
- Large shadows or brief silhouettes beneath the surface.
- Schools moving through an area, scattering, gathering, or changing direction.
- Changes in weather, currents, visibility, and the general behaviour of the water.
- Rare creatures appearing briefly or leaving visible signs of their presence.

These clues should be readable and interesting, but not always give away an exact answer. Some can be noticed by a player who is already fishing nearby; others may reward travelling to investigate. Do not require a gadget to see, interpret, or follow a clue.

**Local activity matters:** the ocean can create small moments around a stationary player, too. A school may pass the spot, birds may gather nearby, baitfish may scatter, a predator may breach in the distance, or a floating find may drift within view. These moments can change the feel or opportunity of a session without forcing the player to chase them.

### Open-world activities

Candidate activities to explore and prototype (not all are locked launch requirements):
- Sailing between distant fishing areas and discovering new routes.
- Visiting islands, ports, beaches, lighthouses, ruins, and unusual landmarks.
- Finding wrecks, drifting cargo, hidden coves, secret fishing spots, and environmental clues.
- Responding to fish migrations, unusual schools, rare sightings, changing weather, and ocean phenomena.
- Joining group expeditions and shared boss encounters.
- Meeting travelling characters, merchants, and other players at world locations.

Avoid turning the ocean into a checklist of repetitive icons or a sequence of mandatory errands. Activities should emerge naturally from the world and remain optional alongside ordinary fishing.

### Underwater exploration

Underwater exploration is a planned part of the full game, not a discarded side idea. It is the second connected layer of the ocean, introduced after the surface fishing and boat foundations are stable. Diving remains optional for each player, while the feature itself belongs in the full game roadmap.

Players can explore reef gardens, rocky shelves, ravines, caves, and sunken wrecks. Possible discoveries include natural crystals and minerals, shells, pearls, unusual coral, fossils, lost cargo, hidden chambers, and underwater creatures. The underwater world should have its own memorable locations and atmosphere, while remaining connected to surface landmarks and ocean routes.

Discovery should come from direct observation and exploration, not sonar, scanners, tracking devices, or research gadgets. Do not assume a strict oxygen timer, pressure simulation, complex dive equipment, or mandatory crafting economy. Prototype comfortable movement and a small number of rewarding places first.

Underwater exploration must not invalidate stationary fishing or make surface-only play incomplete. No essential fish, ordinary progression, or core surface reward should require diving. The detailed feature plan, discovery catalogue, progression options, technical requirements, and open decisions live in [Underwater Exploration](docs/UNDERWATER_EXPLORATION.md).

### Moving creatures and discoveries

Some fish schools and rare creatures can move through the world rather than remain at one fixed point. Their movement and behaviour can create memorable sightings and optional pursuits. A player may notice them from a nearby fishing spot, choose to follow them, or simply continue fishing.

A discovery can lead to another discovery: an unusual sighting may reveal a location, a location may reveal a special fishing opportunity, and that opportunity may lead to a rare creature or boss encounter. These chains should be exciting bonuses, not mandatory progression funnels.

A possible signature encounter discussed: a boss fish could pull the player into a hidden cave area during the fight. Treat this as a concept to prototype, not a locked implementation requirement.

World generation should be reproducible through an idempotent `WorldBuilder` or an equivalent source-controlled workflow. The final implementation approach is still open.

## Boats, customization, and onboard storage

**Confirmed direction:** boats are a major progression and identity system, not disposable transport. Players can buy new boats, upgrade owned boats, and customize their vessel. Boat progression should unlock meaningful travel and group-play options without making early boats feel useless.

### Boat progression
- Purchase additional boat models and unlock them through sensible progression.
- Upgrade dimensions such as speed, handling, durability/stability, storage capacity, and specialized functions.
- Different hulls can have different strengths; avoid a single best boat for every activity.
- Cosmetic customization should remain distinct from gameplay power where possible.
- Boats must support shared trips and safe passenger boarding/leaving.

### Free placement and onboard building
Players should be able to place suitable objects on their boat with very little UI and substantial freedom over where and how objects are positioned. This includes functional equipment and decorative pieces.

Design requirements:
- Placement should feel direct and intuitive: preview, move, rotate, confirm, cancel.
- Support snapping as an optional helper, not a restriction that removes free placement.
- Keep objects inside the boat's allowed build area and prevent blocking helm access, seats, fishing positions, doors, and safety-critical interaction points.
- Define per-object footprint, weight/size class, placement rules, and whether it is functional or decorative.
- Persist placements per boat, with stable item IDs and transforms. Validate all placement and ownership on the server.
- Provide a simple edit mode and a quick way to pick up, move, rotate, or remove owned objects.
- Keep the interface minimal and contextual; the boat itself should remain the focus.

### Coolers and fish storage
The boat's storage identity is primarily **coolers**, rather than a generic cargo-room inventory.
- Players can buy multiple cooler types, place them on the boat, and upgrade them.
- Cooler tiers can improve capacity and may offer clearly defined utility differences later.
- The game must communicate capacity and contents clearly without requiring a large permanent UI.
- A fish should not silently disappear when storage is full. Define an explicit choice: keep in personal inventory, replace/transfer, or decline the catch where appropriate.
- Server-authoritative inventory transfers must prevent duplication, loss, and double-selling.
- Storage capacity is a meaningful boat-build choice, but should not become a mandatory chore.

### Multiplayer ownership
The boat owner controls the vessel and its layout. Guests can interact with permitted equipment and use designated storage according to explicit permissions. The owner should be able to grant limited placement/edit permissions without handing over ownership. A guest must never be able to take, sell, or move another player's stored fish without permission.

## Multiplayer

Playing with friends is a core pillar, not an afterthought.

The intended experience includes:
- Fishing together in the same world.
- Shared boat trips and expeditions.
- Discovering locations and fish together.
- Team-based special encounters or boss fights.
- Server-wide moments for exceptionally rare catches or world events, if they fit the final design.

**Confirmed boss reward direction:** a boss encounter is shared, cooperative content, and every eligible participant receives their own boss catch/reward. The reward is not split between players and one person must not be able to take the only copy. The server determines eligibility and grants each participant exactly once. Contribution can affect presentation or bonus details only if it remains fair and clearly communicated.

Rules for ordinary shared catches, boat ownership, storage permissions, late joining, and party scaling still need detailed contracts. Multiplayer systems must be fair to players with different equipment.

## Fishbook and collection

**Confirmed direction:** the collection system should combine a species encyclopedia with deeper records and discovery tracking.

The fishbook should be able to track:
- Species discovered and caught, with clear undiscovered entries where appropriate.
- mutations found for each species.
- Weight and size records, including personal bests and relevant world/server records if useful.
- First discoveries, notable catches, and boss encounters.
- Helpful clues about habitat, conditions, behaviour, and possible discovery routes, revealed progressively.
- Completion milestones and rewards that encourage exploration without requiring every player to complete everything.

The fishbook should not expose every secret condition immediately. It can begin with partial hints and gradually record discoveries as the player learns more. The collection UI should be readable on mobile and should distinguish a species entry from an individual fish instance stored in inventory.

## World events, live operations, and admin events

**Confirmed direction:** the world should have a mixture of dynamic and scheduled activity:
- Natural world events such as fish migrations, storms, unusual weather, rare schools, and temporary fishing conditions.
- Exploration discoveries such as wrecks, hidden locations, unusual signals, and temporary points of interest.
- Boss appearances that may be random, condition-based, part of a world event, or triggered by a secret discovery.
- Announced and unannounced events, with enough information for players to understand what is happening without turning the game into a constant notification feed.

Admin-run events are a **later live-operations feature**, not a requirement for the first playable release. They should be clearly separate from normal world simulation and use secure server-side permissions, auditable event actions, rate limits, and safe event templates. Admin events should create memorable community moments, never grant hidden unfair advantages or become required for ordinary progression.

## Progression and return motivation

Long-term progression should combine new areas, better or more specialized equipment, collection goals, secrets, rare rewards, and social experiences.

Players should feel curious about what they might discover when they return. Avoid relying on punishing streaks, excessive daily chores, or limited-time pressure as the primary retention mechanic.

## Architecture

**Server-authoritative.** The server owns bite timing, encounter state, reeling validation, rarity and weight rolls, inventory changes, and rewards. The client sends validated requests and input state only. Rate-limit remotes and validate distance, state, equipment, and timing.

**Data.** A player-data layer should persist currency, inventory, discovered species, best weights, equipment, collection progress, and relevant unlocks. Use periodic autosave, save on leave, and `BindToClose`. Provide a safe in-memory fallback for Studio tests when DataStore access is unavailable. Data schema changes need versioning and migration tests.

**Remotes.** Keep remote contracts explicit and documented. Shared types/configuration should define the contract between client and server systems.

## Initial technical file layout

```
src/shared/   CatchOddsConfig, FishConfig, RodConfig, ZoneConfig, shared types
src/server/   Main, PlayerData, FishingService, encounter/reeling services,
              EconomyService, WorldBuilder
src/client/   FishingController, minigame UI, CatchPresentation,
              InventoryUI, CollectionUI, ShopUI
docs/         design decisions, milestones, agent workflow, test plans
```

This is a proposed organization. Adapt it to the actual Studio/repository integration before implementation begins.

## Two-agent development

See:
- [Boat system](docs/BOAT_SYSTEM.md)
- [World events and discovery](docs/WORLD_EVENTS_AND_DISCOVERY.md)
- [Underwater exploration](docs/UNDERWATER_EXPLORATION.md)
- [Fishbook and collection](docs/FISHBOOK_AND_COLLECTION.md)
- [Milestones](docs/MILESTONES.md)
- [Two-agent workflow](docs/TWO_AGENT_WORKFLOW.md)

Each milestone has exactly two independent work packages, one per agent. The two Freebuff agents can swap package ownership at the start of every milestone. Work packages must have explicit file ownership and interface contracts to avoid concurrent edits to the same files.

## Verification

Every implementation milestone should include relevant checks:
- Syntax/require checks for changed scripts.
- Contract checks for shared modules and remotes.
- Server/client validation for gameplay-critical actions.
- Data persistence and migration checks when data changes.
- Playtests covering the complete affected player flow.
- Regression checks for systems touched by both work packages.

For fishing balance, simulate rarity rolls at a scale appropriate to the odds and verify the probability implementation mathematically. A small test cannot meaningfully validate an extremely low-probability event; use deterministic tests and appropriately large offline simulations where appropriate.

## Current open decisions

- Final map layout and fishing-area layout, boat handling, boat progression, and placement rules.
- Cooler tiers, storage limits, guest permissions, and fish overflow behaviour.
- Open-world activity catalogue and the balance between surface exploration and land points of interest; preserve the equal viability of stationary fishing and optional exploration.
- Underwater exploration implementation scope, dive controls, locations, discovery records, and any uses for crystals or other finds. The feature is part of the full game but is staged after the surface foundations.
- Fishbook page structure, record scopes, and collection milestone rewards.
- World-event cadence, boss eligibility/reward rules, and later admin-event permission model.
- Zone access and progression gates.
- Exact fish roster, rarity odds, luck formula, mutations, and value balance.
- Reeling minigame catalogue and per-species assignment.
- Boss encounter structure and multiplayer contribution/reward rules.
- Fish display spaces and special-use systems.
- Rod upgrade and specialization rules.
- Final code synchronization workflow between GitHub and Roblox Studio.

## Publishing

The place is not published automatically. Saving or publishing a place is a deliberate developer decision, not a side effect of building.
