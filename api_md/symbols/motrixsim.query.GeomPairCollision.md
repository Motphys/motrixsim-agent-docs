# motrixsim.query.GeomPairCollision

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source indicating whether selected geom pairs are colliding.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `pairs` | `list[tuple[Any, Any]]` | list[tuple[str, str]] \| list[tuple[int, int]]: Selected geom pairs. |

### pairs

```python
pairs: list[tuple[Any, Any]]
```

list[tuple[str, str]] | list[tuple[int, int]]: Selected geom pairs.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, pairs: Any) -> GeomPairCollision` | Create a query source for collision state of selected geom pairs. |

### __new__

```python
def __new__(cls, pairs: Any) -> GeomPairCollision
```

Create a query source for collision state of selected geom pairs.

        Args:
            pairs: Geom pairs. Pair order and
                duplicates are preserved. Both endpoints within a pair must use the same type.
