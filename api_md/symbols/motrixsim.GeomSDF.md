# motrixsim.GeomSDF

Module: [`motrixsim`](../modules/motrixsim.md)

SDF geometry.

    A geometry defined by a triangle mesh asset that is compiled into an SDF octree for collision.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `mesh_name` | `Optional[str]` | The name of the referenced mesh asset. |
| `mesh_scale` | `Optional[numpy.typing.NDArray[numpy.float32]]` | The scale applied to the source mesh before SDF compilation. |

### mesh_name

```python
mesh_name: Optional[str]
```

The name of the referenced mesh asset.

    Returns:
        Optional[str]: The mesh asset name, or ``None`` if not set.

### mesh_scale

```python
mesh_scale: Optional[numpy.typing.NDArray[numpy.float32]]
```

The scale applied to the source mesh before SDF compilation.

    Returns:
        Optional[NDArray[float]]: A numpy array of shape `(3,)` with `[sx, sy, sz]`,
            or ``None`` if no scaling is applied.
