# motrixsim.query.JointVelocity

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for velocities of selected single-DoF joints.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `list[Any]` | list[str] \| list[int]: Selected joints given by names or indices. |

### selection

```python
selection: list[Any]
```

list[str] | list[int]: Selected joints given by names or indices.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Any) -> JointVelocity` | Create a query source for velocities of selected single-DoF joints. |

### __new__

```python
def __new__(cls, selection: Any) -> JointVelocity
```

Create a query source for velocities of selected single-DoF joints.

        Args:
            selection: Joints given by names or indices.
                The given order is preserved and duplicates are allowed; names and indices must not
                be mixed. Every selected joint must have exactly one position and velocity DoF.
