# Unity Scene Notes

Use Unity Desktop as the practical test platform.

## Initial Scene

Recommended starting setup:

- one plane or quad with dense enough UVs for texture inspection;
- one box or curved mesh later for tangent-space validation;
- albedo, normal, and height textures assigned to one material;
- camera controls that allow normal and grazing view angles;
- a fixed directional light for repeatable screenshots.

## First Milestones

1. Visualize tangent-space view direction as color.
2. Implement basic parallax mapping.
3. Implement POM with linear interpolation.
4. Implement relief mapping with binary refinement.
5. Add debug outputs for UV path, layer depth, and sample count.
6. Compare methods from the same camera angles.

## Notes To Record

For each experiment, record:

- shader name and version;
- height/depth convention;
- sign convention;
- height scale;
- number of samples or maximum samples;
- camera angle;
- visible artifacts;
- approximate performance observations.
