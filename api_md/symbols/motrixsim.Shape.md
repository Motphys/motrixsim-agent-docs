# motrixsim.Shape

Module: [`motrixsim`](../modules/motrixsim.md)

The shape type of a collider.
    
    Enum Values:
        Sphere: A spherical collision shape
        Cylinder: A cylindrical collision shape
        Capsule: A capsule collision shape (cylinder with hemispherical ends)
        Cuboid: A box-shaped collision shape
        InfinitePlane: An infinite plane collision shape
        HField: A height field collision shape for terrain

## Properties

| Name | Type | Description |
|------|------|-------------|
| `Capsule` | `Any` | Capsule shape. |
| `Cuboid` | `Any` | Cuboid shape. |
| `Cylinder` | `Any` | Cylinder shape. |
| `Ellipsoid` | `Any` | Ellipsoid shape. |
| `HField` | `Any` | HField shape. |
| `InfinitePlane` | `Any` | InfinitePlane shape. |
| `Mesh` | `Any` | Mesh shape |
| `Plane` | `Any` | Sized Plane |
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

HField shape.

### InfinitePlane

```python
InfinitePlane: Any
```

InfinitePlane shape.

### Mesh

```python
Mesh: Any
```

Mesh shape

### Plane

```python
Plane: Any
```

Sized Plane

### Sphere

```python
Sphere: Any
```

Sphere shape.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `type_names` | `() -> list[str]` | Returns all shape type names as a list of strings. |
| `types` | `() -> list[Shape]` | Returns all shape types as a list. |

### type_names

```python
def type_names() -> list[str]
```

Returns all shape type names as a list of strings.
        
        Returns:
            List[str]: All shape type names.

### types

```python
def types() -> list[Shape]
```

Returns all shape types as a list.
        
        Returns:
            List[Shape]: All shape types.
