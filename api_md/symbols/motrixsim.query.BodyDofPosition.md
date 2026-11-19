# motrixsim.query.BodyDofPosition

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A query source for the DoF positions of one body.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `body` | `Any` | str \| int: The selected body given by name or index. |
| `include_base` | `bool` | Whether the floating base DoF of the body is included. |

### body

```python
body: Any
```

str | int: The selected body given by name or index.

### include_base

```python
include_base: bool
```

Whether the floating base DoF of the body is included.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, body: Any, include_base: bool = True) -> BodyDofPosition` | Create a query source for the DoF positions of one body. |

### __new__

```python
def __new__(cls, body: Any, include_base: bool = True) -> BodyDofPosition
```

Create a query source for the DoF positions of one body.

        Args:
            body: The body given by name or index.
            include_base: Whether to include the floating base DoF of the body if it has
                one. Defaults to `True`.
