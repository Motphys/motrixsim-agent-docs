# motrixsim.write.ActuatorCtrls

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for actuator control values.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target actuators given by names or indices, or `None` |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target actuators given by names or indices, or `None`
    for all actuators in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> ActuatorCtrls` | Create a write source for actuator control values selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> ActuatorCtrls
```

Create a write source for actuator control values selected by names or indices.

        Args:
            selection: Actuators given by names or
                indices, or `None` for all actuators in model order. The given order defines the
                buffer layout; names and indices must not be mixed and duplicates are rejected
                at compile time.
