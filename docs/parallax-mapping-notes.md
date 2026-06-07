# Parallax Mapping Notes

Most methods in this project treat the detailed surface as a height field over a low-poly base surface.

A base polygon has UV coordinates. A height map assigns one scalar height/depth value to each texel. The shader does not actually change geometry. It changes which UV coordinate is sampled.

## Height And Depth Convention

A height map usually stores one scalar value per texel. Sometimes that value is duplicated into R, G, B, and A, but conceptually only one scalar is needed.

Common interpretations:

- `height = 1` means high/top/near the viewer.
- `height = 0` means low/deep into the surface.
- `depth = 1 - height` means larger values are deeper into the surface.

Always check and document the convention in every shader.

## Height Maps Versus Normal Maps

A normal map stores local surface normal direction. It describes local slope for lighting, but it does not by itself solve the ray-heightfield intersection problem.

A height map is directly useful for parallax/relief methods because the view ray can be marched through the height field.

## Basic Parallax Mapping

Basic parallax mapping estimates an apparent displaced UV using a single offset:

```hlsl
float height = SampleHeight(uv);
float2 offset = viewDirTS.xy / viewDirTS.z * heightScale * height;
float2 parallaxUV = uv - offset;
```

This is intentionally simplified. The sign depends on:

- whether the ray direction is surface-to-camera or camera-to-surface;
- whether the texture value is interpreted as height or depth;
- whether increasing value means closer to viewer or deeper into the surface.

The user previously found inverted direction compared with Unity URP/Lit. When debugging, check sign convention and height/depth convention before changing math.

Basic parallax is cheap but inaccurate because it assumes one local offset and does not actually search for the ray-heightfield intersection.

## Steep Parallax Mapping

Steep parallax improves basic parallax by marching along a ray through a layered height field.

Conceptual model:

- A ray enters a height-field volume in tangent space.
- The algorithm steps through depth layers from top toward bottom.
- At each step it compares current ray depth with sampled height/depth from the height map.
- When ray depth crosses the height field value, an approximate intersection is found.

Common pattern:

```hlsl
float layerDepth = 1.0 / numLayers;
float currentLayerDepth = 0.0;
float2 deltaUV = viewDirTS.xy / viewDirTS.z * heightScale / numLayers;
float2 currentUV = uv;
float currentDepthMapValue = SampleDepth(currentUV);

while (currentLayerDepth < currentDepthMapValue)
{
    currentUV -= deltaUV;
    currentLayerDepth += layerDepth;
    currentDepthMapValue = SampleDepth(currentUV);
}
```

This code is conceptual. Exact signs and comparisons depend on the shader's convention.

## Main Limitations

- Fixed steps may miss fine detail.
- More layers are needed at grazing angles.
- Layering artifacts can appear.
- Linear interpolation or binary search after crossing improves final UV precision.
