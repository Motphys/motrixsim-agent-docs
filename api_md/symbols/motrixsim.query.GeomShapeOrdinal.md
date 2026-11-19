# motrixsim.query.GeomShapeOrdinal

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the effective shape ordinals of selected geoms.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Selected geoms given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Selected geoms given by names or indices, or `None` for
    all geoms in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomShapeOrdinal` | Create a query source for effective ``Shape`` ordinals of geoms selected by names or |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomShapeOrdinal
```

Create a query source for effective ``Shape`` ordinals of geoms selected by names or
        indices (sphere 0, cylinder 1, capsule 2, cuboid 3, ellipsoid 4, infinite plane 5,
        height field 6, mesh 7, plane 8). Mesh variant selections report 7.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
