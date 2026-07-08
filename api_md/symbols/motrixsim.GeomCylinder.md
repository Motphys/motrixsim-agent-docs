# motrixsim.GeomCylinder

Module: [`motrixsim`](../modules/motrixsim.md)

Cylinder geometry.

    A cylindrical shape defined by a radius and half-height.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `half_height` | `float` | The half-height of the cylinder. |
| `radius` | `float` | The radius of the cylinder. |

### half_height

```python
half_height: float
```

The half-height of the cylinder.

    Returns:
        float: The cylinder half-height.

### radius

```python
radius: float
```

The radius of the cylinder.

    Returns:
        float: The cylinder radius.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_size_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective size override for this cylinder. |
| `set_size_override` | `(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the size of this cylinder. |

### get_size_override

```python
def get_size_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective size override for this cylinder.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 2)``. The effective ``[radius, half_height]``.

### set_size_override

```python
def set_size_override(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the size of this cylinder.

        Args:
            data: The scene data to modify.
            size: The new size ``[radius, half_height]``.
                - Shape ``(2,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 2)``: Per-batch values.

        Note:
            If any component is non-positive, NaN, or infinite, the override is silently ignored.
