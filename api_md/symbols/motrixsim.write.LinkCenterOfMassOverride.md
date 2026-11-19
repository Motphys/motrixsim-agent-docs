# motrixsim.write.LinkCenterOfMassOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for center-of-mass overrides of selected links.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target links given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target links given by names or indices, or `None` for
    all links that support mass-property overrides.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> LinkCenterOfMassOverride` | Create a write source for center-of-mass overrides of links selected by names or |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> LinkCenterOfMassOverride
```

Create a write source for center-of-mass overrides of links selected by names or
        indices.

        Args:
            selection: Links given by names or
                indices, or `None` for all links that support mass-property overrides (neither
                mocap nor world-fixed). The given order defines the buffer layout; names and
                indices must not be mixed and duplicates are rejected at compile time.

        Raises:
            ValueError: At compile time, if a selected link is a mocap or fixed to the world.

        Note:
            The center of mass is expressed in the link local frame. Per-instance values with
            non-finite components are ignored during execution and keep the previous override.
