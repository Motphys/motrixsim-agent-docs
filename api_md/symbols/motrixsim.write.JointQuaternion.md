# motrixsim.write.JointQuaternion

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the local orientation quaternions of selected ball joints.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> JointQuaternion` | Create a write source for local orientation quaternions of ball joints selected by |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> JointQuaternion
```

Create a write source for local orientation quaternions of ball joints selected by
        names or indices.

        Args:
            selection: Joints given by names or
                indices, or `None` for all ball joints in joint model order. The given order
                defines the buffer layout; names and indices must not be mixed and duplicates
                are rejected at compile time. Indices address the joint model order.

        Raises:
            ValueError: At compile time, if a selected joint is not a ball joint.

        Note:
            Quaternions are expected in ``[qx, qy, qz, qw]`` order in the joint-local
            reference frame and are normalized during execution; an instance whose quaternion
            is non-finite or zero-norm keeps its previous orientation. A quaternion write
            only updates the joint DoF positions; link poses are refreshed by the forward
            kinematics pass requested through ``compile_write(..., forward_kinematic=True)``.
