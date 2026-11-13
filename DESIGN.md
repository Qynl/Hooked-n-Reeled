# Hooked-n-Reeled — Game Design

An open-world Roblox fishing adventure built around skill-based fishing, collection, progression, rare discoveries, optional ocean exploration, and shared multiplayer expeditions. Its signature identity is a living ocean that rewards both relaxed stationary fishing and curious exploration.

Status: design phase. No gameplay code has been written yet.

## Core vision

Hooked-n-Reeled should feel relaxing when players simply want to fish, but also offer mysterious places, exciting discoveries, rare catches, and memorable adventures with friends. The world should reward curiosity rather than feeling like a collection of disconnected fishing menus.

The long-term appeal combines:
- Discovering new places and fish species.
- Improving and specializing fishing equipment.
- Chasing rare fish, unusual variants, mutations, and boss encounters.
- Building a personal collection and displaying memorable catches.
- Selling catches and using selected fish for special unlocks or activities.
- Exploring and fishing together with friends.

The game should welcome players back after time away through discoveries and ongoing world activity, not punish them with aggressive daily chores or fear-of-missing-out systems.

**Two equally valid playstyles:** players can settle into a favourite fishing spot and enjoy a complete, rewarding fishing experience without travelling around. Players who prefer movement can explore, notice natural ocean clues, follow moving schools, and join special encounters. Exploration adds opportunities; it must never become a requirement for ordinary progression, rare catches, or a satisfying session.

## Core loop

1. **Choose how to play** — stay at a favourite spot for relaxed fishing, or travel through the connected ocean to explore. Neither choice is mandatory.
2. **Choose a fishing spot** — water type, depth, weather, time, and location can influence which fish may appear. Valid fish pools and natural RNG must make stationary fishing worthwhile.
3. **Cast and hook** — cast within the equipped rod's range, wait for a bite, then react to hook the fish.
4. **Reel** — play a skill-based minigame. Different fish species can use different minigame mechanics; rare and boss encounters can introduce special phases and mechanics.
5. **Catch presentation** — show the fish, size/weight, rarity, and relevant variants. Presentation can use dynamic camera work, sound, effects, animations, and special cutscenes for meaningful catches.
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

## Fish, rarity, and variants

Fish include ordinary species, rare variants, fantastical creatures, and boss creatures. The world should contain a large and varied species roster.

Fish can have:
- Species identity.
- An exact catch probability expressed as odds (for example, 1/2, 1/200, or 1/5,000).
- Weight and size.
- Variants and mutations.
- Distinctive visual traits or effects, especially for unusual catches.

**Rarity is odds-based, not a named tier ladder.** Do not classify fish into labels such as Common, Uncommon, Rare, Epic, Legendary, Mythic, or Secret. The actual probability is the rarity definition: a fish with odds of 1/200 is rarer than one with odds of 1/2, and a fish with odds of 1/5,000 is rarer still. Show and communicate rarity through the probability itself (or a clearly equivalent “1 in X” display), not through conventional tier names.

This establishes the system's format only. It does not decide the number of fish, assign odds to any species, or lock any balance values. Exact probabilities and the way luck or conditions affect them remain open design work.

RNG should remain part of the excitement, but not the only factor. Specific fishing area, water depth, weather, time, and other discoverable conditions can influence eligible fish pools or odds. These conditions should be understandable enough that players can make informed choices without turning fishing into an overcomplicated simulation. Every normal fishing area must retain a worthwhile catch pool and a chance at exciting RNG catches; rare fish must not be locked exclusively behind roaming, clues, or events. Environmental clues can improve a player's choices, but players who prefer to camp at one spot must still have a complete and rewarding loop.

## Fish use and collection

**Confirmed direction:** fish can be sold, collected, displayed, and used for special purposes.

These roles should complement one another:
- **Sell:** turn catches into currency for progression.
- **Collect:** register discovered species, variants, and records.
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

The world should be large, connected, and ocean-centric. Most meaningful travel and exploration happen on the water. Land exists as supporting geography (islands, ports, beaches, docks, landmarks, and occasional points of interest), but should not become the main gameplay focus. Underwater exploration is a secondary, optional activity planned for a later phase; it is not part of the initial core gameplay or first playable release.

### Two equally supported playstyles

**Relaxed stationary fishing**
- Players can choose a favourite spot, stay there, and fish for as long as they like.
- Stationary fishing has a complete loop: ordinary catches, rare RNG opportunities, variants, mutations, records, collection progress, and useful progression rewards.
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

### Open-world activities

Candidate activities to explore and prototype (not all are locked launch requirements):
- Sailing between distant fishing areas and discovering new routes.
- Visiting islands, ports, beaches, lighthouses, ruins, and unusual landmarks.
- Finding wrecks, drifting cargo, hidden coves, secret fishing spots, and environmental clues.
- Responding to fish migrations, unusual schools, rare sightings, changing weather, and ocean phenomena.
- Joining group expeditions and shared boss encounters.
- Meeting travelling characters, merchants, and other players at world locations.

Avoid turning the ocean into a checklist of repetitive icons or a sequence of mandatory errands. Activities should emerge naturally from the world and remain optional alongside ordinary fishing.

### Optional underwater exploration (later phase)

Underwater exploration can expand the ocean adventure after the core surface experience is established. It is a secondary activity, not a replacement for fishing, sailing, or surface exploration.

- Players may choose to dive into selected underwater areas such as reefs, rocky shelves, caves, and wreck sites.
- Discoveries may include natural crystals and mineral formations, unusual coral, shells and pearls, hidden crevices, and objects or cargo around sunken wrecks.
- The underwater world should have its own visual identity and memorable places, while remaining connected to the larger ocean.
- Diving must be optional. No essential fish, ordinary progression, or core reward may require underwater exploration.
- Players who prefer to fish from one spot or explore only the surface must still have a complete and rewarding game.
- Discovery should rely on seeing and exploring the environment. Do not introduce sonar, scanners, tracking devices, or similar detection gadgets.
- Do not assume that every discovery must be crafted, sold, or converted into equipment. The uses, collection rules, diving controls, and any equipment requirements remain open design decisions.

This feature belongs after the fishing and boat experience is established. It is not a blocker for the initial release.

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
- Variants and mutations found for each species.
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
- Later-phase optional diving scope, underwater locations, discovery records, and any uses for crystals or other finds.
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
