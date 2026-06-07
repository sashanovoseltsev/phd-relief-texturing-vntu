# Dissertation Topic And Plan

Source files from Google Drive:

- `PhD/звіт_1/обгрунтування.doc`
- `PhD/звіт_1/Розгорнутий план.doc`

## Official Dissertation Topic

**Методи та програмні засоби рельєфного текстурування для систем формування тривимірних графічних зображень**

This is the official topic wording to use in repository notes, paper planning, and dissertation-related documents.

## Researcher And Program

- Researcher: Новосельцев Олександр Олександрович.
- Specialty: 121 - Інженерія програмного забезпечення.
- Educational-scientific program: Інженерія програмного забезпечення.
- Degree track: доктор філософії.
- Scientific supervisor: Романюк О. Н.
- Program guarantor mentioned in source: Коваленко О. О.

## Motivation From The Justification File

The research is motivated by the need to render highly detailed 3D surfaces without excessive geometric complexity.

Key points:

- Three-dimensional computer graphics provides the highest realism for visual representation of real-world objects and processes.
- Requirements for model complexity and accurate display of highly detailed surfaces continue to grow.
- Texturing can represent local surface features without excessively increasing model geometry.
- Relief texturing makes it possible to detail 3D model surfaces without increasing polygon count.
- Relief effects are produced by manipulating lighting, shadows, and texture sampling so that roughness, bumps, dents, and other surface irregularities appear visually present even when the actual mesh remains simple.
- High-quality relief texturing requires additional computations, especially for techniques such as Parallax Occlusion Mapping or tessellation.
- Existing texture mapping methods may produce visual artifacts due to inaccuracies when matching discrete texture space and screen space.
- Combining separate procedures, such as texture-coordinate calculation, texture filtering, color calculation, and relief mapping, may create artifacts or duplicate computations if the methods do not account for each other.

## Stated Goal

The source justification states the goal as:

> підвищення продуктивності текстурування за рахунок зменшення складності обчислень, а також реалістичності за рахунок точнішого визначення кольорів пікселів.

Practical interpretation:

- reduce computational complexity of relief texturing;
- improve rendering performance;
- improve realism through more accurate pixel color determination;
- preserve detailed surface appearance without increasing polygon count.

## Main Research Tasks

From the justification file:

1. Analyze existing texture mapping methods and tools to identify directions for improving performance and realism.
2. Develop a theoretical basis for improving performance and realism of relief texturing.
3. Propose new relief texturing methods.
4. Develop software components and a visualization system based on the proposed methods.
5. Conduct experimental studies of the developed texturing tools.

## Object And Subject

Object of research:

- the process of final visualization of three-dimensional objects in computer graphics systems.

Subject of research:

- methods and tools of relief texturing of three-dimensional graphical objects.

## Research Methods

The justification file lists:

- number theory and numerical methods;
- differential and integral calculus;
- linear algebra;
- analytic geometry for developing models and methods of relief texturing;
- computer modeling for analysis and verification of theoretical results.

For the current Unity Desktop prototype, these should be interpreted pragmatically as:

- mathematical modeling of ray-heightfield intersection;
- shader implementation and measurement;
- visual comparison against baseline methods;
- experimental validation under different viewing angles and height-map patterns.

## Proposed Dissertation Structure

From `Розгорнутий план.doc`.

### Chapter 1 - Analysis Of Relief Texturing Methods And Tools

1.1 Use of texturing inside the graphics pipeline.

1.2 Analysis of texture mapping methods.

1.3 Analysis of texturing tools.

Expected output:

- baseline taxonomy of texture mapping, filtering, and relief texturing methods;
- identification of performance and artifact problems;
- justification for focusing on relief texturing in real-time graphics.

### Chapter 2 - Mathematical Foundations For Improving Realism And Performance

2.1 Study of lighting influence on perception of depth and details in relief textures.

2.2 Development of machine-learning models for automatic generation of relief textures.

2.3 Analysis of techniques for improving speed and realism when visualizing complex textures.

Expected output:

- formal model of the problem;
- criteria for quality/performance comparison;
- possible use of precomputed or predicted data for acceleration.

### Chapter 3 - Development And Modification Of Relief Texturing Methods

3.1 Bump mapping.

3.2 Displacement mapping.

3.3 Parallax mapping.

3.4 Texturing based on physical materials.

Expected output:

- manual implementation and comparison of baseline methods;
- focus on parallax, POM, relief mapping, cone step mapping, and distance-map approaches;
- experimental modification or improvement.

### Chapter 4 - Software Tools And High-Realism Rendering System

4.1 Software implementation of texture filtering and relief texturing methods.

4.2 Shader program development.

4.3 High-realism rendering system based on relief texturing.

Expected output:

- Unity Desktop prototype;
- HLSL/ShaderLab shaders;
- test scenes and visual comparisons;
- sample count/performance measurements;
- documentation of artifacts and limitations.

## Initial Literature Mentioned In The Justification File

The justification file lists a short starting bibliography:

1. `The Surface Texture Book`, Hardcover, March 7, 2005, 256 pages.
2. `Texturing and Modeling, Second Edition: A Procedural Approach`, Morgan Kaufmann Series in Computer Graphics.
3. ISO 21920-2:2021/2022 style surface texture terminology references:
   - Geometrical Product Specifications (GPS) - Surface Texture: Profile - Part 2.
   - Geometrical Product Specifications (GPS) - Surface Texture: Areal - Part 2.
4. Романюк О. Н., Неживенко М. В., `Метод накладання текстури на поверхню тривимірного об'єкта`, Вісник Хмельницького національного університету, 2008.
5. Романюк О. Н., Чорний А. В., `Високопродуктивні методи та засоби зафарбовування тривимірних графічних об'єктів`, монографія, Вінниця.

These are broad starting references. For the actual relief-texturing research direction, use `/docs/literature-and-authors.md` as the growing bibliography index.

## Notes For Current Repository Work

- The repository should treat Unity Desktop testing as the practical implementation environment.
- The official dissertation topic should remain stable across all future notes.
- The research should prioritize relief texturing methods: parallax mapping, POM, relief mapping, cone step mapping, and distance/directional safe-step methods.
- Machine learning appears in the expanded plan, but it should be treated as optional until the classical shader methods are implemented and compared.
