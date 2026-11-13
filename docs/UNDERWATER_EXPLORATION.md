# Underwater Exploration — Hooked-n-Reeled

Status: confirmed as a planned part of the full game; implementation is intentionally staged after the surface fishing and boat foundations.

## Role in the game

Underwater exploration is not a separate game mode or a throwaway side activity. It is the second connected layer of the ocean: the surface is where players fish, sail, spot activity, and travel; below the surface is where they can explore reefs, caves, shelves, ravines, and wrecks.

Diving is optional for an individual player and is not a gate for ordinary fishing progression. It is nevertheless a planned feature of the full Hooked-n-Reeled experience, not an idea to discard or an unspecified post-launch extra.

The underwater world should feel worth entering because it contains memorable places, visual discoveries, collectables, secrets, and encounters that cannot be experienced from the boat.

## Design pillars

1. **Connected to the same ocean.** Dive sites sit beneath or beside recognisable surface landmarks, islands, fishing areas, and wrecks. Players should understand where they are in relation to the world above.
2. **Explore, don't operate gadgets.** Discoveries come from seeing shapes, light, movement, trails, openings, and objects in the environment. Do not add sonar, scanners, tracking devices, or research gadgets.
3. **A place, not a resource field.** Every underwater site should have a recognisable layout, atmosphere, and one or more memorable discoveries. Avoid making diving a repetitive circuit of identical nodes.
4. **Optional, not compulsory.** Surface fishing, stationary fishing, and surface expeditions remain complete and rewarding without diving.
5. **Small and polished first.** Build a few distinctive underwater spaces before expanding into a huge ocean floor.

## Example underwater locations

These are candidate location concepts, not a fixed biome list or final map:
- **Reef gardens:** colourful coral towers, arches, sheltered pockets, small caves, and schools of fish.
- **Rock shelves:** ledges, overhangs, crevices, and crystal seams visible from a distance.
- **Underwater ravines:** dramatic depth changes, narrow passages, unusual rock silhouettes, and pockets of light.
- **Cave systems:** branching but readable spaces, hidden chambers, air pockets if needed, and secret exits.
- **Sunken wrecks:** broken hulls, cargo holds, trapped objects, and environmental stories told through the wreck itself.
- **Quiet seabed clearings:** shells, pearls, unusual plants, fossils, and rare natural formations.

Use evocative place names for actual locations rather than a formal biome taxonomy.

## Discovery ideas

Possible discoveries include:
- Natural crystals and mineral formations, including different shapes, colours, sizes, and unusual clusters.
- Shells, pearls, rare clams, and other ocean finds.
- Distinctive coral, sea plants, and unusual underwater growth.
- Fossils, old artefacts, lost cargo, and objects caught in wreckage.
- Hidden crevices, secret chambers, cave passages, and unusual rock formations.
- Underwater creatures and fish species that players can observe and record.
- Rare visual phenomena such as shafts of light, glowing organisms, drifting particles, or temporary schools.

Not every find needs to be a currency item. Some should exist for collection, discovery records, display, secrets, or simply the satisfaction of finding something unusual.

## Signature moments to prototype

The first underwater slice should contain a few memorable moments rather than a huge number of collectable nodes:

- **A crystal seam in a sunbeam:** a natural crystal formation catches the light from above and becomes visible as the player changes position. No scanner or interaction gadget is needed to reveal it.
- **A living reef passage:** a school of fish moves through a coral arch, briefly revealing a tucked-away opening or small discovery pocket.
- **A wreck with a story:** broken hull sections, tangled nets, scattered cargo, and a readable route into one interior space make the wreck feel like a place rather than a loot pile.
- **A current through a ravine:** water movement gently guides or pushes swimmers through a dramatic passage and hints at a hidden chamber. It should remain controllable, not become an unavoidable hazard.
- **A hidden pearl pocket:** an unusual clam or shell formation gives players a small, satisfying discovery moment without requiring repetitive mining.
- **A deep-water sighting:** a large creature silhouette or unusual school passes through the distant blue. Players can observe it, follow if they want, or simply continue exploring.

These are prototype candidates, not a required launch checklist. Choose a small number that can be made beautiful, readable, and fun.

## A simple diving session

A possible loop to prototype:

1. Notice an interesting underwater feature while sailing, fishing, or exploring a nearby island.
2. Enter the water from a suitable surface location or boat.
3. Swim down and explore the location, choosing routes and looking for visible discoveries.
4. Interact with selected finds or record an observation.
5. Return to the surface and keep, register, display, or otherwise use the discovery according to its type.

The loop should feel smooth and curious rather than like a stressful survival challenge. Do not assume a strict oxygen countdown, pressure simulation, complex diving equipment, or mandatory crafting system. Prototype the simplest comfortable movement and return rules first; only add constraints if they improve the experience.

## How underwater exploration connects to fishing

- Surface fish pools remain fully functional without diving.
- Some surface clues may point toward something interesting below a nearby landmark, but they should not reveal every secret.
- Underwater observation can add Fishbook knowledge about species, locations, behaviour, or discoveries.
- Some creatures may be visible underwater without being catchable there; the exact relationship between diving and fishing remains a separate design decision.
- Underwater events can create temporary activity such as a migrating school, unusual crystal glow, a newly exposed wreck section, or a current that reveals a passage.
- A player who prefers to fish from one spot should never feel forced to dive to keep up.

## Multiplayer

Underwater exploration should support friends diving together:
- Players can see one another clearly and regroup without confusing navigation.
- Discoveries should have fair ownership rules. A shared group discovery may give each eligible participant an individual record or reward rather than making everyone compete for one pickup.
- Group activities can include exploring a wreck, finding a hidden chamber, observing a rare creature, or reaching a difficult-to-find location.
- Solo diving must remain viable; no discovery should require a full group unless it is explicitly designed as a cooperative event.

## Progression and rewards

Possible reward paths:
- Fishbook entries, discovery records, and location completion.
- Display pieces and aquarium/exhibit additions.
- Boat decorations and cosmetic rewards.
- Crystals or other finds used in selected upgrades or crafting, if a later economy design proves this useful.
- Clues to other locations or unusual creatures.
- Titles or collection milestones.

Do not decide crystal prices, crafting recipes, equipment stats, or a large resource economy in this document. First prove that exploring underwater is fun without rewards; then add rewards that reinforce the experience rather than turning it into mining.

## Technical and production requirements

- Use a small number of deliberately designed dive sites for the first prototype.
- Keep underwater geometry connected to the existing world and streamable in manageable sections.
- Plan visibility and lighting for both clear shallow water and darker deep spaces; preserve navigation readability.
- Avoid excessive transparent layers, particles, and overlapping effects.
- Give each site clear entry/exit points and prevent players from getting trapped by geometry or streaming.
- Use server-authoritative interaction and ownership for collectables and discovery rewards.
- Make the interaction readable on PC and mobile, with touch-friendly prompts and controls.
- Profile underwater scenes on mobile; coral, plants, particles, and transparent water effects can become expensive quickly.

## Decisions intentionally left open

- Exact swim controls, speed, buoyancy, and camera behaviour.
- Whether any basic dive equipment is needed, and whether it is cosmetic or functional.
- Whether diving has a gentle time/air limit or no timer at all.
- Whether crystals are primarily collection items, crafting materials, quest items, or a mix.
- Which underwater species can be observed, caught, or only recorded.
- How underwater discoveries respawn, persist, or become unique.
- How boat-based and shore-based dive entry works.
- Exact underwater event types and group reward rules.

These decisions should be made after a small prototype has been playtested. The first implementation should prioritise movement comfort, visual readability, and the joy of discovery.
