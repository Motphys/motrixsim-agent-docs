# motrixsim.write.GeomSizeOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for size overrides of geoms selected by names or indices.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomSizeOverride` | Create a write source for size overrides of geoms selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomSizeOverride
```

Create a write source for size overrides of geoms selected by names or indices.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order defines the
                buffer layout; names and indices must not be mixed and duplicates are rejected
                at compile time.

        Note:
            Each row is ``[component0, component1, component2]``, interpreted by the instance's
            effective primitive selection. Per-instance values that are invalid for the effective
            selection (mesh/fixed selections, non-positive or non-finite required components) are
            ignored during execution and keep the previous override.
