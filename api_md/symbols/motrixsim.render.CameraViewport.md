# motrixsim.render.CameraViewport

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `camera` | `Camera` | The camera displayed in this viewport. |

### camera

```python
camera: Camera
```

The camera displayed in this viewport.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `remove` | `(self) -> None` | Remove the camera viewport widget from the render window. |
| `update` | `(self, camera: Optional[Camera] = None, layout: Optional[Layout] = None, sim_world_index: Optional[int] = None) -> None` | Update the camera viewport widget. |

### remove

```python
def remove(self) -> None
```

Remove the camera viewport widget from the render window.
        
        Note:
            After calling this method, the viewport will be removed from the render window.
            Any further calls to `update()` on this object will result in an error.

### update

```python
def update(self, camera: Optional[Camera] = None, layout: Optional[Layout] = None, sim_world_index: Optional[int] = None) -> None
```

Update the camera viewport widget.
        
        Args:
            camera: New camera object to display. If not provided,
                keeps the current camera.
            layout: New layout configuration. If not provided,
                keeps the current layout.
            sim_world_index: New simulation world index. If not provided,
                keeps the current value.
        Raises
            RuntimeError: If the widget is invalid.
