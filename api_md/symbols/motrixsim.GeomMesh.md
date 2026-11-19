# motrixsim.GeomMesh

Module: [`motrixsim`](../modules/motrixsim.md)

Mesh geometry.

    A geometry defined by a triangle mesh asset. The mesh can optionally be scaled.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `mesh_name` | `Optional[str]` | The name of the referenced mesh asset. |
| `mesh_scale` | `Optional[numpy.typing.NDArray[numpy.float32]]` | The authored diagonal scale applied to the mesh. |
| `mesh_transform` | `Optional[numpy.typing.NDArray[numpy.float32]]` | The complete linear transform applied to mesh-local coordinates. |

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

The authored diagonal scale applied to the mesh.

    Returns:
        Optional[NDArray[float]]: A numpy array of shape `(3,)` with `[sx, sy, sz]`,
            or ``None`` when the geometry has no authored transform or uses a
            general ``Linear`` transform.  A ``Linear`` transform is intentionally
            not reduced to a scale vector.

### mesh_transform

```python
mesh_transform: Optional[numpy.typing.NDArray[numpy.float32]]
```

The complete linear transform applied to mesh-local coordinates.

    Returns:
        Optional[NDArray[float]]: A numpy array of shape ``(3, 3)`` mapping
            mesh-local coordinates into the geometry-local frame.  Axis-aligned
            scales are returned as a diagonal matrix; oriented scales and other
            linear transforms retain all off-diagonal terms.  ``None`` means no
            transform is stored; both ``None`` and an explicit identity matrix have
            identity semantics.
