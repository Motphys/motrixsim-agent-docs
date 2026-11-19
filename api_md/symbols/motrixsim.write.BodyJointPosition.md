# motrixsim.write.BodyJointPosition

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the positions of selected single-DoF joints.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target joints given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target joints given by names or indices, or `None` for
    all single-DoF joints in joint model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> BodyJointPosition` | Create a write source for positions of single-DoF joints selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> BodyJointPosition
```

Create a write source for positions of single-DoF joints selected by names or indices.

        Args:
            selection: Joints given by names or
                indices, or `None` for all single-DoF joints in joint model order. The given
                order defines the buffer layout; names and indices must not be mixed and
                duplicates are rejected at compile time. Indices address the joint model order.

        Raises:
            ValueError: At compile time, if a selected joint does not have exactly one position
                and one velocity DoF.

        Note:
            A joint position write only updates the joint DoF positions; link poses are
            refreshed by the forward kinematics pass requested through
            ``compile_write(..., forward_kinematic=True)``. Floating base DoF are not joints
            and keep being written through `BodyPosition` and `BodyRotation`.
