# motrixsim.GeomSphere

Module: [`motrixsim`](../modules/motrixsim.md)

Sphere geometry.

    A spherical shape defined by a single radius parameter.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `radius` | `float` | The radius of the sphere. |

### radius

```python
radius: float
```

The radius of the sphere.

    Returns:
        float: The sphere radius.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_size_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective size override for this sphere. |
| `set_size_override` | `(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the size of this sphere. |

### get_size_override

```python
def get_size_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective size override for this sphere.

        Returns the overridden radius if a size override has been set,
        otherwise returns the model's original radius.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 1)``. The effective ``[radius]``.

### set_size_override

```python
def set_size_override(self, data: SceneData, size: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the size of this sphere.

        Args:
            data: The scene data to modify.
            size: The new size ``[radius]``.
                - Shape ``(1,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 1)``: Per-batch values.

        Note:
            If the radius is non-positive, NaN, or infinite, the override is silently ignored.
