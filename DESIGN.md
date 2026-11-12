# Hooked-n-Reeled — Game Design

An open-world Roblox fishing adventure built around exploration, skill-based fishing, collection, progression, rare discoveries, and shared multiplayer expeditions.

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

## Core loop

1. **Explore** — travel through a large, connected world with distinct fishing environments, hidden locations, and changing conditions.
2. **Choose a fishing spot** — biome, water type, depth, weather, time, and location can influence which fish may appear.
3. **Cast and hook** — cast within the equipped rod's range, wait for a bite, then react to hook the fish.
4. **Reel** — play a skill-based minigame. Different fish species can use different minigame mechanics; rare and boss encounters can introduce special phases and mechanics.
5. **Catch presentation** — show the fish, size/weight, rarity, and relevant variants. Presentation can use dynamic camera work, sound, effects, animations, and special cutscenes for meaningful catches.
6. **Use the catch** — sell it, add it to the collection, display it, or use it for special activities, unlocks, and other systems.
7. **Improve and discover** — upgrade or change rods and bait, reach new fishing grounds, uncover secrets, and repeat with new possibilities.

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

Presentation intensity should be tiered:
- Common catches: fast, clean feedback.
- Notable catches: stronger reveal, sound, and visual treatment.
- Extremely rare catches: distinctive reveal or cinematic sequence.
- Boss catches: encounter-specific presentation and a memorable conclusion.

Avoid excessive interruption. The excitement should come from contrast and rarity, not from making every catch slow.

## Fish, rarity, and variants

Fish include ordinary species, rare variants, fantastical creatures, and boss creatures. The world should contain a large and varied species roster.

Fish can have:
- Species identity.
- Rarity tier and actual roll odds.
- Weight and size.
- Variants and mutations.
- Distinctive visual traits or effects, especially for unusual catches.

The existing rarity table is a starting proposal, not a final balance commitment. It currently has sixteen tiers, from Common (1 in 3) to Secret (1 in 1,500,000). Exact odds, luck interaction, tier availability by zone, and value multipliers need a dedicated balance pass.

RNG should remain part of the excitement, but not the only factor. Biome, specific location, water depth, weather, time, and other discoverable conditions can influence eligible fish pools or odds. These conditions should be understandable enough that players can make informed choices without turning fishing into an overcomplicated simulation.

## Fish use and collection

**Confirmed direction:** fish can be sold, collected, displayed, and used for special purposes.

These roles should complement one another:
- **Sell:** turn catches into currency for progression.
- **Collect:** register discovered species, variants, and records.
- **Display:** show off memorable catches in personal or shared spaces.
- **Special uses:** selected fish can contribute to unlocks, activities, discoveries, or other systems.

The detailed economy, display spaces, collection UI, and special-use systems remain open design work. Avoid making every fish valuable only as a coin amount.

## Rods, bait, and equipment

**Confirmed direction:** a combination of multiple rods, upgrades, specializations, and unique abilities/effects.

Possible dimensions:
- Different rods with distinct identities and designs.
- Rods specialized for particular species, environments, or fishing styles.
- Upgrade paths that improve or modify a rod.
- Distinctive abilities, effects, animations, and handling.
- Bait that interacts with fishing locations or fish pools.

Balance principle: equipment should create meaningful choices rather than making every older rod obsolete. Luck is only one possible stat and should not be the entire progression system.

## Open world and exploration

The world should be large, connected, and rewarding to explore. It should contain varied environments such as rainforests with rivers, waterfalls, lakes, caves, coastlines, deep ocean areas, and hidden biomes.

**Confirmed direction:** aim for a seamless world with multiple biomes, secrets, and dynamic conditions. The exact map layout, traversal methods, boat design, and zone-access rules still need decisions.

Exploration can reward players through:
- New fish pools and fishing conditions.
- Hidden fishing spots and secret areas.
- Environmental discoveries and mysteries.
- Special encounters that lead to unexpected places.
- Rare resources, records, or unlock opportunities.

A possible signature encounter discussed: a boss fish could pull the player into a hidden cave biome during the fight. Treat this as a concept to prototype, not a locked implementation requirement.

World generation should be reproducible through an idempotent `WorldBuilder` or an equivalent source-controlled workflow. The final implementation approach is still open.

## Multiplayer

Playing with friends is a core pillar, not an afterthought.

The intended experience includes:
- Fishing together in the same world.
- Shared boat trips and expeditions.
- Discovering locations and fish together.
- Team-based special encounters or boss fights.
- Server-wide moments for exceptionally rare catches or world events, if they fit the final design.

Rules for shared catches, contribution, rewards, boat ownership, and party scaling remain to be designed. Multiplayer systems must be fair to players who join late or participate with different equipment.

## Progression and return motivation

Long-term progression should combine new areas, better or more specialized equipment, collection goals, secrets, rare rewards, and social experiences.

Players should feel curious about what they might discover when they return. Avoid relying on punishing streaks, excessive daily chores, or limited-time pressure as the primary retention mechanic.

## Architecture

**Server-authoritative.** The server owns bite timing, encounter state, reeling validation, rarity and weight rolls, inventory changes, and rewards. The client sends validated requests and input state only. Rate-limit remotes and validate distance, state, equipment, and timing.

**Data.** A player-data layer should persist currency, inventory, discovered species, best weights, equipment, collection progress, and relevant unlocks. Use periodic autosave, save on leave, and `BindToClose`. Provide a safe in-memory fallback for Studio tests when DataStore access is unavailable. Data schema changes need versioning and migration tests.

**Remotes.** Keep remote contracts explicit and documented. Shared types/configuration should define the contract between client and server systems.

## Initial technical file layout

```
src/shared/   RarityConfig, FishConfig, RodConfig, ZoneConfig, shared types
src/server/   Main, PlayerData, FishingService, encounter/reeling services,
              EconomyService, WorldBuilder
src/client/   FishingController, minigame UI, CatchPresentation,
              InventoryUI, CollectionUI, ShopUI
docs/         design decisions, milestones, agent workflow, test plans
```

This is a proposed organization. Adapt it to the actual Studio/repository integration before implementation begins.

## Two-agent development

See:
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

For fishing balance, simulate rarity rolls at a scale appropriate to the odds and verify the probability implementation mathematically. A 100,000-roll test cannot meaningfully validate a 1-in-1,500,000 event; use deterministic tests and much larger offline simulations where appropriate.

## Current open decisions

- Final map layout, biome list, travel and boat mechanics.
- Zone access and progression gates.
- Exact fish roster, rarity odds, luck formula, mutations, and value balance.
- Reeling minigame catalogue and per-species assignment.
- Boss encounter structure and multiplayer contribution/reward rules.
- Fish display spaces and special-use systems.
- Rod upgrade and specialization rules.
- Final code synchronization workflow between GitHub and Roblox Studio.

## Publishing

The place is not published automatically. Saving or publishing a place is a deliberate developer decision, not a side effect of building.
