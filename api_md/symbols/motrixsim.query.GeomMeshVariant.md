# motrixsim.query.GeomMeshVariant

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the effective mesh variant ordinals of selected geoms.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomMeshVariant` | Create a query source for effective mesh variant ordinals of geoms selected by names |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomMeshVariant
```

Create a query source for effective mesh variant ordinals of geoms selected by names
        or indices: the variant set-local ordinal for mesh selections and the ``-1`` sentinel
        for everything else.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
