# motrixsim.write.GeomActiveOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the active flags of geoms selected by names or indices.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomActiveOverride` | Create a write source for the active flags of geoms selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomActiveOverride
```

Create a write source for the active flags of geoms selected by names or indices.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order defines the
                buffer layout; names and indices must not be mixed and duplicates are rejected
                at compile time.

        Note:
            Each row holds one flag; values ``> 0.5`` activate the geom for the instance and
            everything else deactivates it (no collision, ray hit, or rendering). The flag
            applies to every geom, including non-switchable shapes, and keeps the recorded
            shape/size/pose for re-enable.
