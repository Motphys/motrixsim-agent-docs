# motrixsim.render.widgets.ImageWidget

Module: [`motrixsim.render.widgets`](../modules/motrixsim.render.widgets.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `image` | `Image` |  |

### image

```python
image: Image
```

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `remove` | `(self) -> None` | Remove the image widget from the render window. |
| `update` | `(self, image: Optional[Image] = None, layout: Optional[Layout] = None) -> None` | Update the image widget. |

### remove

```python
def remove(self) -> None
```

Remove the image widget from the render window.
        
        Note:
            After calling this method, the widget will be removed from the render window.
            Any further calls to `update()` on this object will result in an error.

### update

```python
def update(self, image: Optional[Image] = None, layout: Optional[Layout] = None) -> None
```

Update the image widget.
        
        Args:
            image: New image object to display. If not provided,
                keeps the current image.
            layout: New layout configuration. If not provided,
                keeps the current layout.
        
        Raises:
            RuntimeError: If the widget is invalid.
        
        Example:
        
        .. code:: python
        
            # Update with new image
            widget.update(image=new_img)
            # Update with new layout
            widget.update(layout=new_layout)
            # Update both
            widget.update(image=new_img, layout=new_layout)
