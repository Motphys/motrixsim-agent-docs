# motrixsim.render.DeformableGeometryLayout

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

Launch-time capacities for the scene's deformable geometry.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `draw_count` | `int` |  |
| `index_capacity` | `int` |  |
| `vertex_capacity` | `int` |  |

### draw_count

```python
draw_count: int
```

### index_capacity

```python
index_capacity: int
```

### vertex_capacity

```python
vertex_capacity: int
```

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, vertex_capacity: int, index_capacity: int, draw_count: int) -> DeformableGeometryLayout` | Create a launch-time deformable geometry layout. |

### __new__

```python
def __new__(cls, vertex_capacity: int, index_capacity: int, draw_count: int) -> DeformableGeometryLayout
```

Create a launch-time deformable geometry layout.

        Note:
            The layout describes one scene-wide geometry and a fixed set of draw items. It does not
            allocate one resource per deformable object.

        Args:
            vertex_capacity: Maximum vertex count accepted per frame.
            index_capacity: Maximum triangle-index count accepted per frame.
            draw_count: Number of fixed draw items over the shared index buffer.
