# motrixsim.write.BodyRotation

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for the world rotations of selected floating bodies and mocaps.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target bodies given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target bodies given by names or indices, or `None` for
    all floating bodies and mocaps in body model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> BodyRotation` | Create a write source for world rotations of floating bodies and mocaps selected by |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> BodyRotation
```

Create a write source for world rotations of floating bodies and mocaps selected by
        names or indices as quaternions.

        Args:
            selection: Bodies given by names or
                indices, or `None` for all floating bodies and mocaps in body model order. The
                given order defines the buffer layout; names and indices must not be mixed and
                duplicates are rejected at compile time. Indices address the body model order.

        Raises:
            ValueError: At compile time, if a selected body is neither a floating body nor a
                mocap.

        Note:
            Quaternions are expected in ``[qx, qy, qz, qw]`` order and are normalized during
            execution; an instance whose quaternion is non-finite or zero-norm keeps its
            previous rotation.
