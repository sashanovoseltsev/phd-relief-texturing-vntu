# Relief Mapping Notes

Relief Mapping performs ray-heightfield intersection, usually in two phases:

1. Linear or coarse search along the ray.
2. Binary search refinement near the intersection.

It is closely related to POM, but the historical presentation emphasizes finding an interval with linear search and then refining that interval.

## Core Idea

The ray enters the height-field volume. Coarse stepping quickly finds a bracket:

- one sample before the surface;
- one sample after the surface.

Binary search then repeatedly tests the midpoint of that interval and keeps the half that contains the crossing.

## Why Binary Search Helps

Coarse stepping can find the correct neighborhood with relatively few samples, but the final UV can be rough. Binary search improves precision without needing many uniform layers from the start.

This is useful when:

- the height map has sharp features;
- the camera is close;
- the view angle is shallow;
- visual quality matters more than the cost of a few extra samples.

## Implementation Notes

- The first phase must actually bracket the crossing. Binary search cannot fix an interval that never contains the surface.
- Keep height/depth and sign conventions consistent with the POM implementation.
- Use the refined UV for all material texture samples.
- Compare against POM with the same maximum sample budget.

## Research Comparison Questions

- Does binary refinement visibly improve quality over linear interpolation for the same sample count?
- How many coarse steps are needed before binary refinement is reliable?
- Are artifacts mostly caused by the coarse bracket, by UV bounds, or by height-map resolution?
