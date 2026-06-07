# Cone Step Mapping Notes

Cone Step Mapping accelerates ray-heightfield intersection by using precomputed safe-step information.

Instead of fixed small ray-marching steps, each texel stores a cone ratio or slope. At runtime, the shader uses that value to take larger steps that should not skip the first possible intersection.

## Cone Ratio Intuition

For a given texel, the cone ratio describes how quickly a safe horizontal radius grows as vertical distance from the cone tip increases.

The cone tip is conceptually placed at or near the current height-field point. At vertical distance `h` from the tip, the safe radius can be estimated as:

```text
radius = coneRatio * h
```

Some papers or implementations store the inverse slope instead:

```text
radius = h / coneRatio
```

Always verify the convention used by a paper or shader.

## What The Stored Value Is Not

The baked cone value is not simply:

- the radius at the surface;
- the radius at the top of the height field;
- a universal value with a fixed numeric range.

It is a slope/ratio that lets the shader compute a safe radius at different vertical distances.

At the cone tip, the radius is zero. As vertical distance from the tip increases, the radius grows.

## Why Ranges Are Implementation-Dependent

Typical cone values depend on:

- height scale;
- texture resolution;
- whether distances are in texel units or UV units;
- whether the texture stores slope or inverse slope;
- whether cones are conservative, relaxed, or directional.

Avoid claiming universal numeric ranges unless tied to a specific implementation.

## Conservative Versus Relaxed Cones

A conservative cone tries not to overshoot any possible surface. It is safer but may take smaller steps.

A relaxed cone allows larger steps and often performs better visually, but it may require correction/refinement and careful handling of overshoot.

## Useful Toy Exercise

Derive cone values for a tiny 1D or 2D height field by hand:

1. Pick one texel as the cone tip.
2. Compare it to neighboring height samples.
3. For each neighbor, compute horizontal distance and vertical height difference.
4. Find the slope that keeps the cone from intersecting the height field.
5. Store the limiting ratio.

This exercise helps separate "stored cone slope" from "runtime step length."
