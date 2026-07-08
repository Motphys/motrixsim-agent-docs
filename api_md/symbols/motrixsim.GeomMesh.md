# motrixsim.GeomMesh

Module: [`motrixsim`](../modules/motrixsim.md)

Mesh geometry.

    A geometry defined by a triangle mesh asset. The mesh can optionally be scaled.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `mesh_name` | `Optional[str]` | The name of the referenced mesh asset. |
| `mesh_scale` | `Optional[numpy.typing.NDArray[numpy.float32]]` | The scale applied to the mesh. |

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

The scale applied to the mesh.

    Returns:
        Optional[NDArray[float]]: A numpy array of shape `(3,)` with `[sx, sy, sz]`,
            or ``None`` if no scaling is applied.
