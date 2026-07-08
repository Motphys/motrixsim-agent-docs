# motrixsim.GeomCapsule

Module: [`motrixsim`](../modules/motrixsim.md)

Capsule geometry.

    A capsule shape defined by a radius and half-height. The total height of the
    capsule is ``2 * half_height + 2 * radius``.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `half_height` | `float` | The half-height of the cylindrical part of the capsule. |
| `radius` | `float` | The radius of the capsule. |

### half_height

```python
half_height: float
```

The half-height of the cylindrical part of the capsule.

    Returns:
        float: The half-height of the capsule cylinder.

### radius

```python
radius: float
```

The radius of the capsule.

    Returns:
        float: The capsule radius.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_size_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective size override for this capsule. |
| `set_size_override` | `(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the size of this capsule. |

### get_size_override

```python
def get_size_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective size override for this capsule.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 2)``. The effective ``[radius, half_height]``.

### set_size_override

```python
def set_size_override(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the size of this capsule.

        Args:
            data: The scene data to modify.
            size: The new size ``[radius, half_height]``.
                - Shape ``(2,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 2)``: Per-batch values.

        Note:
            If any component is non-positive, NaN, or infinite, the override is silently ignored.
