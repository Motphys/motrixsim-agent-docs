# motrixsim.write.LinkMassOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for mass overrides of selected links.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target links given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target links given by names or indices, or `None` for
    all links that support mass overrides.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> LinkMassOverride` | Create a write source for mass overrides of links selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> LinkMassOverride
```

Create a write source for mass overrides of links selected by names or indices.

        Args:
            selection: Links given by names or
                indices, or `None` for all links that support mass overrides (neither mocap nor
                world-fixed). The given order defines the buffer layout; names and indices must
                not be mixed and duplicates are rejected at compile time.

        Raises:
            ValueError: At compile time, if a selected link is a mocap or fixed to the world.

        Note:
            A mass override does not scale the inertia tensor about the center of mass.
            Per-instance values that are non-positive, NaN, or infinite are ignored during
            execution and keep the previous override.
