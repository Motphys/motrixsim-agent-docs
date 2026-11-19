# motrixsim.query.LinkAngularVelocity

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the world angular velocities of selected links.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Selected links given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Selected links given by names or indices, or `None` for
    all links in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> LinkAngularVelocity` | Create a query source for world angular velocities of links selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> LinkAngularVelocity
```

Create a query source for world angular velocities of links selected by names or indices.

        Args:
            selection: Links given by names or
                indices, or `None` for all links in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
