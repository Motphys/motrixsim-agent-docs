# motrixsim.write.BodyLinearVelocity

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the world linear velocities of selected floating bodies.

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
| `__new__` | `(cls, selection: Optional[Any] = None) -> BodyLinearVelocity` | Create a write source for world linear velocities of floating bodies selected by names |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> BodyLinearVelocity
```

Create a write source for world linear velocities of floating bodies selected by names
        or indices.

        Args:
            selection: Floating bodies given by
                names or indices, or `None` for all floating bodies in body model order. The
                given order defines the buffer layout; names and indices must not be mixed and
                duplicates are rejected at compile time. Indices address the body model order.

        Raises:
            ValueError: At compile time, if a selected body is a mocap or is neither a floating
                body nor a mocap.
