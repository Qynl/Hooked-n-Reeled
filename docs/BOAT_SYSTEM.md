# Boat System — Hooked-n-Reeled

Status: confirmed design direction; detailed balancing and implementation contracts remain open.

## Product role

Boats are a major progression and personalization pillar. They are the player's way to move through the ocean-first open world, travel with friends, carry fish storage, and express their own style. In the planned underwater phase, boats can also serve as convenient expedition starting and regrouping points, without requiring special detection gadgets or making a boat mandatory for every dive. A boat should feel like a useful personal vessel, not just a speed stat with a seat.

## Acquisition and progression

Players can buy new boat hulls and upgrade owned boats. Candidate upgrade dimensions:
- Speed and acceleration.
- Handling and turning.
- Stability in rough conditions.
- Durability or resilience during special encounters.
- Storage capacity and cooler support.
- Specialized functions for exploration, group trips, or certain fishing activities.

Avoid one universally optimal boat. Different hulls should make different trade-offs, and older boats should remain viable for some roles. Cosmetic appearance should be freely expressive where possible and not secretly determine power.

## Onboard free placement

**Decision:** players should be able to place suitable objects on their boat with minimal UI and near-free positioning.

Expected interaction:
1. Open a contextual edit mode.
2. Select an owned object.
3. Move and rotate a placement preview.
4. Confirm or cancel.
5. Reposition, pick up, or remove objects later.

Optional snapping can help precision but should not be mandatory. The player should feel that they are arranging their own boat, not filling a rigid furniture grid.

### Placement rules

Every placeable definition should declare:
- Stable item ID and category.
- Footprint/bounds and allowed boat classes.
- Whether it is functional, decorative, or both.
- Whether it needs access clearance.
- Whether it can be used while the boat is moving.
- Whether guests can interact with it.
- Placement limits and any power/weight budget if those systems are later introduced.

The server validates ownership, allowed build area, collision/overlap constraints, item limits, and permissions. Clients may preview placement but cannot authoritatively save arbitrary transforms.

Do not allow objects to block the helm, seats, fishing stations, boarding points, or other required interactions. Avoid excessive invisible restrictions that make placement feel fake. Provide a clear preview when placement is invalid.

## Coolers and fish storage

Coolers are the primary onboard fish-storage feature:
- Players can buy different coolers.
- Coolers can be placed on the boat.
- Coolers can be upgraded, especially for capacity.
- Capacity and contents should be easy to inspect through a compact contextual interface.

Do not silently discard a catch when storage is full. Define a clear overflow flow before implementation. Candidate choices include keeping the fish in personal inventory, transferring it to another available storage location, or explicitly declining it where appropriate.

A stored fish must have one authoritative instance ID and one owner. Transfers between personal inventory and coolers must be atomic and server-authoritative. Selling or moving an item must invalidate its previous location so it cannot be duplicated.

## Multiplayer permissions

The boat owner remains the owner of the vessel and its placed objects. Guests may be granted separate permissions for:
- Boarding and riding.
- Using designated fishing stations.
- Accessing coolers.
- Placing or moving objects.
- Editing the overall layout.

Default permissions should be conservative and easy to understand. A guest should never be able to take, sell, delete, or move another player's stored fish or objects without explicit permission.

## Future underwater expedition support

When underwater exploration is introduced, boats may provide a natural place to begin and end a dive, regroup with friends, and store ordinary expedition supplies if the final design needs them. Do not assume a dedicated sonar, scanner, tracker, or research station is required. Shore-based entry should remain possible at suitable locations, and boat ownership must not become a gate to all underwater content.

This is a future integration point, not a requirement for the current boat prototype. Define dive-entry interaction and any storage needs in the underwater feature contract before implementation.

## UX principles

- Minimal, contextual UI; the boat and the world stay visually dominant.
- Placement controls must work on PC, mobile, and controller.
- Show capacity and storage state at the point of interaction.
- Make it easy to recover a misplaced object.
- Provide a reset/undo path for layout edits if practical.
- Save layout by boat identity, not by fragile instance names.

## Open decisions

- Whether placed objects persist per hull, per player, or per owned boat slot.
- Whether players can own multiple active boats or store inactive boats.
- Exact cooler tiers, capacities, and prices.
- Whether boat upgrades can be reset or transferred.
- Whether guests can use a cooler without being allowed to remove items.
- How boat destruction, reset, or server migration affects stored fish and layout.
