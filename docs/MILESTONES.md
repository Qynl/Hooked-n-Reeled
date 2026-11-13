# Hooked-n-Reeled — Development Milestones

## Development philosophy

**Build the world first.** Hooked-n-Reeled should make players want to sail out and discover what is beyond the horizon. The first production work is therefore the ocean map and its visual identity, not fishing menus or backend systems.

Work in small, integrated slices. Each milestone has exactly two bounded packages. Package A and Package B are workstreams, **not permanent agent roles**: assign either agent to either package at the start of each milestone and feel free to swap assignments next time.

A milestone should normally produce one visible, testable improvement rather than attempting to finish an entire large system. Do not start the next milestone just because files were written; integrate both packages and verify the result in Roblox Studio first.

## How to run each milestone

1. Read this file, [DESIGN.md](../DESIGN.md), the relevant system docs, and [TWO_AGENT_WORKFLOW.md](TWO_AGENT_WORKFLOW.md).
2. Agree on the exact scope, file ownership, and any shared interfaces before either agent edits files.
3. Assign one writer to each package. Never have both agents edit the same file at the same time.
4. Build in small passes. Keep a working place after each pass.
5. Integrate both packages, open the result in Studio, and test the acceptance checklist.
6. Record what is complete, what is not, screenshots, changed files, and any decisions that need the user's approval.

**Visual references:** Every image in `docs/visual-references/` is concept inspiration only by default. Do not copy images one-to-one or treat them as final designs, asset lists, fish rosters, boat specifications, prices, or map decisions. Follow [the visual-reference rules](visual-references/README.md). Written confirmed decisions take priority.

---

# Phase 1 — Build an amazing world

## M0 — The master ocean map

**Goal:** Establish the exciting, recognisable world of Hooked-n-Reeled. This is the first production milestone. Prioritise a beautiful, memorable map composition with a strong sense of scale and discovery.

### Package A — World geography and large forms
- Translate the world concept into a readable top-down layout.
- Establish the central starting region, main harbour location, island groups, broad ocean channels, remote outer areas, and distant landmarks.
- Create the first in-Studio world layout: ocean surface, island silhouettes, coastlines, major cliffs, beaches, reefs, and large rock formations.
- Make navigation routes between important areas clear and leave room for future expansions.
- Keep the world ocean-first: islands are destinations and landmarks, not disconnected level islands.

**Deliverables:** approved world layout document/image placement, first navigable map layout in Studio, named region/landmark list.

### Package B — Environment asset foundation
- Create a small, cohesive first asset kit for the map: palm variations, tropical trees, bushes, grass, beach plants, rocks, boulders, cliff pieces, and a few signature formations.
- Build reusable modular pieces rather than one-off models wherever practical.
- Establish consistent scale, pivot/origin conventions, naming, collision approach, material palette, and asset organisation.
- Use the visual references for style inspiration only; make original assets that suit the actual map.
- Provide simple placeholder variants when a final asset would block Package A.

**Deliverables:** reusable first environment kit in Studio/repository, asset naming and scale conventions, short usage notes.

**Shared agreement before work:** map scale and coordinate convention, region names/IDs, asset dimensions/pivots, terrain material palette, and which landmarks are required in the first map pass.

**Acceptance:**
- The world can be explored by moving through connected ocean routes.
- The map has a clear visual identity and memorable large-scale silhouettes, not a flat greybox.
- Island groups and major landmarks are recognisable from a distance.
- The first environment assets fit together visually and can be reused.
- No major route is accidentally blocked; performance is checked with a representative view.
- A Studio screenshot/video of the integrated map is captured and reviewed.

## M1 — Make the first region beautiful and playable

**Goal:** Turn the starting area into a polished first impression without trying to finish every island.

### Package A — Starter region environment
- Build the starter island and its immediate coastline using the M0 asset kit.
- Add a small arrival dock, welcoming beach, first fishing location, clear paths, and a few memorable details.
- Create the first visual pass of the main harbour area or a compact harbour slice.
- Make the environment readable at player height as well as from an elevated overview.

**Deliverables:** one finished starter-area slice and one harbour slice, with screenshots from player and overview cameras.

### Package B — World navigation and region structure
- Implement stable region/area identifiers and world bounds.
- Set up player spawn and safe respawn locations.
- Add basic navigation guidance through landmarks, coastline shapes, and routes; avoid cluttering the screen with permanent waypoint UI.
- Establish a practical streaming/performance approach for the world size.
- Add simple region entry/exit detection if needed, without implementing fishing rewards yet.

**Deliverables:** region metadata, spawn setup, basic navigation/streaming configuration, test notes.

**Shared agreement:** region ID format, spawn ownership, map coordinate system, streaming boundaries, and how environment objects identify their region.

**Acceptance:**
- A new player spawns in the intended starting location.
- The starter area is visually coherent and easy to understand.
- Players can travel from the starter area to the first nearby fishing area.
- Region detection and streaming do not break travel or hide nearby important geometry.
- PC and mobile performance receive an initial check.

## M2 — Make the ocean feel alive

**Goal:** Give the map its colour, atmosphere, water identity, and environmental detail.

### Package A — Water, lighting, and atmosphere
- Establish the core lighting setup and colour palette.
- Create readable shallow-to-deep water transitions and coastline foam/wave treatment.
- Add a restrained sunny-day atmosphere and one contrasting weather/time-of-day test.
- Keep reflections, transparency, particles, and post effects performant.

**Deliverables:** approved base lighting/water setup and one alternate atmosphere preset.

### Package B — Environmental dressing and landmarks
- Dress the first region with vegetation, rocks, beach details, dock props, and a few visual discoveries.
- Add a small number of signature landmarks that help players orient themselves.
- Establish density rules so important gameplay areas remain readable.
- Check object collisions and avoid decorative clutter around paths, docks, and fishing locations.

**Deliverables:** dressed starter region, landmark pass, simple set-dressing rules.

**Shared agreement:** material palette, lighting ownership, water colour/depth language, environment density, and performance budget.

**Acceptance:**
- The starter region looks like a deliberate, polished game environment.
- Shallow and deep water are visually distinguishable.
- Landmarks are readable at useful distances.
- Decoration does not obstruct player movement or interactions.
- The scene is checked in Studio under the agreed performance budget.

## M3 — First fishing locations

**Goal:** Create a small set of genuinely different fishing places before implementing the full fishing system.

### Package A — Fishing spot environments
- Build and dress three initial fishing spots, for example a calm lagoon, rocky coast, and reef edge.
- Give each spot a distinct silhouette, water appearance, and environmental identity.
- Include at least one satisfying stationary fishing location.
- Keep the spots accessible from the ocean routes.

**Deliverables:** three in-world fishing spot environments.

### Package B — Fishing area data and validation foundation
- Define stable fishing spot IDs and metadata such as region, water type, depth band, and relevant condition tags.
- Add server-side validation helpers for checking whether a player is in a valid fishing area.
- Establish a small shared configuration contract for fishing areas.
- Do not implement fish selection, rarity rolls, or rewards yet.

**Deliverables:** fishing spot data definitions and server validation contract.

**Shared agreement:** spot IDs, water/depth vocabulary, player-to-spot detection, and region metadata.

**Acceptance:**
- The three spots are visually distinct and reachable.
- The server can identify a valid spot for a player without trusting client claims.
- A player can remain at a valid stationary spot without being forced to explore.
- Spot metadata can be extended without rewriting the world layout.

---

# Phase 2 — Make fishing fun

## M4 — Project and gameplay foundation

**Goal:** Add only the technical foundation needed for the first fishing slice.

### Package A — Server foundation
- Establish the server service/bootstrap structure.
- Add shared types/configuration and a clean service lifecycle.
- Create safe player join/leave handling and a minimal player data wrapper.
- Keep persistence minimal until the data model is known.

### Package B — Client and communication foundation
- Establish client bootstrap and UI mounting structure.
- Define remote-event/function conventions and typed payloads.
- Add server validation, rate limiting, and clear error handling for the first fishing interactions.
- Add a small debug/test interface for development, not a player-facing feature.

**Shared agreement:** module ownership, service names, remote names/payloads, data ownership, and error conventions.

**Acceptance:**
- Client and server start without errors.
- A test interaction can travel client → server → client.
- Invalid payloads are rejected and rate-limited.
- No client can authoritatively set currency, inventory, fish, or rewards.

## M5 — First complete fishing cycle

**Goal:** One rod, one spot, a small starter fish pool, and a complete cast-to-catch experience.

### Package A — Server fishing encounter
- Implement cast validation, bite timing, hook window, encounter state, and server-side catch resolution.
- Validate player state, position, valid fishing spot, equipped rod, and request timing.
- Use a tiny temporary fish pool for this first playable test.
- Ensure cancellation, timeout, disconnect, and duplicate-request handling are safe.

### Package B — Fishing controls and first minigame
- Implement cast input and clear bobber/bite feedback.
- Build one simple but satisfying reeling minigame.
- Support keyboard/mouse and touch controls.
- Show a compact catch result panel.

**Shared agreement:** encounter state machine, remote payloads, minigame input contract, cancellation rules, and catch-result shape.

**Acceptance:**
- A player can cast, receive a bite, hook, reel, and receive a catch.
- The server decides the catch and reward; the client only sends input.
- Invalid or repeated requests cannot create extra catches.
- The interaction works on PC and mobile.
- The first fishing spot remains enjoyable for repeated stationary fishing.

## M6 — Real fish identities and fishbook

**Goal:** Replace temporary fish with a small set of distinct species and make discoveries meaningful.

### Package A — Starter fish catalogue
- Define a deliberately small first roster of original fish species.
- Give each species a stable ID, habitat eligibility, size/weight range, visual description, and initial rarity configuration.
- Ensure fish have distinct silhouettes and identities; do not derive the roster by copying `Fish_IDeas.png`.
- Add data validation for missing or duplicate species IDs.

### Package B — Fishbook discovery
- Implement species discovery tracking and basic fishbook pages.
- Record first catch and personal size/weight records.
- Show unknown/known information clearly.
- Keep species discovery separate from ownership of an individual fish.

**Shared agreement:** species schema, fish IDs, rarity representation, weight units, discovery record format.

**Acceptance:**
- The starter fish pool contains a small, reviewed set of distinct species.
- Catching a species registers it once in the fishbook.
- Selling or losing an individual fish does not erase species discovery.
- Fishbook records cannot be duplicated by repeated client requests.

## M7 — Fish inventory and selling

**Goal:** Give each catch a reliable identity and a meaningful destination.

### Package A — Fish instance inventory
- Create unique server-generated IDs for individual caught fish.
- Store catches in player inventory with clear capacity/overflow behaviour.
- Implement safe transfers between inventory and a designated storage location.
- Prevent duplicate instances and invalid ownership transfers.

### Package B — Selling and first economy UI
- Implement a simple sell interaction and readable fish value display.
- Calculate sale value on the server from approved species/size/rarity data.
- Add a basic currency display and sale confirmation.
- Protect notable catches from accidental irreversible sale with clear feedback.

**Shared agreement:** fish instance schema, ownership/transfer states, sale valuation, currency update contract.

**Acceptance:**
- Each catch exists in exactly one location/state.
- Selling grants currency exactly once.
- Selling an individual fish does not erase fishbook discovery.
- Client payloads cannot choose sale prices or grant currency.

## M8 — Rods, bait, and first progression

**Goal:** Give players a few meaningful fishing choices, not a huge equipment catalogue.

### Package A — Rod definitions and equipment
- Define a small starter set of rods with distinct intended roles.
- Implement rod ownership, equipping, and server-side effect validation.
- Keep stat differences understandable and avoid one universally dominant rod.

### Package B — Bait, shop, and progression
- Define a small starter set of bait types and their eligible pool/condition effects.
- Implement a simple shop flow with server-owned purchases.
- Add clear UI for owned/equipped rods and bait.
- Use non-stat cosmetics or small unlocks as early rewards where appropriate.

**Shared agreement:** rod/bait data shape, effect vocabulary, purchase request/result, and balance rules.

**Acceptance:**
- Players can buy, equip, and switch the initial rods and bait.
- Server validates ownership, prices, and effects.
- Bait changes eligible fishing opportunities in a readable way.
- No purchase can be duplicated or made with insufficient currency.

## M9 — More reeling variety and special catches

**Goal:** Make different fish feel different to catch and give truly special catches a memorable reveal.

### Package A — Reeling mechanics
- Add a second and third reeling archetype as separate reusable modules.
- Assign mechanics to selected species through configuration.
- Tune difficulty for keyboard/mouse and touch.
- Keep the first mechanic available for suitable species.

### Package B — Catch presentation
- Add rarity-aware sound, animation, camera, and effect hooks.
- Build one notable/rare catch reveal and one boss-style presentation prototype.
- Keep common catches quick and non-disruptive.
- Ensure all effects cancel and clean up safely.

**Shared agreement:** minigame interface, species-to-minigame mapping, presentation event schema, and cancellation/cleanup behaviour.

**Acceptance:**
- At least three reeling mechanics are playable.
- Selected species use the intended mechanics.
- Special reveals trigger from server-confirmed results only.
- Effects do not trap the player or block normal play after cancellation.

---

# Phase 3 — Boats, multiplayer, and world depth

## M10 — First boats and ocean travel

**Goal:** Let players own a boat and travel the connected ocean reliably.

### Package A — Boat models and progression starter set
- Create a small initial family of boat hulls with clearly different silhouettes and scale.
- Make progression visually satisfying: higher-cost boats should generally feel larger, more impressive, and offer more capability, while hull roles can still have trade-offs.
- Add seats, helm, boarding points, and clear interaction locations.
- Treat boat concept sheets as inspiration, not a locked boat list or price table.

### Package B — Boat ownership and travel system
- Implement boat purchase/ownership and spawn/despawn flow.
- Add basic server-validated movement and safe boarding/disembarking.
- Add a simple boat selection/spawn interface.
- Test network ownership and multiplayer movement behaviour.

**Shared agreement:** boat IDs, hull dimensions, ownership state, movement authority, spawn points, and upgrade vocabulary.

**Acceptance:**
- A player can acquire, spawn, board, pilot, and despawn an owned boat.
- Other players can safely board as guests.
- Boat movement does not allow arbitrary client teleporting or invalid ownership.
- Boats fit through the intended ocean routes.

## M11 — Boat upgrades and customization

**Goal:** Make boats personal and create a satisfying upgrade path.

### Package A — Upgrades and visual customization
- Add a small first set of upgrades for speed, handling, stability, and storage support.
- Add paint/colour and a few cosmetic customization options.
- Keep functional stats and cosmetic appearance separate.
- Make boat progression visible and understandable.

### Package B — Onboard placement
- Prototype contextual free placement of a small set of owned objects.
- Support move, rotate, confirm, cancel, and pickup.
- Validate build bounds, collisions, object limits, and access clearance on the server.
- Start with a few decorative and functional objects; do not build a giant furniture catalogue.

**Shared agreement:** boat save identity, upgrade data, placeable item schema, transform limits, and permission rules.

**Acceptance:**
- Upgrades persist and apply on the server.
- Players can place and reposition approved objects within valid boat bounds.
- Required controls and boarding/helm access cannot be blocked.
- Placement works with mouse and touch.

## M12 — Coolers and fish storage on boats

**Goal:** Make the boat useful for longer fishing trips without risking fish loss or duplication.

### Package A — Cooler objects and capacity
- Add a small set of cooler sizes/tiers.
- Allow coolers to be placed on eligible boats.
- Display cooler capacity and contents through a compact contextual UI.
- Define a clear full-capacity response.

### Package B — Safe fish transfers and permissions
- Implement atomic transfers between player inventory and boat coolers.
- Add owner/guest permissions for viewing and depositing fish.
- Prevent guests from taking, selling, or moving another player's fish without explicit permission.
- Handle boat despawn, disconnect, and server transfer safely.

**Shared agreement:** cooler IDs, capacity schema, fish ownership, transfer state, and guest permission levels.

**Acceptance:**
- A fish cannot exist in inventory and a cooler simultaneously.
- Full storage never silently deletes a catch.
- Permissions are checked by the server.
- Stored fish remain safe through normal boat despawn/rejoin flows.

## M13 — Group expeditions and cooperative encounters

**Goal:** Make fishing trips with friends work as a coordinated activity.

### Package A — Group expedition flow
- Add simple party/expedition membership and leave/join handling.
- Show useful shared activity/location context without clutter.
- Support group travel on shared boats.
- Define safe behaviour when the owner leaves or disconnects.

### Package B — Cooperative fishing/boss prototype
- Build one bounded cooperative encounter.
- Define participant eligibility and late-join rules.
- Grant each eligible participant their own reward exactly once.
- Keep reward delivery server-authoritative and idempotent.

**Shared agreement:** party membership, boat guest permissions, encounter participant state, eligibility, and unique reward grant IDs.

**Acceptance:**
- Two or more players can travel and complete the cooperative test.
- Each eligible participant receives their own reward once.
- Disconnects and duplicate completion requests do not duplicate or erase rewards.

## M14 — More world discoveries and fishing conditions

**Goal:** Add optional reasons to explore while keeping stationary fishing rewarding.

### Package A — Fishing conditions and natural clues
- Add a small number of weather/time/water-condition effects on eligible fish pools.
- Add natural clues such as birds, splashes, unusual ripples, jumping fish, and visible schools.
- Show clues that can be noticed from a stationary fishing spot as well as clues that reward travelling.
- Do not introduce sonar, tracking devices, scanning gadgets, or research equipment.

### Package B — Secrets and special locations
- Add one hidden cove or secret fishing location.
- Add one discoverable wreck/drifting find or similar surface discovery.
- Record discoveries in the fishbook or a simple journal.
- Keep all secrets optional and avoid making them mandatory for ordinary progression.

**Shared agreement:** condition tags, clue vocabulary, discovery IDs, reward payloads, and stationary-fishing guarantees.

**Acceptance:**
- Players can understand at least one natural clue and discover its meaning.
- Exploration provides extra opportunities without invalidating ordinary fishing spots.
- A player who stays in a suitable spot still has worthwhile fish pools and rare RNG chances.
- No discovery gadget is required.

## M15 — World events and expanded content slice

**Goal:** Add a small, controlled event system and prepare the world for more content.

### Package A — One or two world event prototypes
- Prototype a fish migration, unusual school, or temporary weather window.
- Make event timing, eligible areas, start/end state, and fish-pool effects data-driven.
- Ensure the event is optional and normal fishing remains active.

### Package B — Content and reliability pass
- Expand the initial fish/spot/boat content only where the existing systems support it.
- Add missing fishbook clues and records for the new content.
- Test event cleanup, player joining/leaving, and reward integrity.
- Document admin-run events as a later live-operations feature, not a launch dependency.

**Shared agreement:** event definition, eligible zones, event lifecycle, fish-pool modifier contract, and cleanup rules.

**Acceptance:**
- At least one event can start, run, and end cleanly.
- Normal fishing continues outside event conditions.
- Event rewards and catches cannot be duplicated.
- Content can be added through data/configuration without rewriting core systems.

---

# Phase 4 — Stabilise and prepare the first release

## M16 — Persistence, performance, and release candidate

**Goal:** Make the first complete slice reliable enough for wider playtesting.

### Package A — Data safety and security
- Add schema versioning and migrations for player data.
- Test save/load failures, retries, session ownership, and rejoin behaviour.
- Audit every reward, purchase, sale, inventory transfer, boat edit, and remote.
- Add logs for important server-side failures without exposing sensitive player data.

### Package B — UX, accessibility, and performance
- Polish onboarding, fishing feedback, fishbook, inventory, shop, and boat interfaces.
- Verify keyboard/mouse and mobile controls.
- Profile representative map areas, boats, effects, and multiplayer encounters.
- Fix the highest-impact visual, usability, and performance issues.

**Shared agreement:** release data schema, performance budgets, supported-device targets, and final test checklist.

**Acceptance:**
- No known data-loss, item-duplication, or reward-duplication issue remains in the tested flows.
- Core play works on supported input devices.
- Rejoin and save/load scenarios pass.
- Performance is measured and documented in representative locations.
- The first release candidate is reviewed in Roblox Studio with screenshots/video and a clear list of remaining issues.

---

## Milestone rules

- Exactly two packages per milestone.
- Package A/B are task labels, not permanent agent specialties.
- Every package has a bounded scope and a clear deliverable.
- One writer per file at a time.
- Agree on shared interfaces before parallel implementation.
- Do not silently expand a package; pause and coordinate if its scope must change.
- Integrate and test both packages before marking a milestone complete.
- A successful commit or static check does not prove the Roblox experience works.
- Capture and review the actual Studio result for visual milestones.
- Never treat concept images as final specifications.
- Do not skip ahead to large systems before their smaller dependencies are proven.

## Milestone handoff checklist

For every milestone, record:

- [ ] Package A owner and exact scope confirmed
- [ ] Package B owner and exact scope confirmed
- [ ] File ownership and shared interfaces agreed
- [ ] Package A deliverable reviewed
- [ ] Package B deliverable reviewed
- [ ] Both packages integrated
- [ ] Roblox Studio test completed
- [ ] Screenshots/video captured for visual work
- [ ] Known issues and next milestone dependencies documented

