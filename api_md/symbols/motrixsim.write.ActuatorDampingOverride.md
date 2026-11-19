# motrixsim.write.ActuatorDampingOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for damping overrides of selected actuators.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target actuators given by names or indices, or `None` |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target actuators given by names or indices, or `None`
    for all actuators that support damping overrides.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> ActuatorDampingOverride` | Create a write source for damping overrides of actuators selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> ActuatorDampingOverride
```

Create a write source for damping overrides of actuators selected by names or indices.

        Args:
            selection: Actuators given by names or
                indices, or `None` for all actuators that support damping overrides (position
                and general actuators). The given order defines the buffer layout; names and
                indices must not be mixed and duplicates are rejected at compile time.

        Raises:
            ValueError: At compile time, if a selected actuator type does not support damping
                overrides (only position and general actuators do).

        Note:
            Per-instance values that are negative, NaN, or infinite are ignored during execution
            and keep the previous override.
