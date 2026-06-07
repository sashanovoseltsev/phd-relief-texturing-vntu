# Experimental RGBA Directional Distance Idea

The recurring research intuition:

> A normal height map stores only one scalar in one channel, leaving other channels unused or duplicated. Maybe extra channels can store more useful distance or directional information.

## Possible Hypothesis

Store distance or safe-step information for several predefined tangent-space view directions in a 2D texture.

Example channel assignment:

- `R`: base height/depth or straight/normal-direction distance.
- `G`: safe-step distance for one oblique tangent-space direction.
- `B`: safe-step distance for another oblique tangent-space direction.
- `A`: safe-step distance for a third oblique tangent-space direction.

At runtime, interpolate or select among these stored values based on the actual tangent-space view direction.

## Potential Research Value

- Could reduce runtime ray-marching steps.
- Could approximate a compact directional distance field in a 2D texture.
- Could be compared against Cone Step Mapping, Relaxed Cone Stepping, Distance Mapping, and POM.
- Could be a practical PhD experiment if scoped carefully.

## Main Risks

- Directional values may be hard to interpolate accurately.
- Conservative safety is difficult; a safe step must not overshoot the first intersection.
- View directions between stored directions may fail.
- Memory cost increases if extra textures or channels are needed.
- Preprocessing complexity may become the main cost.

## Useful Evaluation Questions

- Does the method reduce average samples compared with POM at similar visual quality?
- Does it remain stable at grazing angles?
- Does it produce fewer overshoots than relaxed cone stepping?
- How much extra memory does it require?
- Can the baked values be explained geometrically and reproduced on a small toy height field?

## Suggested Baselines

Compare against:

- basic parallax mapping;
- POM with fixed layers;
- POM with view-angle-dependent layers;
- relief mapping with binary refinement;
- cone step mapping;
- relaxed cone stepping if implemented.

Do not dismiss this idea. Treat it as a research hypothesis to formalize, test, and compare against existing methods.
