# motrixsim.GeomCuboid

Module: [`motrixsim`](../modules/motrixsim.md)

Cuboid (box) geometry.

    A box shape defined by half-extents in each axis direction.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `half_extents` | `numpy.typing.NDArray[numpy.float32]` | The half-extents of the cuboid. |

### half_extents

```python
half_extents: numpy.typing.NDArray[numpy.float32]
```

The half-extents of the cuboid.

    Returns:
        NDArray[float]: A numpy array of shape `(3,)` with `[half_x, half_y, half_z]`.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_size_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective size override for this cuboid. |
| `set_size_override` | `(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the size of this cuboid. |

### get_size_override

```python
def get_size_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective size override for this cuboid.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 3)``. The effective
                ``[half_x, half_y, half_z]``.

### set_size_override

```python
def set_size_override(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the size of this cuboid.

        Args:
            data: The scene data to modify.
            size: The new half-extents ``[half_x, half_y, half_z]``.
                - Shape ``(3,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 3)``: Per-batch values.

        Note:
            If any component is non-positive, NaN, or infinite, the override is silently ignored.
