# motrixsim.query.SitePosition

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for world positions of selected sites.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> SitePosition` | Create a query source for world positions of selected sites. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> SitePosition
```

Create a query source for world positions of selected sites.

        Args:
            selection: Sites given by names or
                indices, or `None` for all sites. Order and duplicates are preserved.
