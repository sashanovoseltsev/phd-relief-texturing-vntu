# Unity Shader Debugging

This project targets Unity Desktop shader experiments.

## Preferred Unity Test Scene

Use a simple scene first:

- one plane, quad, or box;
- one directional light;
- one camera that can view the surface at normal and grazing angles;
- albedo texture;
- height map;
- normal map;
- material properties for height scale and sample count.

## Common Shader Variables

```hlsl
float2 uv;
float3 viewDirWS;
float3 viewDirTS;
float3 normalWS;
float3 tangentWS;
float3 bitangentWS;
float heightScale;
int numLayers;
```

## Useful Vertex-To-Fragment Data

```hlsl
struct v2f
{
    float4 pos : SV_POSITION;
    float2 uv : TEXCOORD0;
    float3 worldPos : TEXCOORD1;
    float3 tangentWS : TEXCOORD2;
    float3 bitangentWS : TEXCOORD3;
    float3 normalWS : TEXCOORD4;
};
```

Important interpolation notes:

- Values passed from vertex to fragment are interpolated across the triangle.
- `worldPos`, `tangentWS`, `bitangentWS`, and `normalWS` can be interpolated.
- Interpolated TBN vectors may need normalization in the fragment shader.
- `SV_POSITION` is used by the rasterizer for screen position/depth and is not used like regular custom interpolated data.

## Per-Fragment View Direction

For conceptual correctness:

```hlsl
float3 viewDirWS = normalize(_WorldSpaceCameraPos - worldPos);

float3 viewDirTS = normalize(float3(
    dot(tangentWS, viewDirWS),
    dot(bitangentWS, viewDirWS),
    dot(normalWS, viewDirWS)
));
```

This uses the surface-to-camera convention. If a shader uses camera-to-surface rays, document that explicitly and adjust signs consistently.

## Debug Views

Useful temporary outputs:

- `viewDirTS * 0.5 + 0.5` to visualize tangent-space direction.
- `float3(uv, 0)` to inspect base UVs.
- `float3(parallaxUV, 0)` to inspect shifted UVs.
- grayscale height or depth value.
- number of ray-marching steps normalized to `[0, 1]`.
- intersection depth.

## Debug Checklist

When parallax looks wrong, check in this order:

1. Is the texture interpreted as height or depth?
2. Is the view direction surface-to-camera or camera-to-surface?
3. Is the UV offset sign correct?
4. Are `T`, `B`, and `N` normalized in the fragment shader?
5. Is the bitangent sign/handedness correct?
6. Are matrix rows/columns and `mul` order consistent?
7. Are all material textures sampled with the corrected UV?
8. Are UVs leaving the texture range at grazing angles?
9. Is height scale too large for the texture and mesh scale?
