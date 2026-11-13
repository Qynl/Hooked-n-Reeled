# Hooked-n-Reeled — Visual Reference Plan

## Purpose

Build a coherent visual library before detailed world construction. The supplied reference image is the primary style anchor: a polished stylized 3D tropical ocean environment with vivid turquoise water, chunky rock formations, lush palms, layered islands, atmospheric distance, and bright cinematic daylight.

This is a **reference-generation plan**, not a claim that any images or game assets have already been created.

## Agent interpretation rule — applies to every image

All images in `docs/visual-references/` are **conceptual inspiration only by default**. They are not final game assets, final designs, confirmed content lists, or instructions to reproduce pictured objects exactly. This applies to every current and future image, not only the fish sheet.

In particular, `Fish_IDeas.png` (also informally called `fishideas.png`) is a fish-art-direction moodboard: it suggests possible visual variety and rarity presentation only. It does not define the actual species roster, exact fish designs, names, rarity values, stats, or models. Boat, equipment, nature, map, location, underwater, and atmosphere references follow the same rule.

Agents must use the images to understand style, shape language, palette, mood, and possible directions, then create original designs that fit confirmed written specifications and practical Roblox constraints. Never infer mechanics, stats, prices, progression, species, geography, or required asset lists from a concept image. Written confirmed decisions take precedence over images. An image only becomes an approved design when the user explicitly approves that specific design or a written specification confirms it. Even then, the production Roblox asset must be built separately and optimised.

See [the visual-reference README](visual-references/README.md) for the status workflow and detailed rules.

## Image-generation rules

- Generate one image per numbered reference unless a row explicitly requests a single asset sheet.
- Keep all images in the same visual style: polished stylized 3D, deliberate low-poly geometry, rich but controlled colours, bright natural lighting, atmospheric depth.
- No text, labels, UI, watermarks, logos, borders, or typography unless a later UI reference explicitly requests them.
- Asset sheets: one image containing many **separate, fully visible, non-overlapping** objects, evenly spaced on a plain neutral background. Use a consistent three-quarter view and consistent scale within each category.
- World images: environment concept art, wide 16:9 landscape framing unless otherwise stated.
- Map images: clean top-down orthographic planning view, no perspective distortion. Keep geography readable.
- Keep a stable visual style across all prompts. Do not let each prompt invent a different rendering style.
- Save originals without cropping or editing. If variants are generated, append a version suffix.
- Concept art is not a production asset. Rebuild approved designs as performant, modular Roblox geometry.

## Master style phrase

Append this style phrase to environment and asset prompts:

> polished stylized 3D tropical adventure game art, deliberate low-poly geometry with rich sculpted forms, vibrant fresh colours, turquoise and deep-blue ocean, lush layered vegetation, chunky natural rock formations, warm sunlight, soft readable shadows, atmospheric depth, high-quality game environment concept art, cohesive art direction, no text, no UI, no watermark

---

# Stage 1 — World layout and fishing-area planning

## 01 — Master world overview

**Filename:** `01_world_overview.png`  
**Format:** 16:9 wide environment panorama.

**Prompt:**

> Create a breathtaking wide establishing view of the entire Hooked-n-Reeled game world, a large connected tropical ocean archipelago. Show a broad turquoise-to-deep-blue ocean with multiple distinct island groups, small sandy coves, rocky coastlines, palm-covered islands, distant cliffs, a few unusual floating rock formations and memorable far-horizon landmarks. Compose the scene in clear foreground, midground, and background layers so the world feels huge and explorable. Make the ocean the dominant visual element and leave believable navigable channels between island groups. The image should feel like a real playable open-world game environment, not a map or collage. [MASTER STYLE PHRASE]

## 02 — World map layout

**Filename:** `02_world_map_layout.png`  
**Format:** 16:9 top-down orthographic map concept.

**Prompt:**

> Create a clean top-down orthographic world-planning map for a large ocean fishing adventure. Show a connected archipelago with clearly separated island clusters and broad navigable ocean routes. Include a central starter region and main port, several distinct fishing grounds, remote outer islands, hidden coves, reefs, open-water fishing grounds, and a few distant endgame landmarks. Use simple readable terrain silhouettes and clear water-depth and location distinctions. No labels, no icons, no UI, no compass, no text. Geography must be clear enough to translate into a Roblox world layout. [MASTER STYLE PHRASE]

## 03 — Underwater world cutaway

**Filename:** `03_underwater_world_cutaway.png`  
**Format:** 16:9 wide underwater environment concept with a readable surface-to-seabed relationship.

**Prompt:**

> Create a polished stylized 3D underwater world concept for Hooked-n-Reeled, showing the underwater layer of the same connected tropical ocean. Compose a wide underwater view with a bright surface visible above, sunbeams reaching through clear turquoise water, a reef garden in the foreground, a rocky shelf descending into a deeper ravine, a distant cave opening, and the silhouette of a sunken wreck. Include a few natural crystal formations integrated into the rock, shells and coral, and small distant sea-life silhouettes. The scene should feel explorable and full of discoveries, not frightening or photorealistic. Keep the environment visually connected to the surface world. No divers, no equipment gadgets, no sonar UI, no text, no labels. [MASTER STYLE PHRASE]

## 04 — Ocean zones and water transitions

**Filename:** `04_ocean_zones.png`  
**Format:** 16:9 wide environment study.

**Prompt:**

> Show a wide stylized ocean environment study with clearly visible water zones transitioning from pale transparent aqua over white sand, to bright turquoise lagoon, to rich teal reef water, to deep tropical blue offshore. Include subtle underwater silhouettes, reef patches, wave patterns, shoreline foam, and several small rock outcrops. The water should be beautiful and readable, with controlled reflections rather than photorealistic mirror gloss. [MASTER STYLE PHRASE]

---

# Stage 2 — Environment asset sheets

## 05 — Nature asset sheet

**Filename:** `05_nature_asset_sheet.png`  
**Format:** one large 3:2 or 16:9 asset sheet on a plain light neutral background.

**Prompt:**

> Create a professional 3D game environment asset library sheet containing many separate, fully visible, non-overlapping stylized low-poly tropical nature assets. Include several different palm trees, broad-canopy tropical trees, short trees, dead trees, leafy bushes, small shrubs, ferns, broad-leaf plants, flowers, grass clumps, reeds, vines, driftwood, small stones, medium rocks, large angular boulders, rock clusters, coral pieces, and beach plants. Arrange every asset individually in a neat grid with generous spacing. Show each object from a consistent three-quarter view, with consistent studio lighting and a plain warm light-grey background. No ground scene, no island diorama, no text, no labels, no shadows crossing into neighbouring assets, no overlapping objects. Every object must be easy to identify and usable as a separate modelling reference. [MASTER STYLE PHRASE]

## 06 — Rock and terrain formation sheet

**Filename:** `06_rock_terrain_asset_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a modular stylized 3D environment asset sheet of separate terrain and rock formations for a tropical ocean adventure. Include small shoreline stones, medium boulders, large faceted boulders, layered cliff chunks, flat rock shelves, steep cliff sections, sea-arch pieces, cave entrances, pointed distant rock spires, reef rocks, and several floating-rock shapes. Arrange each piece separately with generous spacing in a consistent three-quarter view. Plain neutral background, no island scene, no text, no labels, no overlap. [MASTER STYLE PHRASE]

## 07 — Coastal architecture asset sheet

**Filename:** `07_coastal_architecture_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a cohesive modular architecture asset sheet for a colourful tropical fishing world. Show separate complete building and structure references: small fishing huts, coastal houses, fish market stall, bait shop, boat workshop, wooden pier sections, dock corners, dock posts, rope railings, small bridges, stairs, lookout platform, covered seating shelter, lighthouse, signboards, lamps, crates, barrels, and cloth awnings. Friendly handcrafted coastal architecture, sun-warmed timber, painted panels, simple roof shapes, clean stylized geometry. Arrange each asset separately with generous spacing on a plain neutral background. No environment scene, no text, no labels, no overlap. [MASTER STYLE PHRASE]

## 08 — Ocean props and discovery asset sheet

**Filename:** `08_ocean_props_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a separate-object 3D game asset sheet for ocean exploration and fishing discoveries. Include floating wooden crates, barrels, buoys, mooring posts, anchors, fishing nets, rope coils, life rings, treasure chests, broken ship timbers, shipwreck hull fragments, old cannons as harmless scenery props, coral clusters, shells, giant clams, driftwood, message bottles, and small decorative wreckage. Each object must be isolated, fully visible, non-overlapping, and evenly spaced on a plain neutral background. Consistent three-quarter view and studio lighting. No scene, no text, no labels. [MASTER STYLE PHRASE]

## 09 — Underwater environment asset sheet

**Filename:** `09_underwater_asset_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a separate-object stylized 3D asset sheet for underwater scenery: branching coral, rounded coral, tube sponges, sea fans, sea grass, kelp clusters, anemones, shells, starfish, reef rocks, underwater cave rocks, small wreck fragments, and decorative aquatic plants. Use a fresh but controlled palette of turquoise, seafoam, coral, violet, and ocean blue. Every asset isolated and non-overlapping on a plain neutral background, consistent three-quarter view, no underwater scene, no text, no labels. [MASTER STYLE PHRASE]

---

# Stage 3 — Key locations

## 10 — Starter island

**Filename:** `10_starter_island.png`  
**Format:** 16:9 playable environment concept.

**Prompt:**

> Design the first island players discover in Hooked-n-Reeled. Show a welcoming small tropical island with a curved pale-sand beach, turquoise shallows, a few distinctive palm trees, chunky rock formations, a small wooden arrival dock, a modest fishing hut, a clear first fishing spot, and a visible route out toward the wider ocean. Compose it as a believable Roblox gameplay environment with clear paths and readable spaces, not a cinematic inaccessible landscape. [MASTER STYLE PHRASE]

## 11 — Main fishing port

**Filename:** `11_main_fishing_port.png`  
**Format:** 16:9 playable environment concept.

**Prompt:**

> Design the main social and progression hub of Hooked-n-Reeled: a lively tropical fishing port built around a sheltered turquoise harbour. Include a large welcoming dock network, boat moorings, fish market, bait and rod shops, boat workshop, fish display area, small coastal buildings, signs, seating, and a clear open central gathering area. Show boats in the harbour and lush rocky islands beyond. Make the layout readable and practical for multiplayer players moving between services. [MASTER STYLE PHRASE]

## 12 — Remote fishing outpost

**Filename:** `12_remote_outpost.png`  
**Format:** 16:9 playable environment concept.

**Prompt:**

> Design a small remote fishing outpost on a rocky tropical island far from the main port. Include a compact dock, a weathered but charming shelter, a small supply point, a lookout, a few palms and shrubs, unusual rock shapes, and deep blue fishing waters nearby. It should feel like a useful expedition stop and a memorable landmark, not a second main town. [MASTER STYLE PHRASE]

## 13 — Landmark collection

**Filename:** `13_world_landmarks_sheet.png`  
**Format:** one sheet with 8 separate landmark concepts.

**Prompt:**

> Create one cohesive concept sheet showing eight separate large-scale navigational landmarks for the same stylized tropical ocean world: a giant natural sea arch, a tall isolated rock spire, a waterfall island, a cliffside lighthouse, a ring-shaped lagoon, a cluster of floating rocks, a hidden cove entrance, and a giant shipwreck silhouette. Show each landmark separately in a small environment vignette with consistent visual style and scale cues. No labels or text. [MASTER STYLE PHRASE]

---

# Stage 4 — Boats and fishing equipment

## 14 — Boat family sheet

**Filename:** `14_boat_family_sheet.png`  
**Format:** one sheet, separate boats on neutral background.

**Prompt:**

> Create a polished 3D concept sheet of a progression family of stylized fishing and exploration boats for the same tropical ocean game. Show several clearly distinct boat silhouettes from small starter skiff, compact motorboat, open fishing boat, covered cabin boat, larger expedition vessel, to a premium late-game fishing boat. Each boat shown separately from a consistent three-quarter front-side view, fully visible, with believable proportions and clear deck space. Cohesive design language, fresh colours, warm timber and painted hulls. Plain neutral background, no water scene, no text, no labels, no overlap. [MASTER STYLE PHRASE]

## 15 — Boat customization kit

**Filename:** `15_boat_customization_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a separate-object modular customization asset sheet for stylized fishing boats. Include seats, steering consoles, small engines, cabin modules, railings, rod holders, fishing chairs, coolers in several sizes, storage boxes, lights, flags, canopies, ladders, decorative plants, bumpers, ropes, and deck decorations. Each object isolated and fully visible, consistent three-quarter view, plain neutral background, no boat scene, no labels, no overlap. [MASTER STYLE PHRASE]

## 16 — Fishing equipment sheet

**Filename:** `16_fishing_equipment_sheet.png`  
**Format:** one asset sheet, neutral background.

**Prompt:**

> Create a polished stylized 3D fishing equipment asset sheet with separate complete objects: several fishing rod silhouettes, reels, rod stands, tackle boxes, bait containers, bait jars, nets, hooks, floats, line spools, small fish buckets, and portable fishing gear. Make the designs readable and appealing, with a cohesive colour language and clear differences between starter and advanced equipment. Arrange each item separately on a plain neutral background, no text, no labels, no overlap. [MASTER STYLE PHRASE]

## 17 — Fishing spot visual language

**Filename:** `17_fishing_spot_types.png`  
**Format:** one sheet with 6 small environment vignettes.

**Prompt:**

> Create a cohesive visual concept sheet of six fishing spot types in a stylized tropical ocean game: calm shallow lagoon, coral reef edge, open deep-water current, rocky coast, sheltered mangrove inlet, and a rare shimmering fish-school area. Each vignette should clearly communicate the water, terrain, and fish activity that make the spot distinct. No UI markers, no labels, no text. [MASTER STYLE PHRASE]

---

# Stage 5 — Atmosphere and water studies

## 18 — Weather and time-of-day sheet

**Filename:** `18_weather_lighting_sheet.png`  
**Format:** one sheet with 5 equal environment panels.

**Prompt:**

> Create five equal panels showing the exact same stylized tropical island coastline under different conditions: clear bright midday, warm sunset, overcast calm weather, dramatic distant storm, and peaceful moonlit night. Keep geometry, camera angle, and composition identical so only lighting, sky, atmosphere, and water mood change. Preserve readability and the same polished stylized 3D art direction. No text or labels.

## 19 — Water and shoreline close-up

**Filename:** `19_water_shoreline_study.png`  
**Format:** 16:9 close environment study.

**Prompt:**

> Create a close, beautiful stylized 3D study of a tropical shoreline showing transparent pale-aqua shallows over sand, turquoise water around rocks, gentle layered waves, soft white foam at the beach, underwater stones visible through clear water, and a transition into deeper blue. Focus on how water meets sand and rock. Bright natural sunlight, controlled reflections, no people, no text. [MASTER STYLE PHRASE]

---

# Stage 6 — Underwater locations and discoveries

## 20 — Underwater location collection

**Filename:** `20_underwater_location_collection.png`  
**Format:** one cohesive sheet with three separate wide environment vignettes.

**Prompt:**

> Create a cohesive stylized 3D game-environment concept sheet with three separate underwater location vignettes for Hooked-n-Reeled: (1) a colourful reef garden with coral arches, sea plants, fish schools, and a hidden crevice; (2) a rocky underwater cave with a visible entrance, layered shelves, a few natural crystal seams, and a secret chamber; (3) a sunken wooden shipwreck resting near a ravine, with broken hull sections, scattered cargo, shells, and shafts of sunlight. Make each location feel like a distinct explorable place connected to the same tropical ocean. Clear readable navigation, rich but controlled colours, no divers, no gadgets, no UI, no labels, no text. [MASTER STYLE PHRASE]

## 21 — Underwater discoveries sheet

**Filename:** `21_underwater_discoveries_sheet.png`  
**Format:** one asset sheet on a plain neutral background.

**Prompt:**

> Create a polished stylized 3D asset sheet of separate underwater discoveries for a tropical ocean adventure game. Include several distinct natural crystal and mineral formations, small and large crystal clusters, unusual shells, pearls, giant clams, fossils, rare coral specimens, sea-glass-like natural fragments, weathered cargo objects, and a few small ancient-looking artefacts. Every object must be isolated, fully visible, non-overlapping, and evenly spaced on a plain neutral background. Use a consistent three-quarter view, cohesive stylized low-poly art direction, and a controlled palette of turquoise, deep blue, seafoam, violet, warm sand, and coral accents. No text, labels, UI, or watermarks. [MASTER STYLE PHRASE]

---

## Suggested generation order

1. `01_world_overview.png`
2. `02_world_map_layout.png`
3. `03_underwater_world_cutaway.png`
4. `05_nature_asset_sheet.png`
5. `06_rock_terrain_asset_sheet.png`
6. `07_coastal_architecture_sheet.png`
7. `10_starter_island.png`
8. `11_main_fishing_port.png`
9. Generate the remaining surface sheets and location concepts.
10. Generate `20_underwater_location_collection.png` and `21_underwater_discoveries_sheet.png` when planning the underwater milestone.

Do not generate every image at once. Approve the overall world layout first; then generate assets for the locations and fishing areas that are actually needed.

## Approval checklist

- [ ] Master world overview approved
- [ ] World geography and island distribution approved
- [ ] Nature asset language approved
- [ ] Rock and terrain language approved
- [ ] Architecture language approved
- [ ] Starter island approved
- [ ] Main port approved
- [ ] Boat family approved
- [ ] Water and lighting studies approved
- [ ] Underwater visual direction approved
- [ ] First underwater location concepts approved
- [ ] Underwater discovery art direction approved

## Image index

| ID | Filename | Status | Notes |
|---|---|---|---|
| 01–21 | See sections above | Planned | No generated references committed yet |
