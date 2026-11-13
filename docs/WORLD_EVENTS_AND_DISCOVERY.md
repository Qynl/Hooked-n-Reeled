# World Events and Discovery — Hooked-n-Reeled

Status: confirmed design direction; cadence and exact content remain open.

## World identity

The world is seamless and ocean-first, with surface and underwater spaces forming two connected layers. Surface fishing, travel, and discovery are the first implementation priority; underwater exploration is a planned part of the full game that follows once the surface and boat foundations are stable. Islands, ports, beaches, lighthouses, ruins, and other land features add landmarks and destinations, but land is not intended to become a second full-scale adventure game.

The ocean should feel alive through natural environmental signals and creature behaviour. Discovery is based on observation, fishing, experimentation, memory, and exploration. Do not build the discovery identity around sonar, tracking devices, scanning gadgets, research equipment, or similar tools.

## Two equally valid playstyles

### Relaxed stationary fishing

Players must be able to choose a fishing spot and remain there for a long session without feeling that they are missing the real game.

- Stationary fishing has a complete and rewarding loop, including ordinary fish, rare RNG catches, variants, mutations, records, collection progress, and useful progression.
- The local fish pool and conditions can make different spots feel distinct.
- Players can notice environmental activity while staying in one place.
- No essential species, progression gate, or core reward should require constant movement, exploration chains, or temporary events.

### Exploration and expeditions

Players who enjoy travelling can find additional opportunities by exploring the ocean.

- Discover new fishing areas, landmarks, hidden coves, wrecks, drifting cargo, and unusual formations.
- Notice and investigate natural clues or unusual creature behaviour.
- Encounter moving schools, rare sightings, temporary fishing opportunities, and shared boss events.
- Follow optional discovery chains where one clue or location can lead to another.

Exploration adds variety and bonus opportunities. It must not make stationary fishing obsolete or mandatory travel the only effective way to progress.

## Natural ocean signals

Use environmental storytelling rather than dedicated discovery gadgets. Possible signals include:
- Birds gathering or circling above a patch of water.
- Distant splashes, jumping fish, unusual waves, bubbles, and ripples.
- Large shadows or brief silhouettes beneath the surface.
- Fish schools gathering, scattering, or moving through an area.
- Changes in weather, currents, visibility, and the behaviour of the water.
- Rare creatures appearing briefly or leaving visible signs of their presence.

Some clues should be noticeable from a player's current fishing spot. Others can reward travelling to investigate. Clues should invite curiosity rather than provide constant exact waypoint instructions. Players should never need a gadget to see, interpret, or follow them.

## Rare-fish clues and RNG

Use a mix of natural RNG and learnable conditions:
- Ordinary fishing always retains valid fish pools and meaningful RNG opportunities.
- Some clues reveal where or when a species is more likely to appear.
- Some conditions improve odds or expand the eligible fish pool.
- Some exact combinations can make a particular fish or encounter available.
- Some discoveries can be experimental and community-shareable.

A guaranteed encounter means the fish becomes available under the stated conditions, not that every cast automatically catches it. If a truly guaranteed catch is intended, its scope must be explicit. Keep natural random discovery viable so players can still be surprised.

Do not lock all rare fish behind exploration, clues, or events. A player who stays at a suitable spot must still have a chance at exciting rare RNG catches. Conditions and clues should reward knowledge without invalidating relaxed fishing.

The fishbook can record what the player has learned without exposing every secret from the beginning. Clues may come from environmental details, fishbook entries, NPC dialogue, weather patterns, unusual schools, maps, or expedition discoveries.

## Moving schools and creatures

Some schools and rare creatures can move through the world and behave in distinctive ways. Their movement creates optional opportunities:
- Players may notice activity nearby while already fishing.
- Curious players can follow a school or creature to see where it leads.
- A creature may appear briefly, retreat, dive, or change direction.
- Different species can have recognisable behaviour, without requiring a tracking device or scanner.

Moving encounters should coexist with ordinary fish pools. They should not constantly pull players away from a spot or punish players who choose not to follow.

## World events

Candidate event families:
- Fish migrations and unusually dense schools.
- Short weather windows that alter fish availability.
- Storms or ocean conditions that create new routes or risks.
- Rare fish sightings and temporary fishing hotspots.
- Wrecks, drifting objects, and temporary discoveries.
- Underwater phenomena such as unusual currents, glowing reefs, migrating schools, or newly exposed wreck areas.
- Boss appearances and server-wide expeditions.

Events can be random, scheduled, condition-triggered, or discovery-triggered. Use a mix of announced and subtle events. Players should be able to understand the opportunity without needing to watch a constant alert feed. Events are optional additions to the world, not mandatory daily chores or the only source of desirable catches.

## Boss encounters

Bosses can appear:
- Randomly in the world.
- When specific environmental conditions align.
- As part of a world event.
- After a player or group discovers a secret.

Bosses should have a memorable introduction, distinct multi-phase fishing encounter mechanics, and a strong conclusion. Multiplayer boss encounters are shared: every eligible participant receives their own reward/catch, exactly once. The server owns eligibility and reward delivery.

Late-join eligibility, distance rules, disconnect handling, and contribution rules need a clear contract before implementation. Participation should be understandable and not punish players for using a different rod or joining a little later.

## Underwater world activity

Underwater exploration is part of the full game world, not a throwaway post-launch idea. It is intentionally staged after the surface fishing, boats, and core world systems are stable. Diving is optional for each player, and the surface game must remain complete without it.

Candidate underwater activity includes:
- Exploring reef gardens, rocky shelves, ravines, cave systems, and sunken wrecks.
- Finding natural crystals and mineral formations, shells, pearls, unusual coral, fossils, and lost cargo.
- Discovering hidden crevices, secret chambers, and passages that connect to recognisable surface landmarks.
- Observing unusual underwater creatures, fish schools, and environmental behaviour.
- Experiencing temporary underwater phenomena such as unusual currents, glowing organisms, shifting schools, or a newly revealed wreck section.

The underwater world should feel like a set of memorable places, not a repeated resource-node route. Discoveries come from direct observation and exploration, not sonar, scanners, tracking devices, or research gadgets. Avoid assuming a strict oxygen countdown, pressure simulation, or complex dive equipment before a prototype proves it improves play.

Surface and underwater discoveries can connect: a strange surface sighting may hint at a reef or wreck below; an underwater discovery may reveal a hidden cove or new fishbook clue. These chains are optional and must not gate ordinary fishing progression.

See [Underwater Exploration](UNDERWATER_EXPLORATION.md) for the feature design, possible rewards, multiplayer rules, technical constraints, and open decisions.

## Admin-run events: later phase

Admin events are a future live-operations feature, not a core progression requirement and not needed for the first vertical slice.

Potential uses:
- Community-wide rare fish migrations.
- Special boss appearances.
- Themed ocean conditions or temporary visual transformations.
- Celebration events and controlled content previews.

Safety and integrity requirements:
- Admin authorization must be checked on the server using a restricted allowlist or a robust role system.
- Never trust a client-provided username, rank, or permission flag.
- Use bounded event templates rather than arbitrary client-supplied code or unvalidated parameters.
- Log who started, changed, and ended each event.
- Add cooldowns, duration limits, and emergency stop controls.
- Keep admin event rewards fair, transparent, and separate from hidden progression shortcuts.
- Never require an admin event to complete ordinary collections or progression.

## Open decisions

- Event frequency, duration, and whether events are server-local or cross-server.
- Which events are announced, hinted, or completely discoverable.
- Whether players can start some discovery events themselves.
- Boss scaling for solo and group play.
- Exact admin roles and audit-log retention.
- How to balance rare RNG opportunities at stationary spots against optional exploration bonuses.
