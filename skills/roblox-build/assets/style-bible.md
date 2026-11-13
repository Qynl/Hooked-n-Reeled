# Hooked-n-Reeled — Visual Style Bible

## Core visual identity

**Style:** polished stylized 3D tropical ocean adventure.

The visual target is the supplied tropical-island reference: rich turquoise water, chunky natural rock formations, lush palms and foliage, layered distant islands, occasional fantastical landmarks, bright open skies, and atmospheric sunlight.

This is **not** flat low-poly art, primitive block builds, or realistic PBR. Use simplified, deliberate geometry with rich composition, appealing colour, readable silhouettes, and controlled material detail.

**Mood words:** adventurous · sunlit · inviting · mysterious at the horizon

**Hero shot:** from a rocky, palm-covered beach looking across luminous turquoise shallows into a wide ocean channel, with layered islands, rock formations, and distant landmarks fading into atmospheric haze.

## Visual principles

1. **Stylized, not primitive.** Use faceted or smoothly simplified forms, intentional silhouettes, and carefully shaped terrain. Low polygon count must never look unfinished.
2. **Rich composition.** Foreground framing, midground islands, and distant silhouettes create depth. Avoid empty flat horizons.
3. **Fresh colour with restraint.** Ocean and vegetation carry the palette. Warm sand, stone, timber, and small coral accents provide contrast.
4. **Readable gameplay.** Fishing spots, interactables, docks, loot, and navigation landmarks must stand out without giant floating labels or excessive glow.
5. **Atmospheric distance.** Use colour shifts, haze, and silhouette simplification to make the world feel expansive.
6. **Consistent asset language.** Trees, rocks, buildings, boats, fish, and props share the same stylized proportions, edge treatment, and material response.
7. **Designed variation.** Reuse modular kits, but vary silhouette, scale, rotation, clustering, and local colour so repetition is not obvious.

## Palette

| Role | Colour | Hex | Use |
|---|---|---|---|
| Main shallow water | Clear turquoise | `#35C6C8` | Lagoons, reefs, near-shore water |
| Main ocean | Deep tropical blue | `#176B87` | Offshore water |
| Water highlight | Seafoam | `#A5E6D3` | Foam, shallow transitions, highlights |
| Vegetation | Island green | `#63B66B` | Grass, broad foliage |
| Vegetation shadow | Palm green | `#287C59` | Dense foliage, canopy depth |
| Sand | Warm sand | `#F1D49A` | Beaches, paths |
| Stone | Cool muted slate | `#777F91` | Rocks and cliffs |
| Timber | Sun-warmed wood | `#A96F45` | Docks, boats, buildings |
| Accent | Soft coral | `#F28B72` | Select props, flowers, readable accents |
| Sunlight | Warm gold | `#FFD477` | Small highlights, warm lighting |

These are art-direction anchors, not a rule that every object must use exact flat hex values. Use hue/value variation within each material family.

## Geometry and forms

- Terrain: broad, sculpted shapes with layered cliffs, coves, beaches, ridges, and occasional dramatic rock silhouettes.
- Rocks: chunky, faceted, varied silhouettes; combine large anchor rocks with smaller clustered stones.
- Trees: distinctive trunks and canopy silhouettes; palms should have readable fronds, not identical repeated stamps.
- Foliage: grouped masses with varied heights and leaf shapes; avoid noisy individual-leaf clutter.
- Architecture: clean, friendly coastal construction with timber, painted panels, cloth awnings, and readable roof shapes.
- Props: slightly exaggerated proportions and clear silhouettes.
- Avoid default-part-looking cubes, razor-sharp terrain spikes, excessive bevels, and random polygon noise.

## Materials and rendering

- Mostly matte or satin surfaces.
- Water is the visual hero: layered turquoise-to-blue colour, readable shallow/deep transitions, controlled reflections, gentle wave detail, and shoreline foam.
- Keep specular highlights controlled; avoid mirror-like water.
- Rock should have subtle value variation, not noisy photorealistic textures.
- Wood should show restrained stylized grain or plank separation.
- Avoid heavy outlines, excessive bloom, chromatic aberration, lens dirt, and over-sharpening.

## Lighting and atmosphere

- Default: bright tropical daytime with warm sun, soft but readable shadows, clear sky, and atmospheric distance.
- Use gentle haze on far islands and landmarks.
- Keep the image readable in gameplay camera conditions, not only in cinematic screenshots.
- Sunset, storms, night, and unusual events can shift the mood while preserving the same material and geometry language.
- Avoid crushed shadows and blown-out white sand or water.

## Composition rules

- Every major view should have foreground, midground, and background layers.
- Use islands, rock arches, trees, cliffs, and unusual silhouettes as navigation landmarks.
- Keep open-water routes visually legible.
- Do not fill every patch of land with props. Give beaches, docks, and fishing spots breathing room.
- Use colour contrast to separate land, water depth, and points of interest.

## Roblox performance constraints

- Prefer reusable modular meshes and shared materials.
- Use mesh/texture detail only where it materially improves the silhouette or close-up experience.
- Plan LOD or distance simplification for dense foliage and distant islands.
- Avoid excessive transparent foliage layers and large numbers of independent tiny parts.
- Use clustered assets and controlled instance counts; visual richness must not depend on thousands of tiny parts.

## Reference image workflow

The canonical image shot list and generation prompts live in [`docs/VISUAL_REFERENCE_PLAN.md`](../../../docs/VISUAL_REFERENCE_PLAN.md).

Generated images belong in [`assets/visual-references/`](./visual-references/). Keep the original generated image unchanged. Do not treat a concept image as an exact build specification: translate it into modular, measurable Roblox assets and a performant world layout.

## Do / don't

- DO: match the supplied tropical reference's water colour, layered islands, lush foliage, chunky rocks, and atmospheric depth.
- DO: create asset sheets with separate, clearly isolated objects on a consistent neutral background.
- DO: keep a coherent scale and camera language across all reference images.
- DO: give important locations memorable silhouettes, landmarks, and local visual details without requiring a formal biome system.
- DON'T: drift into generic flat low-poly starter-pack visuals.
- DON'T: make every island or fishing area visually identical; vary local scenery and atmosphere naturally.
- DON'T: use neon rarity glows as a substitute for good fish design.
- DON'T: generate collages with labels, UI, watermarks, or overlapping objects when the image is meant to be an asset source sheet.
