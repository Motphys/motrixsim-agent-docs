# motrixsim.query.GeomQuatOverride

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the effective local rotations of selected geoms.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomQuatOverride` | Create a query source for effective local rotations of geoms selected by names or |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomQuatOverride
```

Create a query source for effective local rotations of geoms selected by names or
        indices, in ``[i, j, k, w]`` order. Reports the pose override when present, otherwise
        the authored orientation.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
