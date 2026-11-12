# World Events and Discovery — Hooked-n-Reeled

Status: confirmed design direction; cadence and exact content remain open.

## World identity

The world is seamless and ocean-first. Surface travel, fishing, and discovery are the core. Islands, ports, beaches, lighthouses, ruins, and other land features add landmarks and destinations, but land is not intended to become a second full-scale adventure game. Underwater exploration is not a core requirement for the initial design.

## Open-world activity ideas

These are a candidate activity pool, not all guaranteed launch features:
- Discovering islands, remote docks, ports, lighthouses, and unusual landmarks.
- Finding shipwrecks, drifting cargo, hidden coves, secret fishing spots, and strange signals.
- Following clues to rare fish habitats or temporary fishing windows.
- Taking delivery, recovery, research, and expedition tasks that make use of boats.
- Visiting travelling merchants, researchers, or other characters.
- Exploring unusual ocean formations, routes, and weather phenomena.
- Joining group expeditions and responding to boss sightings.

Activities should emerge naturally from travelling through the world. Avoid turning the ocean into a checklist of repetitive icons.

## Rare-fish clues

Use a mix of RNG and learnable conditions:
- Some clues only reveal where or when to look.
- Some clues improve odds or expand the eligible fish pool.
- Some exact combinations can guarantee that a particular fish or encounter becomes available.
- Some discoveries should be experimental and community-shareable.

A guaranteed encounter should mean the fish becomes available under the stated conditions, not that every cast automatically catches it. If a truly guaranteed catch is intended, its scope must be explicit. Keep natural random discovery viable so players can still be surprised.

Clues can be found in environmental details, fishbook entries, NPC dialogue, weather patterns, unusual schools, maps, or expedition discoveries. The fishbook should record what the player has learned without exposing every secret from the beginning.

## World events

Candidate event families:
- Fish migrations and unusually dense schools.
- Short weather windows that alter fish availability.
- Storms or ocean conditions that create new routes or risks.
- Rare fish sightings and temporary fishing hotspots.
- Wrecks, drifting objects, and temporary discoveries.
- Boss appearances and server-wide expeditions.

Events can be random, scheduled, condition-triggered, or discovery-triggered. Use a mix of announced and subtle events. Players should be able to understand the opportunity and its location without needing to watch a constant alert feed.

## Boss encounters

Bosses can appear:
- Randomly in the world.
- When specific environmental conditions align.
- As part of a world event.
- After a player or group discovers a secret.

Bosses should have a memorable introduction, distinct multi-phase fishing/combat-like encounter mechanics (without becoming a generic damage sponge), and a strong conclusion. Multiplayer boss encounters are shared: every eligible participant receives their own reward/catch, exactly once. The server owns eligibility and reward delivery.

Late-join eligibility, distance rules, disconnect handling, and contribution rules need a clear contract before implementation. Participation should be understandable and not punish players for using a different rod or joining a little later.

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
