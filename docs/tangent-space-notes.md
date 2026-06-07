# Tangent Space Notes

Tangent space is the most important coordinate system for parallax, POM, relief mapping, and cone step mapping.

For one point on a surface:

- Object space coordinates are relative to the model object.
- World space coordinates are after the object transform.
- Tangent space is a local coordinate frame attached to the surface point.

## TBN Basis

The tangent-space basis is usually:

- `T`: tangent direction, often aligned with increasing texture `u`.
- `B`: bitangent direction, often aligned with increasing texture `v`.
- `N`: normal direction, perpendicular to the base surface.

A vector expressed in tangent space tells how much it points along `T`, `B`, and `N`.

## Dot Product Intuition

For a world-space vector `V`:

- `dot(T, V)` gives the coordinate/projection of `V` along the tangent direction.
- `dot(B, V)` gives the coordinate/projection of `V` along the bitangent direction.
- `dot(N, V)` gives the coordinate/projection of `V` along the normal direction.

So converting a world-space vector into tangent-space coordinates can be written clearly as:

```hlsl
float3 tangentV = float3(
    dot(tangentWS, V),
    dot(bitangentWS, V),
    dot(normalWS, V)
);
```

This form is usually best for explanation because every component has a direct geometric meaning.

## Matrix Convention Caution

The user often asks why `mul(float3x3(T, B, N), V)` can give a tangent-space direction.

Start from the dot products. If matrix rows are `T`, `B`, and `N`, then multiplying matrix by vector gives:

```text
[ dot(T, V), dot(B, V), dot(N, V) ]
```

That is exactly the coordinates of `V` in the tangent basis, assuming the basis is orthonormal.

If the basis vectors are columns instead, the multiplication order must change. In Unity/HLSL, be explicit about how the matrix is constructed and whether code uses `mul(matrix, vector)` or `mul(vector, matrix)`.

## View Direction In Tangent Space

For parallax methods, the key vector is the view direction expressed in tangent space.

Typical conceptual flow:

1. Compute world position of the current fragment.
2. Compute world-space view direction from surface point toward camera.
3. Transform that view direction into tangent space using TBN.
4. Use `viewDirTS.xy / viewDirTS.z` to estimate how much UV shifts for a given height/depth change.

Important intuition:

- `viewDirTS.xy` tells how much the ray moves sideways across the texture.
- `viewDirTS.z` tells how much the ray moves through the height/depth axis.
- `viewDirTS.xy / viewDirTS.z` tells horizontal UV movement per one unit of vertical movement.

At grazing angles, `viewDirTS.z` becomes smaller, so the ratio becomes larger. Parallax displacement becomes stronger and ray marching usually needs more samples.

## Unity Fragment-Side Conversion

For conceptual correctness in experiments:

```hlsl
float3 viewDirWS = normalize(_WorldSpaceCameraPos - worldPos);

float3 viewDirTS = normalize(float3(
    dot(tangentWS, viewDirWS),
    dot(bitangentWS, viewDirWS),
    dot(normalWS, viewDirWS)
));
```

Normalize interpolated `tangentWS`, `bitangentWS`, and `normalWS` in the fragment shader before using them.
