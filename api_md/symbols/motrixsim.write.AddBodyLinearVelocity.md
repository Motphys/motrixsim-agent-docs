# motrixsim.write.AddBodyLinearVelocity

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for world linear velocity increments of selected floating bodies.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target floating bodies given by names or indices, or |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target floating bodies given by names or indices, or
    `None` for all floating bodies in body model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> AddBodyLinearVelocity` | Create a write source that adds world linear velocity increments to floating bodies. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> AddBodyLinearVelocity
```

Create a write source that adds world linear velocity increments to floating bodies.

        Args:
            selection: Floating bodies given by
                names or indices, or `None` for all floating bodies in body model order. The
                given order defines the buffer layout; names and indices must not be mixed and
                duplicates are rejected at compile time. Indices address the body model order.

        Raises:
            ValueError: At compile time, if a selected body is not floating or is a mocap, or
                another field sets or adds linear velocity on the same body.

        Note:
            The field shape is ``(num_selected_bodies, 3)``. Each row contains world-frame
            ``[delta_vx, delta_vy, delta_vz]`` in m/s, added directly to the current linear
            velocity DoF without reading link kinematics or rotating the increment. This is a
            velocity kick, not a physical impulse; position, angular velocity and joint velocity
            are unchanged. The buffer is not consumed or cleared, so repeated executions with
            ``reset=False`` accumulate. With ``reset=True``, increments apply after reset.
            Link kinematics refresh only when ``forward_kinematic=True`` is requested.
