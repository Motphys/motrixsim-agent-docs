# motrixsim.render.Layout

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

Layout configuration for camera viewport widgets.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `bottom` | `Any` |  |
| `height` | `Any` |  |
| `left` | `Any` |  |
| `right` | `Any` |  |
| `top` | `Any` |  |
| `width` | `Any` |  |

### bottom

```python
bottom: Any
```

### height

```python
height: Any
```

### left

```python
left: Any
```

### right

```python
right: Any
```

### top

```python
top: Any
```

### width

```python
width: Any
```

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, left: Optional[Any] = None, right: Optional[Any] = None, top: Optional[Any] = None, bottom: Optional[Any] = None, width: Optional[Any] = None, height: Optional[Any] = None) -> Layout` | Create a new layout configuration. |

### __new__

```python
def __new__(cls, left: Optional[Any] = None, right: Optional[Any] = None, top: Optional[Any] = None, bottom: Optional[Any] = None, width: Optional[Any] = None, height: Optional[Any] = None) -> Layout
```

Create a new layout configuration.
        
        Note:
            The layout parameters accept multiple formats:
            - String: "50px" for pixels, "50%" for percentage, "auto" for automatic
            - Number: Interpreted as pixels (e.g., 50 = 50px)
            All parameters default to "auto" if not specified.
        
        Args:
            left: Left position. Default is "auto".
            right: Right position. Default is "auto".
            top: Top position. Default is "auto".
            bottom: Bottom position. Default is "auto".
            width: Width. Default is "auto".
            height: Height. Default is "auto".
        
        Example:
        
        .. code:: python
        
            # Specify only the parameters you need
            layout1 = motrixsim.render.Layout(left=50, top=50, width=200, height=200)
            # All parameters default to "auto"
            layout2 = motrixsim.render.Layout()
            # Using percentages
            layout3 = motrixsim.render.Layout(
                left="10%", top="10%", width="50%", height="50%"
            )
            # Mixed
            layout4 = motrixsim.render.Layout(left="auto", top="50px", width="100%", height="auto")
