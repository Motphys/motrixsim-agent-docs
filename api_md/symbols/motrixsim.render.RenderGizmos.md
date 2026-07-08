# motrixsim.render.RenderGizmos

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

Gizmos module for rendering simple shapes in immediate mode.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `draw_arrow` | `(self, start: Any, end: Any, color: Color = ...) -> None` | Draw a arrow. |
| `draw_axes` | `(self, pos: Optional[Any] = None, rot: Optional[Any] = None, length: float = 1.0) -> None` | Draw the XYZ axes at the given position and rotation. |
| `draw_capsule` | `(self, half_height: float, radius: float, pos: Any, rot: Any, color: Color = ...) -> None` | Draw a capsule. |
| `draw_cuboid` | `(self, size: Any, pos: Any, rot: Any, color: Color = ...) -> None` | Draw a cuboid. |
| `draw_cylinder` | `(self, half_height: float, radius: float, pos: Any, rot: Any, color: Color = ...) -> None` | Draw a cylinder. |
| `draw_grid` | `(self, pos: Any, rot: Any, x_count: int = 2, y_count: int = 2, z_count: int = 2, spacing: Optional[Any] = None, color: Color = ...) -> None` | Draw a rectangle. |
| `draw_line` | `(self, start: Any, end: Any, color: Color = ...) -> None` | Draw a line. |
| `draw_ray` | `(self, start: Any, vector: Any, color: Color = ...) -> None` | Draw a ray. |
| `draw_rect` | `(self, width: float, height: float, pos: Any, rot: Any, color: Color = ...) -> None` | Draw a rectangle. |
| `draw_sphere` | `(self, radius: float, pos: Any, color: Color = ...) -> None` | Draw a sphere at the given position with the specified radius and color. |

### draw_arrow

```python
def draw_arrow(self, start: Any, end: Any, color: Color = ...) -> None
```

Draw a arrow.

        Args:
            start: The start point of the arrow in 3D space.
            end: The end point of the arrow.
            color: Color of the arrow.

### draw_axes

```python
def draw_axes(self, pos: Optional[Any] = None, rot: Optional[Any] = None, length: float = 1.0) -> None
```

Draw the XYZ axes at the given position and rotation.

        Args:
            pos: the position of axes with (x,y,z) format.
            rot: the rotation of axes as a quaternion (x, y, z,
            length: the length of each axis.
        w).

### draw_capsule

```python
def draw_capsule(self, half_height: float, radius: float, pos: Any, rot: Any, color: Color = ...) -> None
```

Draw a capsule.

        Args:
            half_height: The half height of the capsule.
            radius: The radius of the capsule.
            pos: Position of the capsule in 3D space.
            rot: Rotation of the capsule as a quaternion (x, y, z, w).
            color: Color of the capsule.

### draw_cuboid

```python
def draw_cuboid(self, size: Any, pos: Any, rot: Any, color: Color = ...) -> None
```

Draw a cuboid.

        Args:
            size: Size of the cuboid in 3D space.
            pos: Position of the cuboid in 3D space.
            rot: Rotation of the cuboid as a quaternion (x, y, z, w).
            color: Color of the cuboid.

### draw_cylinder

```python
def draw_cylinder(self, half_height: float, radius: float, pos: Any, rot: Any, color: Color = ...) -> None
```

Draw a cylinder.

        Args:
            half_height: The half height of the cylinder.
            radius: The radius of the cylinder.
            pos: Position of the cylinder in 3D space.
            rot: Rotation of the cylinder as a quaternion (x, y, z, w).
            color: Color of the cylinder.

### draw_grid

```python
def draw_grid(self, pos: Any, rot: Any, x_count: int = 2, y_count: int = 2, z_count: int = 2, spacing: Optional[Any] = None, color: Color = ...) -> None
```

Draw a rectangle.

        Args:
            pos: Position of the rectangle in 3D space.
            rot: Rotation of the rectangle as a quaternion (x, y, z, w).
            x_count: The number of grid cells along the x-axis.
            y_count: The number of grid cells along the y-axis.
            z_count: The number of grid cells along the z-axis.
            spacing: The spacing(x,y,z) between the grid cells.
            color: Color of the rectangle.

### draw_line

```python
def draw_line(self, start: Any, end: Any, color: Color = ...) -> None
```

Draw a line.

        Args:
            start: The start point of the line in 3D space.
            end: The end point of the line.
            color: Color of the line.

### draw_ray

```python
def draw_ray(self, start: Any, vector: Any, color: Color = ...) -> None
```

Draw a ray.

        Args:
            start: The start point of the ray in 3D space.
            vector: The direction of the ray.
            color: Color of the ray.

### draw_rect

```python
def draw_rect(self, width: float, height: float, pos: Any, rot: Any, color: Color = ...) -> None
```

Draw a rectangle.

        Args:
            width: The width of the rectangle.
            height: The height of the rectangle.
            pos: Position of the rectangle in 3D space.
            rot: Rotation of the rectangle as a quaternion (x, y, z, w).
            color: Color of the rectangle.

### draw_sphere

```python
def draw_sphere(self, radius: float, pos: Any, color: Color = ...) -> None
```

Draw a sphere at the given position with the specified radius and color.

        Args:
            radius: The radius of the sphere.
            pos: The position of the sphere in 3D space.
            color: The color of the sphere.
