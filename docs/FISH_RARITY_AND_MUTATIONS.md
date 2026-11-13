# Fish Rarity, Mutations, and Catch Outcomes

Status: confirmed core rules; exact species odds, mutation rates, multipliers, and balance values remain to be tuned.

This document is the source of truth for how fish rarity and mutations work. Other documents should link here rather than inventing alternate rarity rules.

## 1. The non-negotiable identity rule

**A fish species has exactly one rarity value: its numerical species catch odds.**

Examples: `1/2`, `1/200`, `1/8,500`, `1/50,000`.

- The species is the fish. It has one stable species ID and one base rarity/odds value.
- Do not create Common, Uncommon, Rare, Epic, Legendary, Mythic, Secret, or similar rarity tiers.
- Do not give a mutation its own replacement rarity label or overwrite the species' rarity.
- A mutated fish is still the same species. A Golden Crystalfin is a Crystalfin with the Golden mutation, not a new fish species.
- The same species rarity is shown for the normal and mutated forms.
- A mutation's own roll chance is a separate implementation parameter, not a second rarity assigned to the fish.

A species may have one exact odds value in its catalogue. It must not have a collection of competing rarity labels or values.

## 2. Keep four concepts separate

| Concept | What it answers | Changes species rarity? |
|---|---|---|
| Species | Which fish did the player catch? | Defines its one rarity value |
| Mutation | What special trait does this individual fish have? | No |
| Size and weight | How large/heavy is this individual? | No |
| Catch conditions | Which species can appear in this situation? | No change to the species' identity |

These are not four rarity layers. Only the species has a rarity value.

### Example

A Crystalfin has species odds of `1/8,500`.

- Normal Crystalfin: species odds `1/8,500`.
- Golden Crystalfin: species odds `1/8,500`, mutation = Golden.
- Tiny Golden Crystalfin: species odds `1/8,500`, mutation = Golden, small individual weight.
- Record-sized normal Crystalfin: species odds `1/8,500`, no mutation, exceptional individual size.

The Fishbook must not display the Golden form as a new species or assign it a different species rarity.

## 3. Species odds and encounter selection

The species catalogue owns the single canonical odds value. It is configured once per species and is not rewritten by a mutation roll.

The fishing system must use a documented, deterministic server-side selection process:

1. Validate the player's fishing state, spot, equipment, and cast.
2. Build the eligible species pool from the current spot and approved conditions (such as water area, depth, time, weather, or a discoverable event).
3. Select a species using the approved odds/weighting model.
4. Resolve that species' individual outcome: mutation, size, weight, and any species-specific attributes.
5. Create one server-authoritative fish instance and grant it exactly once.

The exact probability model still needs a balancing contract before implementation. In particular, the team must specify whether catalogue odds are direct per-catch probabilities or relative weights within an eligible pool, and how the pool is normalised. Do not mix those interpretations or present relative weights as literal per-cast odds.

**Recommended contract:** treat the displayed species odds as the canonical baseline odds under the catalogue's reference conditions. Conditions may control eligibility and any explicitly approved encounter modifiers, but must never silently rewrite the species' stored rarity value. If modifiers change the actual chance in a given situation, the UI must not misleadingly present the baseline as the exact live chance; either show the baseline clearly as the species rarity or calculate and label a contextual chance separately. Do not introduce a second rarity tier.

Stationary fishing must retain a valid, rewarding pool and meaningful RNG opportunities. Exploration, events, time, and weather may add optional eligible species or opportunities, but must not make constant travel mandatory.

## 4. Mutations

A mutation is a roll applied to an already selected species. It changes that individual fish, not its species identity.

Mutation examples to explore:
- **Golden:** gold material/colour treatment, distinctive sparkle or catch reveal, and a configurable sell-value multiplier.
- **Luminous:** glowing markings or body accents, with a presentation effect appropriate to the species.
- **Crystal:** crystal growths or translucent crystalline features.
- **Shadow:** darkened palette and distinctive visual treatment.
- **Glacial:** frosted or icy visual treatment.

These are candidate mutation concepts, not a requirement that every fish supports every mutation. Each species should declare which mutations are compatible with its model and silhouette. A mutation must remain visually legible and should not make unrelated species look identical.

### Golden mutation example

A Golden Crystalfin remains a Crystalfin:
- Species ID: `crystalfin`
- Species odds: `1/8,500`
- Mutation ID: `golden`
- Sell-value multiplier: example placeholder `3.0x`, not a final balance decision
- Visual treatment: gold material/colour, controlled highlights, and a distinct reveal

The Golden mutation can make a catch more valuable without changing the species' odds. The multiplier is applied to the server-calculated value; the client cannot choose or modify it.

### Mutation compatibility and stacking

For the first implementation, support zero or one mutation per fish instance. This keeps the system understandable and avoids combinatorial visual/economy problems. Design the data shape so multiple compatible mutations could be considered later, but do not implement stacking until it has a clear gameplay and UI purpose.

Mutation compatibility must be explicit per species. Never roll a mutation that the species does not support.

A mutation can affect:
- Appearance and catch presentation.
- Sell value through a configured multiplier or additive rule.
- A Fishbook mutation-discovery record.
- Optional display or collection recognition.

A mutation should not automatically affect:
- Species identity or species odds.
- Fishing minigame difficulty.
- Catch success after the species has been selected.
- Progression power or combat-like stats.
- The fish's size/weight roll, unless a future approved design explicitly connects them.

Do not make every mutation a simple value multiplier. Some may be primarily visual/collectible. Avoid making ordinary non-mutated fish feel worthless.

## 5. Size, weight, and value

Each individual fish receives its own valid size and weight within the species' configured range/distribution. The server validates and generates these values.

A sale-value calculation should be transparent and server-owned. A future formula may combine:
- Species base value.
- Weight/size contribution.
- Mutation value modifier, if that mutation has one.
- Any explicit event or sale bonus.

Do not derive value from a hidden named rarity tier. The species' numerical odds may be one balancing input, but value must not become a runaway exponential reward that breaks the economy.

Define rounding, minimum/maximum values, and caps. Ensure a mutation multiplier is applied exactly once and cannot be stacked by duplicate requests or client-supplied attributes.

## 6. Fishbook and collection behaviour

The Fishbook is organised around species entries, with individual discoveries recorded beneath the species.

A species page should show:
- Species name and stable species ID internally.
- Its one canonical numerical rarity/odds display.
- Known habitat and discovered conditions.
- First-catch and personal size/weight records.
- Supported mutations and which ones the player has discovered.
- Optional notable individual catches.

Mutation discovery is a sub-record of the species, not a new species entry. The Golden Crystalfin belongs under Crystalfin. Selling or losing an individual fish must not erase the species or mutation discovery already recorded.

Keep these states distinct:
- Species discovered.
- Species caught.
- Mutation discovered for that species.
- Individual fish currently owned/stored/displayed/sold.
- Personal size/weight record.

Collection completion must not require every extremely low-probability mutation for essential progression. Rewards for difficult collection goals should be optional and proportionate.

## 7. Catch presentation

Presentation intensity may respond to the actual species odds and whether the individual has a mutation.

- Routine catches should be quick and readable.
- A mutation can add a distinct visual accent or reveal.
- A low-probability species can receive a stronger species reveal.
- A particularly notable combination (for example, an already uncommon species with a supported mutation and a personal record size) can receive a special presentation if it is genuinely meaningful.

Do not create named rarity bands just to select animations. Use numeric thresholds/configuration or explicit per-species presentation settings. Avoid making every mutation reveal interrupt the fishing loop.

## 8. Data and technical contract

Suggested conceptual data separation (adapt names to the actual project architecture):

**Species definition**
- `speciesId`
- `displayName`
- `baseOdds` (one canonical odds value)
- `eligibleHabitatIds` / condition rules
- `sizeWeightProfileId`
- `baseSellValue`
- `supportedMutationIds`
- optional presentation configuration

**Mutation definition**
- `mutationId`
- `displayName`
- `rollWeight` or explicit chance configuration
- visual configuration
- optional value modifier
- compatibility rules

**Fish instance**
- unique server-generated `instanceId`
- `speciesId`
- optional `mutationId` for the initial one-mutation implementation
- generated size and weight
- calculated/derived value data as appropriate
- exactly one authoritative owner and location/state

Keep species rarity and mutation roll configuration in separate fields/modules. Never copy a mutation chance into the species rarity field.

The server owns species selection, mutation rolls, size/weight generation, value calculation, inventory transfer, and reward delivery. Clients may request actions and render results; they cannot submit a chosen species, mutation, odds, size, weight, or sale value.

Persist stable IDs and validate them on load. Version the fish-instance and player collection schema. Migration must preserve existing species discoveries and individual fish without duplicating or changing their identity.

## 9. Probability and balance verification

Do not rely on a tiny playtest to validate extremely low odds.

Required checks before shipping:
- Deterministic tests for species eligibility and selection boundaries.
- Deterministic tests proving mutation rolls do not change species ID or species odds.
- Tests proving a Golden mutation is recorded on the original species entry.
- Tests proving mutation value modifiers apply once, server-side, with configured caps.
- Tests proving unsupported mutations cannot be generated.
- Tests for zero, one, and (if ever approved) multiple mutation handling.
- Statistical simulations at suitable sample sizes, with confidence intervals and expected-versus-observed comparisons.
- Tests for empty eligible pools, invalid odds, malformed IDs, disconnects, duplicate requests, and failed saves.
- Economy simulations covering common catches, low-probability species, mutation payouts, and extreme size/weight rolls.

For a species with a literal `1/N` chance, explain whether this means one success per N independent eligible catch rolls on average, not a guarantee after N attempts. Never use a pity counter or guaranteed-after-N mechanic unless explicitly designed and disclosed.

## 10. Open tuning decisions

These values are intentionally not final:
- Final species list and each species' numerical odds.
- Whether odds are direct probabilities or a normalised weighted-pool representation; settle this before implementing the live roll.
- Mutation chance/weight for each mutation and species compatibility.
- Golden and other mutation value modifiers.
- Size/weight distributions and value caps.
- Which conditions affect eligibility versus contextual odds.
- Whether any future species supports multiple simultaneous mutations.
- Presentation thresholds and special reveal rules.

Until these are decided, use clearly marked test data only. Do not present example odds or multipliers in this document as approved balance values.
