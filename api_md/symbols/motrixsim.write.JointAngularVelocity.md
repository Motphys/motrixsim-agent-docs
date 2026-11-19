# motrixsim.write.JointAngularVelocity

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the local angular velocities of selected ball joints.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target joints given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target joints given by names or indices, or `None` for
    all ball joints in joint model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> JointAngularVelocity` | Create a write source for local angular velocities of ball joints selected by names or |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> JointAngularVelocity
```

Create a write source for local angular velocities of ball joints selected by names or
        indices.

        Args:
            selection: Joints given by names or
                indices, or `None` for all ball joints in joint model order. The given order
                defines the buffer layout; names and indices must not be mixed and duplicates
                are rejected at compile time. Indices address the joint model order.

        Raises:
            ValueError: At compile time, if a selected joint is not a ball joint.

        Note:
            Angular velocities are expressed in the joint-local reference frame and stored
            directly as the joint's velocity DoF values.
