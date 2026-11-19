# motrixsim.query.GeomPosition

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the world positions of selected geoms.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomPosition` | Create a query source for world positions of geoms selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomPosition
```

Create a query source for world positions of geoms selected by names or indices.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
