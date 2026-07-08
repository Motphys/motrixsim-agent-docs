# motrixsim.GeomHField

Module: [`motrixsim`](../modules/motrixsim.md)

Height field geometry.

    A geometry defined by a height field asset, used for terrain and elevation data.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `hfield` | `Optional[HField]` | The height field associated with this geom. |

### hfield

```python
hfield: Optional[HField]
```

The height field associated with this geom.

    Returns:
        Optional[HField]: The HField object if this geom has an associated
            height field, otherwise ``None``.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `sample_height` | `(self, data: SceneData, xy: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Sample the terrain surface height at world-space XY coordinates. |

### sample_height

```python
def sample_height(self, data: SceneData, xy: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Sample the terrain surface height at world-space XY coordinates.

        Transforms the given world XY points into the height field's local frame,
        performs bilinear interpolation on the grid, and returns the world-space Z
        height for each query point.

        Args:
            data: The scene data (provides current geom world pose).
            xy: World-space XY coordinates.
                - Shape ``(N, 2)``: ``N`` query points shared across all batches.
                - Shape ``(*data.shape, N, 2)``: per-batch query points.
            out: Pre-allocated output array of shape
                ``(*data.shape, N)``. When provided the result is written into this
                array and returned directly, avoiding an internal allocation.

        Returns:
            NDArray[float]: World-space surface heights.
                Shape ``(*data.shape, N)``.

        Note:
            Points that fall outside the height field boundary are clamped to the
            nearest edge cell.
