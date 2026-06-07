# Parallax Occlusion Mapping Notes

Parallax Occlusion Mapping is a refined form of steep parallax mapping.

The shader represents the view ray in tangent/texture space, marches through height/depth layers, detects where the ray crosses the height field, and returns a corrected UV coordinate for sampling albedo, normal, roughness, etc.

## Core Algorithm

1. Convert view direction to tangent space.
2. Choose a number of layers, often more at grazing angles.
3. Compute per-layer depth step.
4. Compute per-layer UV step from `viewDirTS.xy / viewDirTS.z`.
5. March through the height field until the ray depth crosses the sampled height/depth value.
6. Refine the final UV using linear interpolation or a short binary search.
7. Sample material textures at the corrected UV.

## Geometric Intuition

Imagine a side view of the height field. The view ray moves diagonally through a box of depth from `0` to `1`. Each layer asks:

> At this depth along the ray, is the ray still above the height surface, or has it entered the solid part of the relief?

The first crossing gives the visible point.

## Linear Interpolation After Crossing

When a crossing is found, the previous sample was before the surface and the current sample is after the surface. Linear interpolation estimates a better UV between them.

This is cheaper than binary search and often good enough for POM.

## Important Implementation Notes

- Be explicit whether the texture stores `height` or `depth`.
- Use a stable sign convention for UV stepping.
- Clamp or handle UVs that leave the valid texture range.
- Increase sample count at grazing angles because `viewDirTS.z` becomes small.
- Use the same corrected UV for albedo and normal sampling, otherwise lighting and color will not agree.

## Possible Debug Outputs

- Output `viewDirTS * 0.5 + 0.5` as color.
- Output final `parallaxUV` as red/green.
- Output number of steps used.
- Output current ray depth at intersection.
- Temporarily disable normal mapping to isolate UV displacement artifacts.
