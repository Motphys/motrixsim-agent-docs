# motrixsim.query.SensorValues

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for sensor values.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Selected sensors given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Selected sensors given by names or indices, or `None` for
    all sensors in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> SensorValues` | Create a query source for sensor values selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> SensorValues
```

Create a query source for sensor values selected by names or indices.

        Args:
            selection: Sensors given by names or
                indices, or `None` for all sensors in model order. The given order is preserved
                and duplicates are allowed; names and indices must not be mixed.
