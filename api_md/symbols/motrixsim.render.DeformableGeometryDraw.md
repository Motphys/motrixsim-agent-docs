# motrixsim.render.DeformableGeometryDraw

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

One fixed draw item's slice of the shared scene index buffer.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `index_count` | `int` |  |
| `index_offset` | `int` |  |

### index_count

```python
index_count: int
```

### index_offset

```python
index_offset: int
```

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, index_offset: int, index_count: int) -> DeformableGeometryDraw` | Create one fixed draw item. |

### __new__

```python
def __new__(cls, index_offset: int, index_count: int) -> DeformableGeometryDraw
```

Create one fixed draw item.

        Note:
            `index_offset` selects a triangle boundary in the shared index array. An
            `index_count` of zero makes this item absent for the current frame while the other
            items continue to draw.

        Args:
            index_offset: First index used by this draw item.
            index_count: Number of indices used by this draw item.
