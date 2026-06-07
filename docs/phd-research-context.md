# PhD Research Context

This repository supports a PhD research project in Computer Graphics focused on detailed visual representation of 3D surfaces without increasing polygon count.

The central practical idea is to treat a flat or low-poly surface as a base layer and use a height field in texture space to fake depth. The shader does not usually move geometry. Instead, it changes which UV coordinate is sampled, so color and normal information appear to come from a displaced point.

## Official Dissertation Topic

**Методи та програмні засоби рельєфного текстурування для систем формування тривимірних графічних зображень**

Use this exact wording as the official dissertation topic.

## Main Research Question

How can relief-texturing methods improve apparent surface detail while keeping runtime cost low enough for interactive Unity Desktop rendering?

The likely route is:

1. Implement known methods manually.
2. Compare visual quality, correctness, artifacts, and performance.
3. Identify weaknesses, especially at grazing view angles.
4. Explore a small improvement based on baked data or directional approximations.
5. Evaluate that idea against established baselines.

## Methods Of Interest

| Method | Runtime samples | Precomputation | Accuracy | Memory cost | Main artifact/risk |
| --- | ---: | ---: | ---: | ---: | --- |
| Basic Parallax Mapping | Very low | None | Low | Low | Sliding, stretching, wrong intersections |
| Steep Parallax Mapping | Medium/high | None | Medium | Low | Layering artifacts, missed detail |
| POM | Medium/high | None | Medium/high | Low | Cost rises at grazing angles |
| Relief Mapping | Medium/high | None | High after refinement | Low | Binary search depends on initial bracket |
| Distance Mapping | Lower runtime steps | High | High if distance field is good | High | Memory-heavy, complex preprocessing |
| Cone Step Mapping | Lower runtime steps | Medium/high | Good if conservative | Medium | Overshoot if cone data is not conservative |
| Relaxed Cone Stepping | Lower runtime steps | Medium/high | Often better/faster | Medium | Needs careful correction/refinement |

## Literature Framing

When summarizing or studying papers, explain:

- the problem the paper solves;
- the core algorithm in plain language;
- the geometric meaning of the math;
- what is precomputed and what happens at runtime;
- limitations and artifacts;
- how it could fit into this PhD project.

Relevant families:

- Parallax Occlusion Mapping for detailed surface rendering.
- Relief Mapping.
- Cone Step Mapping and Relaxed Cone Stepping.
- Donnelly distance mapping and distance fields.
- Related real-time height-field intersection methods.

Use `/docs/literature-and-authors.md` as the local bibliography index. It starts with the literature extracted from Oleksandr Dudnyk's 2018 dissertation and is intended to grow with new computer graphics, parallax mapping, and relief texturing papers.

## Important Terminology

- Height field: scalar relief surface over UV coordinates.
- Ray-heightfield intersection: finding where the view ray first hits the height field.
- Tangent space: local surface coordinate system defined by tangent, bitangent, and normal.
- TBN: tangent-bitangent-normal basis.
- View direction: vector from surface point to camera, or camera to surface depending on convention.
- Height: value representing how high a point is above the base plane.
- Depth: often `1 - height`, representing how far into the surface the ray has traveled.
- Parallax offset: UV shift caused by view-dependent apparent displacement.
- Coarse stepping: large approximate ray marching steps.
- Binary search refinement: repeatedly narrowing the interval around an intersection.
- Cone ratio/slope: precomputed value describing safe cone growth around a texel.
- Safe step: ray advancement intended not to skip the first possible intersection.

## Working Assumption

The practical target is Unity Desktop shader testing.
