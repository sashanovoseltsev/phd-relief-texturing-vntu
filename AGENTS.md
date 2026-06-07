# AGENTS.md - PhD Relief Texturing Project Context

This repository is the working context for a PhD research project in Computer Graphics, focused on relief texturing methods for detailed 3D surface appearance without increasing polygon count.

`AGENTS.md` is the short operating guide for Codex/AI agents. The detailed research notes live in `/docs`.

## User profile

The user is a beginner PhD student studying Computer Graphics, with a practical software engineering background and experience with Blender, Unity, React/TypeScript, and .NET/C#.

The user is currently concentrating on Unity Desktop shader experiments.

Official dissertation topic:

> Методи та програмні засоби рельєфного текстурування для систем формування тривимірних графічних зображень

The user wants deep intuition, not just final formulas. Prefer:

- geometry first, equations second, code third;
- step-by-step reasoning;
- tangent-space mental models;
- small numeric examples;
- explicit coordinate-space explanations;
- practical Unity/HLSL implementation guidance.

Avoid:

- overly abstract math without geometric interpretation;
- opaque optimized shader snippets before the simple version is clear;
- assuming the user already understands tangent space, TBN matrix conventions, or Unity shader coordinate conventions.

## Research direction

High-level research idea:

> Detailed relief texturing of 3D surfaces without increasing polygon count, possibly by improving or combining existing view-dependent height-field intersection methods.

Main interests:

- parallax mapping, steep parallax mapping, POM, relief mapping, cone step mapping, and distance mapping;
- efficient ray-heightfield intersection in texture/tangent space;
- reducing runtime shader work while preserving convincing depth;
- using precomputed/baked texture data to accelerate ray marching;
- exploring whether unused RGBA channels can store additional directional safe-step or distance information;
- comparing visual quality, correctness, artifacts, and performance in Unity Desktop.

## Repository layout

Use these files as the main research memory:

- `/docs/phd-research-context.md` - project scope, method comparison, terminology, and literature framing.
- `/docs/dissertation-topic-and-plan.md` - official dissertation topic, justification, goal, tasks, object/subject, and expanded plan from `PhD/звіт_1`.
- `/docs/literature-and-authors.md` - extracted bibliography and author notes from Dudnyk's dissertation.
- `/docs/latex-formatting-rules.md` - LaTeX formatting rules for Ukrainian university assignments, dissertation-oriented drafts, formulas, and APA-style references.
- `/docs/tangent-space-notes.md` - object/world/tangent space, TBN, dot products, and matrix conventions.
- `/docs/parallax-mapping-notes.md` - height/depth convention, basic parallax, and steep parallax.
- `/docs/pom-notes.md` - Parallax Occlusion Mapping algorithm and implementation notes.
- `/docs/relief-mapping-notes.md` - coarse search plus binary refinement.
- `/docs/cone-step-mapping-notes.md` - cone ratios, safe stepping, and preprocessing intuition.
- `/docs/experimental-rgba-directional-distance.md` - research hypothesis for packing extra directional information into RGBA channels.
- `/docs/unity-shader-debugging.md` - Unity Desktop shader conventions and debugging checklist.
- `/unity/scene-notes.md` - Unity test-scene notes.
- `/shaders` - Unity ShaderLab/HLSL prototypes.
- `/templates/latex/ukrainian-university-assignment-template.tex` - reusable LaTeX template for Ukrainian university assignments.

The user mentioned `/shader`, but the existing project folder is `/shaders`; use `/shaders` unless explicitly asked to rename it.

## Current practical environment

The user is working on macOS with an Apple Silicon MacBook Pro M2.

Important tools:

- Unity Desktop for 3D shader experiments.
- HLSL/ShaderLab/Unity shaders.
- Blender for modeling and texture preparation.
- VS Code for editing.

Current Unity prototype direction:

- simple test scene with a plane, quad, or box;
- albedo/color texture;
- height map;
- normal map;
- manual shader implementations of basic parallax, POM, relief mapping, and cone step mapping;
- desktop visual/performance comparison at different view angles.

## Codex behavior instructions

When acting as Codex in this repository:

1. Read this file first, then open the relevant `/docs` topic file before making substantial suggestions.
2. Preserve the research-oriented nature of the project.
3. Prefer educational, understandable shader code over opaque optimized snippets.
4. Keep Unity/HLSL examples small and testable.
5. When implementing a shader method, include concise comments explaining the geometry.
6. Be explicit about coordinate spaces.
7. Be explicit about height/depth convention and sign convention.
8. Avoid silently changing conventions across files.
9. If creating experimental code, document assumptions in comments.
10. If discussing performance, identify the trade-off in texture samples, ALU, memory, preprocessing, and view-angle behavior.

## Important recurring debugging points

The user has previously run into:

- parallax direction inverted relative to Unity URP/Lit;
- confusion about whether a texture stores height or depth;
- confusion about whether `T`, `B`, `N` in a matrix are rows or columns;
- confusion about why dot products give tangent-space coordinates;
- confusion about why `viewDir.xy / viewDir.z` appears in parallax formulas;
- confusion about how a 2D height map can represent deep relief;
- confusion about 3D texture representation for distance fields.

When helping, build from simple 2D diagrams or numeric examples, then connect the idea to shader code.

## Current next useful tasks

1. Create a minimal Unity shader that computes tangent-space view direction per fragment and visualizes it as color.
2. Implement basic parallax mapping with a clear height/depth convention.
3. Implement POM with layer stepping and linear interpolation after intersection.
4. Build debug visualizations for sampled UV path and ray depth.
5. Implement relief mapping with coarse search plus binary search.
6. Study cone step mapping preprocessing and derive cone ratio from a small 2D toy height field.
7. Experiment with packing additional directional safe-distance information into RGBA channels.
8. Compare sample counts and visual artifacts at different view angles.

## Communication preference

The user is comfortable with English technical terms but may ask in Ukrainian, Russian, or English.

For difficult math/graphics topics, respond in the language of the user's question unless there is a clear reason to use English terms.

The user values clarity, intuition, and practical implementation guidance.
