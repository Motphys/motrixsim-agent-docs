# motrixsim.query.JointQuaternion

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the local orientation quaternions of selected ball joints.

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
| `__new__` | `(cls, selection: Any) -> JointQuaternion` | Create a query source for local orientation quaternions of selected ball joints. |

### __new__

```python
def __new__(cls, selection: Any) -> JointQuaternion
```

Create a query source for local orientation quaternions of selected ball joints.

        Args:
            selection: Joints given by names or indices.
                The given order is preserved and duplicates are allowed; names and indices must not
                be mixed. Every selected joint must be a ball joint.

        Note:
            Quaternions are reported in ``[qx, qy, qz, qw]`` order in the joint-local
            reference frame.
