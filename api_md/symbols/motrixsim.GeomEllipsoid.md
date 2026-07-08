# motrixsim.GeomEllipsoid

Module: [`motrixsim`](../modules/motrixsim.md)

Ellipsoid geometry.

    An ellipsoidal shape defined by semi-axis lengths in each direction.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `half_extents` | `numpy.typing.NDArray[numpy.float32]` | The half-extents (semi-axis lengths) of the ellipsoid. |

### half_extents

```python
half_extents: numpy.typing.NDArray[numpy.float32]
```

The half-extents (semi-axis lengths) of the ellipsoid.

    Returns:
        NDArray[float]: A numpy array of shape `(3,)` with `[semi_x, semi_y, semi_z]`.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_size_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective size override for this ellipsoid. |
| `set_size_override` | `(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the size of this ellipsoid. |

### get_size_override

```python
def get_size_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective size override for this ellipsoid.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 3)``. The effective semi-axis lengths
                ``[semi_x, semi_y, semi_z]``.

### set_size_override

```python
def set_size_override(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the size of this ellipsoid.

        Args:
            data: The scene data to modify.
            size: The new semi-axis lengths ``[semi_x, semi_y, semi_z]``.
                - Shape ``(3,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 3)``: Per-batch values.

        Note:
            If any component is non-positive, NaN, or infinite, the override is silently ignored.
