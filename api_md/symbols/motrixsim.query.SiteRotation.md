# motrixsim.query.SiteRotation

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for world rotations of selected sites.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Selected sites, or `None` for all sites in model order. |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Selected sites, or `None` for all sites in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> SiteRotation` | Create a query source for world rotations of selected sites as quaternions. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> SiteRotation
```

Create a query source for world rotations of selected sites as quaternions.

        Args:
            selection: Sites given by names or
                indices, or `None` for all sites. Order and duplicates are preserved.
