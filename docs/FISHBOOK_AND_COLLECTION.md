# Fishbook and Collection — Hooked-n-Reeled

Status: confirmed direction; final UI, reward structure, and record scopes remain open.

## Two related but separate concepts

The fishbook records what a player has discovered. Inventory stores individual fish they currently own. These must not be conflated: selling a fish should not erase a species discovery, and registering a record should not duplicate the fish item.

## Fishbook scope

The intended direction combines:
- Species encyclopedia.
- Discovery tracking.
- Variant and mutation records.
- Size and weight records.
- First-catch and notable-catch history.
- Clues and habitat knowledge, including observations that can be made while fishing from a stationary spot.
- Collection milestones and rewards.

A species page may include its known habitat, eligible water regions, time/weather clues, naturally observed behaviour, and known variants. Unknown information can remain obscured until discovered. Clues should come from fishing, observation, environmental details, NPC dialogue, and exploration, not from requiring sonar, tracking devices, scanning gadgets, or research equipment.

## Records

Potential record categories:
- Personal heaviest and longest catch per species.
- Personal first catch and first variant discovery.
- Rare mutation discoveries.
- Boss catches and special event records.
- Optional server-wide or global records, if their moderation and persistence costs are justified.

Use clear scopes. A personal record is always available; global records are optional and should not be required for progression. Define tie-breaking, record reset rules, and validation on the server before implementing competitive leaderboards.

## Fish instance lifecycle

An individual caught fish should have a unique server-generated instance ID and a clear state/location:
- In personal inventory.
- Stored in a specific boat cooler.
- Displayed in an owned exhibit.
- Sold or consumed by a special-use system.

Every transfer must be atomic and idempotent. A fish cannot exist in two places or be sold twice. The species discovery can remain recorded after the individual fish is sold.

## Uses and choices

Fish have multiple meaningful destinations:
- Sell for currency.
- Keep for collection milestones or personal records.
- Display in personal or shared exhibits.
- Use selected species for quests, unlocks, research, or special activities.

Avoid making every fish's best choice obvious from a single coin value. Some fish can be valuable as discoveries, records, or unlock requirements. Clearly communicate irreversible choices before a player sells or consumes a particularly notable catch.

## Milestones

Collection rewards can include titles, cosmetics, boat decorations, fishbook upgrades, access clues, or other non-stat rewards. Avoid forcing completion of every rare mutation or extreme RNG tier for essential progression.

## Open decisions

- Whether the fishbook is account-wide or character/profile-specific.
- Which records are personal, server-wide, or global.
- How fish displays work and whether exhibits can be visited by friends.
- Exact special-use categories and whether consumed fish are recoverable.
- Whether the fishbook reveals partial clues or only confirmed discoveries.
