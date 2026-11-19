# motrixsim.query.ActuatorControls

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for actuator control values.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Selected actuator controls given by names or indices, or |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Selected actuator controls given by names or indices, or
    `None` for all actuator controls in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> ActuatorControls` | Create a query source for actuator control values selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> ActuatorControls
```

Create a query source for actuator control values selected by names or indices.

        Args:
            selection: Actuators given by names or
                indices, or `None` for all actuator controls in model order. The given order is
        preserved         and duplicates are allowed; names and indices must not be mixed.
