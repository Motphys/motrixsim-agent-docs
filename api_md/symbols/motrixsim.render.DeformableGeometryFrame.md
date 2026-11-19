# motrixsim.render.DeformableGeometryFrame

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

One frame of deformable geometry.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, positions: Any, normals: Any, indices: Any, draws: Sequence[DeformableGeometryDraw]) -> DeformableGeometryFrame` | Create one frame of deformable geometry. |

### __new__

```python
def __new__(cls, positions: Any, normals: Any, indices: Any, draws: Sequence[DeformableGeometryDraw]) -> DeformableGeometryFrame
```

Create one frame of deformable geometry.

        Note:
            Positions and normals are packed world-space `vec3` values. Indices may change every
            frame and refer to the same shared vertex array.

        Args:
            positions: One-dimensional, C-contiguous float32 vertex positions.
            normals: One-dimensional, C-contiguous float32 vertex normals.
            indices: One-dimensional, C-contiguous uint32 triangle indices.
            draws: Fixed-order draw items over the shared index
        buffer.
