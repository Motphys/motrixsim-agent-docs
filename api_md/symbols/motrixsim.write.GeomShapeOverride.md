# motrixsim.write.GeomShapeOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for shape overrides of geoms selected by names or indices.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target geoms given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target geoms given by names or indices, or `None` for
    all geoms in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomShapeOverride` | Create a write source for shape overrides of geoms selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomShapeOverride
```

Create a write source for shape overrides of geoms selected by names or indices.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order defines the
                buffer layout; names and indices must not be mixed and duplicates are rejected
                at compile time.

        Note:
            Each row is ``[shape_ordinal, variant, size0, size1, size2]``: the ``Shape``
            ordinal (sphere 0, cylinder 1, capsule 2, cuboid 3, ellipsoid 4, mesh 7), the mesh
            variant set-local ordinal used by mesh rows (``-1`` on primitive rows), and the
            primitive size applied atomically with the switch (ignored by mesh rows; component
            semantics follow the selected primitive). This is the plan-level joint form: a
            shape switch never depends on a separate size field's application order, and cannot
            be silently rejected for carrying an invalid size. Per-instance rows that are
            invalid for the geom (unsupported ordinals, mesh rows without a valid variant,
            non-switchable geoms selecting a non-mesh shape, primitive sizes that remain
            invalid for the selected shape) are ignored during execution and keep the previous
            selection.
