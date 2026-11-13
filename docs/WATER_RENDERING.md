# Hero Water Rendering Specification

Status: required visual direction for M0; implementation must be proven in Roblox Studio before it is called complete.

## The target

The ocean is the main visual feature of Hooked-n-Reeled. It must not read as a flat, uniformly coloured blue/turquoise plane. The target is a rich, layered, luminous water surface whose appearance comes from light, reflections, transparency cues, wave shape, depth, foam, and movement working together.

The water in the visual reference is an art-direction target, not a demand to reproduce an unavailable custom shader. The result should feel spectacular at boat height and remain convincing from the world overview.

**Colour is only one input.** Do not try to solve water by choosing a better Color3, adding a blue tint, or changing Terrain water properties alone.

## Visual qualities that must be visible

1. **Layered surface response:** broad, slow swells under smaller wind ripples. Avoid a perfectly flat plane or a noisy choppy texture.
2. **Moving highlights:** broken, elongated sun glints that move with the wave pattern. Highlights should gather on wave faces and shift with view/light direction rather than appear as static white stripes.
3. **Reflective sky and environment:** readable soft reflections with a clear horizon response. Reflections should be lively but not a mirror.
4. **Depth and transparency cues:** shallow water reveals sand, rocks, reef shapes, and seabed detail. Water transitions gradually into richer, darker open-water depth. Never rely on a hard ring of different flat colours.
5. **Shoreline interaction:** thin, irregular foam at beaches and rocks, small wavelets, subtle wet/darker shoreline edges, and occasional foam breakup. Avoid a thick white outline around every island.
6. **Surface movement:** the water must have visible motion even when the player is stationary. Use more than a scrolling colour texture.
7. **Scale variation:** broad swell reads at distance; fine ripples and small glints read near the player. The ocean must not look like a tiled repeating texture.
8. **Underwater continuity:** from below, the surface should remain a bright, moving ceiling with readable sun shafts and a believable falloff into depth.

## Roblox implementation strategy

Roblox does not expose arbitrary custom real-time water shaders to ordinary Luau scripts. Do not promise physically correct refraction, screen-space reflection, or a fully custom shader unless the engine actually provides it in the target environment. Build the best layered solution supported by Roblox and verify it in Studio.

### Surface foundation

- Use Roblox Terrain water only if the prototype proves it meets the visual target. It is a fast baseline, not an automatic final answer.
- For the hero surface, prototype a custom water mesh/mesh system with a controlled topology, shared materials, and a small number of large sections. It must support the continuous ocean and not create visible seams between chunks.
- Use a deliberately authored water material/texture set where supported: colour/albedo variation, normal detail, roughness response, and subtle directional patterning. Avoid relying on a single flat material colour.
- Use layered wave geometry or supported mesh deformation/animation for broad swell. If true vertex deformation is not available at runtime, use an authored animated mesh/bone approach or layered surface forms that preserve a continuous horizon. Do not fake waves with hundreds of individual parts.
- Add a separate, subtle fine-ripple layer only if it improves the close-up view. It must not look like a second transparent sheet floating above the sea.

### Lighting and reflections

- Set up the scene for high-quality environment response using the supported modern lighting mode and environment specular settings.
- Use a suitable sky/environment so the water has something attractive to reflect. A high specular setting without a good environment does not create beautiful reflections by itself.
- Tune water roughness/reflectivity to produce broad, soft reflections with moving bright accents, not chrome.
- Test the same water at midday, sunset, overcast, and storm conditions. Lighting changes should alter the water's mood without destroying depth readability.
- Keep bloom restrained. Water glints should be bright because of the surface response, not because the entire ocean is overexposed.

### Depth, shallows, and seabed

- Build a continuous seabed with gradual shelves and deeper channels. Surface appearance should be driven by actual depth and what lies below it.
- In shallow areas, let the player read the sand, rock, and reef through the water using supported transparency/visibility techniques. If the chosen water surface cannot provide true refraction, use carefully aligned shallow-water materials and seabed colour/value contrast to imply it without obvious hard boundaries.
- Open water should gain depth through layered visibility, atmospheric distance, and diminishing seabed visibility, not simply a dark-blue paint bucket.
- Avoid a visible flat colour ring at the boundary between shallow and deep areas.
- Do not cover the whole seabed with bright decorative textures. Keep enough darker open water to establish scale.

### Foam and coastline

- Foam belongs at interactions: shore breaks, rock edges, reefs, wakes, and wave convergence.
- Use irregular foam meshes/textures or authored shoreline strips with variation in width, opacity, and breakup.
- Foam should be localised and animated subtly. Avoid a continuous white outline around all coastlines.
- Boat wakes can be a later gameplay-integrated effect; M0 only needs representative water/shoreline proof.

## Performance and architecture

- Prefer a small number of large, reusable mesh sections and shared materials over thousands of Parts.
- Avoid excessive overlapping transparent surfaces; transparency overdraw is expensive and can produce sorting artefacts.
- Use level-of-detail or distance falloff for fine ripples, foam and high-frequency detail. Far water needs broad coherent motion, not close-up texture density.
- Keep water chunk edges hidden below the visible surface or use a seam-safe shared grid and matching wave phase across neighbouring sections.
- Use a deterministic shared wave phase so adjacent sections do not drift apart.
- Profile on a representative mobile device as well as desktop. Water is always on screen, so its frame cost matters continuously.
- Provide quality levels: high detail near the player, reduced fine detail at distance, and a low-cost fallback for weaker devices. Preserve the overall water identity at every quality level.
- Keep the water renderer modular and configurable. Do not bake all water appearance into a giant one-off Studio script.

## M0 prototype and review requirements

Before the full ocean is dressed, build a small water test scene containing:
- A beach with pale sand visible through shallow water.
- A rocky shoreline with broken foam.
- A reef or submerged rock patch.
- A clear shallow-to-deep transition.
- A wide open-water horizon.
- A boat-height camera and an elevated overview camera.
- A simple underwater camera looking up at the surface.

Capture screenshots or video of the same scene in bright daylight and one alternate lighting condition. Review the water at boat height, not only from far above.

### Acceptance checklist

- [ ] It does not read as a flat single-colour plane.
- [ ] Broad swell and fine surface movement are both perceptible.
- [ ] Moving highlights/glints respond convincingly to lighting and wave shape.
- [ ] Reflections contribute to the look without becoming mirror-like.
- [ ] Shallow seabed detail is visible and transitions naturally toward depth.
- [ ] Shoreline foam is irregular, restrained, and placed only where water meets geometry.
- [ ] No obvious repeating texture, chunk seams, or transparent-layer sorting artefacts.
- [ ] It looks impressive from boat/player height and coherent from the overview.
- [ ] It remains readable in overcast/storm lighting and from underwater.
- [ ] Desktop and mobile performance are measured and recorded.

If any of these checks fail, the water is not visually approved. Do not mark the M0 ocean complete just because the map has a water surface.

## Explicitly avoid

- One flat blue/turquoise Part or Terrain water plane as the finished result.
- Solving the entire look with a Color3 or colour gradient.
- A static normal texture with no broad movement.
- Repeating bright wave stripes or obvious tiling.
- A mirror-polished surface.
- Opaque water that hides every shallow feature.
- A thick white foam border around every island.
- Hundreds or thousands of small Parts used as fake waves.
- Claims of true refraction or custom shader effects that have not been demonstrated in Roblox Studio.

## Decisions still open

The exact mesh/animation technique, texture source, wave amplitude/speed, reflection tuning, foam method, and quality-tier thresholds must be selected through the M0 prototype. These are technical implementation choices, not reasons to lower the visual target.
