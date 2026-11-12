# Hooked-n-Reeled Development Milestones

## How to assign the two agents

Every milestone below contains exactly two packages. At the start of each milestone, freely choose which Freebuff handles Package A and which handles Package B. You can swap roles every milestone.

Do not start both packages until file ownership and shared interfaces are agreed. Follow [TWO_AGENT_WORKFLOW.md](TWO_AGENT_WORKFLOW.md).

## M0 — Design and technical contracts

**Goal:** turn the current concept into implementable, testable contracts.

### Package A — Gameplay design contracts
- Define the first playable fish roster and species data shape.
- Propose the first set of distinct reeling minigame archetypes and map initial species to them.
- Define catch presentation tiers: ordinary, notable, extremely rare, boss.
- Document fish lifecycle: caught, inventory, collection, display, sale, special use.

### Package B — World and progression contracts
- Propose the first connected-world greybox layout and initial biome list.
- Define fishing spot metadata: biome, water type, depth band, weather/time tags.
- Propose rod/bait data shape and progression dimensions.
- Define multiplayer expedition and shared-boat requirements at a design level.
- Agree on boat customization, free-placement constraints, cooler storage, and permissions.
- Define fishbook records, discovery clues, and boss reward eligibility.

**Shared contract before implementation:** fish IDs, rarity representation, fishing-spot identifiers, rod/bait identifiers, and the shape of a fishing encounter.

**Acceptance:** no unresolved naming or data-shape conflict between the two packages; design decisions are documented. Do not build production gameplay systems yet.

## M1 — Project foundation and playable greybox

**Goal:** a player can enter a simple world and move between at least two distinct fishing environments.

### Package A — World foundation
- Implement the initial greybox terrain/landmarks and water regions.
- Create the reproducible world-building workflow.
- Add clear location/zone identifiers and basic spawn placement.

### Package B — Shared gameplay foundation
- Set up shared configuration/types and the server/client service skeleton.
- Establish remote contracts and basic validation/rate limiting.
- Add a minimal player-data wrapper with safe Studio fallback.

**File ownership:** A owns world-generation and world-layout files. B owns shared contracts, service bootstrap, remotes, and player-data foundation. Agree on any shared config file before coding; assign it to exactly one package.

**Acceptance:** a player can spawn, move between two fishing areas, and the server/client foundation starts without errors.

## M2 — First complete fishing loop

**Goal:** complete cast → bite → hook → reel → catch → reward.

### Package A — Fishing encounter service
- Implement server-owned cast validation, bite timing, hook window, encounter state, and catch resolution.
- Validate player state, distance to water, equipped gear, and request timing.
- Return a result from server-owned fish/rarity/weight data.

### Package B — Fishing client and first minigame
- Implement cast input, bobber feedback, bite feedback, and the first reeling minigame UI.
- Implement catch result presentation for ordinary catches.
- Send input state only; never choose the fish or reward on the client.

**Shared contract:** encounter state machine, remote payloads, and result DTO must be agreed before work starts.

**Acceptance:** a full fishing cycle works in a server playtest; invalid client requests cannot award catches; normal catch feedback is clear on PC and mobile.

## M3 — Fish identity, collection, and economy

**Goal:** catches have identity and meaningful destinations.

### Package A — Fish catalogue and collection
- Add initial species definitions, rarity metadata, weights, and discovery tracking.
- Implement collection/encyclopedia progress and best-catch records.
- Add variant/mutation fields in a data-driven way, even if only a small starter set is enabled.

### Package B — Inventory, sale, and display foundation
- Implement fish inventory storage and safe item transfer.
- Implement selling and server-authoritative currency rewards.
- Build a basic display/exhibit interaction or a documented placeholder contract.

**Shared contract:** fish instance schema, species ID rules, inventory persistence, and sale valuation.

**Acceptance:** caught fish persist, appear in the collection, can be sold exactly once, and can be displayed without duplicating or losing data.

## M4 — Rods, bait, and progression

**Goal:** equipment choices change fishing opportunities and feel distinct.

### Package A — Rod system
- Implement rod definitions, equipment slots, upgrade/specialization data, and server validation.
- Add a small starter set of rods with genuinely different identities.
- Add a basic upgrade path.

### Package B — Bait, shop, and progression UI
- Implement bait definitions and their interaction with eligible fish pools or conditions.
- Build the first shop and equipment UI.
- Connect purchases and unlocks to server-owned currency and progression.

**Shared contract:** equipment data schema, stat/effect vocabulary, purchase payloads, and balance rules.

**Acceptance:** players can acquire, equip, and switch rods/bait; server validates purchases and effects; no single stat dominates all choices.

## M5 — Distinct reeling mechanics and special catch presentation

**Goal:** species and important catches feel different moment to moment.

### Package A — Reeling archetypes
- Implement additional minigame mechanics as separate, reusable modules.
- Assign mechanics to selected species through data/configuration.
- Add boss encounter phases as a bounded prototype.

### Package B — Catch presentation
- Add rarity-aware camera, sound, effects, and animation hooks.
- Build notable/rare catch reveals and one boss presentation prototype.
- Keep ordinary catches fast and non-disruptive.

**Shared contract:** minigame interface, encounter event payloads, presentation event schema, and cancellation/cleanup behavior.

**Acceptance:** at least three distinct reeling mechanics work; selected fish use the intended mechanic; special presentation triggers correctly and cleans up safely.

## M6 — Multiplayer expeditions and shared boats

**Goal:** friends can travel and fish together as a coordinated activity.

### Package A — Shared boat and travel
- Prototype boat spawning/ownership and safe shared occupancy.
- Implement basic travel controls and server-side movement validation.
- Define how players join/leave a boat safely.
- Define boat purchase and upgrade data, including speed/handling/storage/specialization.
- Prototype low-friction onboard free placement with server-validated build bounds and obstruction rules.
- Add cooler placement, capacity upgrades, and clear fish-storage overflow behaviour.

### Package B — Group fishing and expedition flow
- Implement party/expedition grouping and shared location markers or activity flow.
- Prototype a cooperative fishing encounter or group objective.
- Define boss eligibility and reward rules: each eligible participant receives an individual copy/reward exactly once.
- Add explicit boat guest permissions for equipment, cooler access, and optional layout editing.

**Shared contract:** boat state, party membership, participant eligibility, encounter ownership, and reward distribution.

**Acceptance:** two or more players can travel together and complete a cooperative test encounter without state desync or duplicated rewards.

## M7 — World depth, secrets, and dynamic conditions

**Goal:** exploration meaningfully changes what players can discover.

### Package A — Biomes and fishing conditions
- Expand the seamless, ocean-first world with additional connected biomes and fishing locations; land remains supporting geography.
- Implement weather/time/water-condition tags and their effect on eligible fish pools.
- Add clear player-facing hints for discoverable conditions, including clue-based odds boosts and selected guaranteed encounters.
- Prototype surface-focused open-world activities such as island visits, wreck discoveries, ports, drifting finds, and special routes.

### Package B — Secrets and special encounters
- Prototype hidden fishing spots and one secret area discovery.
- Prototype a boss encounter that can be random, condition-based, event-based, or secret-discovered.
- Add discovery rewards and fishbook clue/record integration.
- Ensure a shared boss win grants each eligible participant their own reward exactly once.

**Shared contract:** zone/spot metadata, condition evaluation API, transition rules, and discovery reward payload.

**Acceptance:** players can discover at least one meaningful secret and observe understandable differences between fishing conditions.

## M8 — Persistence, polish, and release candidate

**Goal:** stabilize the complete first release slice.

### Package A — Data and reliability pass
- Add schema versioning, migrations, save/load failure handling, and persistence tests.
- Audit remote validation and exploit-sensitive reward paths.
- Profile server and client performance in representative playtests.

### Package B — UX, accessibility, and content polish
- Polish fishing feedback, collection, inventory, shop, and onboarding.
- Verify PC and mobile usability.
- Add initial sound/visual polish and fix high-impact usability issues.
- Add a data-driven world-event framework for migrations, weather windows, rare schools, and boss appearances.
- Document admin-run events as a later feature; if prototyped, use server-side allowlists, permission checks, audit logs, and bounded event templates.

**Shared contract:** release data schema, performance budgets, and final acceptance checklist.

**Acceptance:** no known data-loss or reward-duplication bugs in test scenarios; core flow works on supported input devices; performance and release checks are documented.

## Milestone rules

- Exactly two work packages per milestone.
- Agent ownership is reassigned freely at every milestone.
- One writer per file at a time.
- Shared interfaces are agreed before parallel implementation.
- A milestone is not complete until both packages are integrated and tested.
- Milestones are a roadmap, not permission to skip design decisions or build systems prematurely.


## Cross-system design contracts added in Rounds 5–7

Before implementation crosses the prototype stage, document and agree on:
- **Ocean-first world:** surface exploration is the primary loop; land points of interest support it. Underwater exploration is not a required core feature.
- **Boat build state:** boat owner, unlocked hull, upgrades, placed-object IDs/transforms, build-area bounds, object footprints, and guest permissions.
- **Cooler storage:** cooler identity/tier/capacity, stored fish instance IDs, transfer rules, full-capacity behaviour, and anti-duplication guarantees.
- **Fishbook:** species discovery, individual catch instances, variants/mutations, record scopes, clue progression, and collection rewards.
- **Clue system:** distinguish odds modifiers from guaranteed availability/encounters. A guarantee must state its exact scope and conditions.
- **Boss rewards:** participant eligibility, late-join rules, individual reward grant IDs, and exactly-once server-side delivery.
- **World events:** event definition, start/end state, eligible zones, fish-pool modifiers, boss triggers, UI announcement policy, and cleanup.
- **Admin events (later):** permission model, server-only execution, audit log, cooldowns, safe templates, and explicit separation from normal progression.
