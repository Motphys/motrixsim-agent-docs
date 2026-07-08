# motrixsim.render.Color

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

A color in RGBA format, where each component is a float in the range [0.0, 1.0].

## Properties

| Name | Type | Description |
|------|------|-------------|
| `a` | `float` | The alpha component of the color, representing transparency. |
| `b` | `float` | The blue component of the color. |
| `g` | `float` | The green component of the color. |
| `r` | `float` | The red component of the color. |

### a

```python
a: float
```

The alpha component of the color, representing transparency.

### b

```python
b: float
```

The blue component of the color.

### g

```python
g: float
```

The green component of the color.

### r

```python
r: float
```

The red component of the color.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `rgb` | `(r: float, g: float, b: float) -> Color` | Create a color with red, green, blue. Each value should be in the range [0.0, 1.0]. |
| `white` | `() -> Color` |  |

### rgb

```python
def rgb(r: float, g: float, b: float) -> Color
```

Create a color with red, green, blue. Each value should be in the range [0.0, 1.0].

        Args:
            r: Red component.
            g: Green component.
            b: Blue component.
        Returns:
            Color: The created color.

### white

```python
def white() -> Color
```
