# motrixsim.Shape

Module: [`motrixsim`](../modules/motrixsim.md)

The source shape type of a high-level geometry.

    This mirrors Rust's `msd::geom::ShapeType` / `GeometryShape` and describes the user-facing
    geometry before compile-time lowering. A mesh high-level shape may lower to one or more
    low-level runtime collider shapes.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `Capsule` | `Any` | Capsule shape. |
| `Cuboid` | `Any` | Cuboid shape. |
| `Cylinder` | `Any` | Cylinder shape. |
| `Ellipsoid` | `Any` | Ellipsoid shape. |
| `HField` | `Any` | Height field shape. |
| `InfinitePlane` | `Any` | Infinite plane shape. |
| `Mesh` | `Any` | Source mesh shape. |
| `Plane` | `Any` | Sized plane shape. |
| `Sphere` | `Any` | Sphere shape. |

### Capsule

```python
Capsule: Any
```

Capsule shape.

### Cuboid

```python
Cuboid: Any
```

Cuboid shape.

### Cylinder

```python
Cylinder: Any
```

Cylinder shape.

### Ellipsoid

```python
Ellipsoid: Any
```

Ellipsoid shape.

### HField

```python
HField: Any
```

Height field shape.

### InfinitePlane

```python
InfinitePlane: Any
```

Infinite plane shape.

### Mesh

```python
Mesh: Any
```

Source mesh shape.

### Plane

```python
Plane: Any
```

Sized plane shape.

### Sphere

```python
Sphere: Any
```

Sphere shape.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `type_names` | `() -> list[str]` | Returns all high-level source shape type names as a list of strings. |
| `types` | `() -> list[Shape]` | Returns all high-level source shape types as a list. |

### type_names

```python
def type_names() -> list[str]
```

Returns all high-level source shape type names as a list of strings.

        Returns:
            List[str]: All high-level source shape type names.

### types

```python
def types() -> list[Shape]
```

Returns all high-level source shape types as a list.

        Returns:
            List[Shape]: All high-level source shape types.
