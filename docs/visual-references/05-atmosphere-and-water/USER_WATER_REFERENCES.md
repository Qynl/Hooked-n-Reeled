# Surface and Underwater Water References

**Status:** user-approved visual direction for the M0 water prototype  
**Date added:** 2026-11-14  
**Branch:** `QynlIdeas`

This document records the two visual references supplied directly by the user in the project conversation. They are art-direction references, not production assets or a demand to reproduce a particular rendering technique.

## Reference A — Surface ocean

The first image shows a stylized close view of a lively turquoise ocean:
- Broad, rounded, irregular teal and cyan wave masses.
- Deep blue-green pockets between raised wave forms.
- Strong, bright white foam networks branching and connecting between waves.
- Smaller white streaks, holes, tendrils, and broken foam islands.
- A fluid, organic pattern rather than a regular grid or repeated stripe texture.

**Implementation intent:** create animated, irregular foam masks/meshes coordinated with broad wave movement. White foam should be prominent enough to define the ocean's identity, but not blanket the entire surface. Near shore, larger breaking waves and denser foam can create extra energy.

## Reference B — Underwater environment

The second image shows a stylized underwater reef:
- Bright cyan-blue water with sunlight entering from above.
- Crisp nearby rocks, coral, plants, and fish.
- A readable seabed and clear foreground-to-background composition.
- Distant scenery becoming less distinct through blue atmospheric haze.
- Stronger depth mood without turning the scene opaque or murky.

**Implementation intent:** finite underwater visibility. Preserve nearby gameplay readability, soften mid-distance forms, and fade distant scenery into blue haze. Deeper water should reduce visibility and light penetration further. Do not allow the player to see infinitely far underwater.

## Required prototype camera tests

1. Surface close-up: confirm irregular white foam networks visibly animate with the waves.
2. Boat height: confirm open-ocean foam and larger shore breaks read at normal gameplay distance.
3. Shallow underwater: foreground detail is crisp, midground softens, and distant forms fade.
4. Deep underwater: stronger blue attenuation and reduced light reach, while nearby routes and objects remain readable.
5. Performance: test the same effects on desktop and a representative mobile device.

## Technical guardrails

- Use Roblox-supported geometry, materials, textures, lighting, atmosphere, and camera-side effects.
- Do not claim unsupported custom shaders, true refraction, or screen-space effects without an actual Studio proof.
- Avoid a static foam decal, repeated white stripes, a continuous white island outline, a hard circular underwater fog wall, and excessive transparent layers.
- Treat the reference images as the visual target; choose the implementation technique through the M0 prototype.

## Related specifications

- [Hero Water Rendering Specification](../WATER_RENDERING.md)
- [Visual Style Bible](../../skills/roblox-build/assets/style-bible.md)
- [Production Milestones](../MILESTONES.md)
