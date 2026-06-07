# Unity Shader Prototypes

This folder is for Unity ShaderLab/HLSL prototypes used in the relief-texturing research.

Suggested files:

- `ViewDirectionTangentDebug.shader`
- `BasicParallax.shader`
- `ParallaxOcclusionMapping.shader`
- `ReliefMapping.shader`
- `ConeStepMapping.shader`

## Conventions

Every shader should document:

- whether the texture stores height or depth;
- whether the view ray is surface-to-camera or camera-to-surface;
- the UV offset sign convention;
- which texture channels are used;
- sample count and view-angle behavior;
- whether all material textures use the corrected UV.

Prefer clarity over heavy optimization while the math is being studied.
