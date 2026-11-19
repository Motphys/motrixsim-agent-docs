# motrixsim.write.ActuatorKpOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for kp overrides of selected position actuators.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target actuators given by names or indices, or `None` |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target actuators given by names or indices, or `None`
    for all actuators that support kp overrides.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> ActuatorKpOverride` | Create a write source for kp overrides of actuators selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> ActuatorKpOverride
```

Create a write source for kp overrides of actuators selected by names or indices.

        Args:
            selection: Actuators given by names or
                indices, or `None` for all actuators that support kp overrides (position
                actuators). The given order defines the buffer layout; names and indices must
                not be mixed and duplicates are rejected at compile time.

        Raises:
            ValueError: At compile time, if a selected actuator is not a position actuator.

        Note:
            A kp override writes both gain and stiffness. Per-instance values that are negative,
            NaN, or infinite are ignored during execution and keep the previous override.
