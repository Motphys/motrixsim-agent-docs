# motrixsim.Camera

Module: [`motrixsim`](../modules/motrixsim.md)

The Camera object in the scene.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `depth_only` | `bool` | Whether the camera is in depth-only mode. |
| `far_plane` | `float` | Get the far plane distance of the camera. |
| `fovy` | `float` | Get the vertical field of view of the camera in degrees. |
| `index` | `int` | The index of the camera in the `motrixsim.SceneModel.cameras`. |
| `link` | `Optional[Link]` | Get the link that this camera is attached to. |
| `model` | `SceneModel` | The scene model that this camera belongs to. |
| `name` | `Optional[str]` | Option[str]: Get the name of the camera. |
| `near_plane` | `float` | Get the far plane distance of the camera. |
| `position_track` | `str` | Get or set the position track mode of the camera. |
| `render_target` | `str` | Get the render target of the camera, either "window" or "image". |
| `rotation_track` | `str` | Get or set the rotation track mode of the camera. |
| `track_target_link` | `Optional[Link]` | Get or set the link that the camera looks at. |

### depth_only

```python
depth_only: bool
```

Whether the camera is in depth-only mode.

### far_plane

```python
far_plane: float
```

Get the far plane distance of the camera.

### fovy

```python
fovy: float
```

Get the vertical field of view of the camera in degrees.

### index

```python
index: int
```

The index of the camera in the `motrixsim.SceneModel.cameras`.

### link

```python
link: Optional[Link]
```

Get the link that this camera is attached to.
    
    Note:
        Returns `None` if the camera is not attached to any link (i.e., it's a
        world space camera).

### model

```python
model: SceneModel
```

The scene model that this camera belongs to.

### name

```python
name: Optional[str]
```

Option[str]: Get the name of the camera.

### near_plane

```python
near_plane: float
```

Get the far plane distance of the camera.

### position_track

```python
position_track: str
```

Get or set the position track mode of the camera.
    
    Possible values are:
    
    - "free": Free to move in all directions.
    - "fixed_local": Fixed the relative position to parent in local frame.
    - "fixed_world": Fixed the relative position to parent in world frame.

### render_target

```python
render_target: str
```

Get the render target of the camera, either "window" or "image".

### rotation_track

```python
rotation_track: str
```

Get or set the rotation track mode of the camera.
    
    Possible values are:
    
    - "free": Free to rotate.
    - "fixed_local": Fixed the relative rotation to parent in local frame.
    - "fixed_world": Fixed the relative rotation to parent in world frame.
    - "look_at_link": Always look at the target link. This mode requires setting the
      `track_target_link` attribute.

### track_target_link

```python
track_target_link: Optional[Link]
```

Get or set the link that the camera looks at.
    
    Note:
        This attribute is only valid when the rotation track mode is "look_at_link".

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world pose of the camera. |
| `set_near_far` | `(self, near: float, far: float) -> None` | Set the near and far plane of the camera. |
| `set_render_target` | `(self, target: str, w: int = 400, h: int = 300) -> None` | Set the render target of the camera. |

### get_pose

```python
def get_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world pose of the camera.
        
        Args:
           data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 7)``. Each pose is represented as a 7 elements
                array with `[x, y, z, qx, qy, qz,qw]` format.

### set_near_far

```python
def set_near_far(self, near: float, far: float) -> None
```

Set the near and far plane of the camera.
        
        Args:
           near: The near plane distance. Must be positive.
           far: The far plane distance. Must be larger than near.

### set_render_target

```python
def set_render_target(self, target: str, w: int = 400, h: int = 300) -> None
```

Set the render target of the camera.
        
        Args:
           target: The render target, either "window" or "image".
        
           w: The width of the image if the target is "image". ignored if the target is
           "window".   
        
           h: The height of the image if the target is "image". ignored if the target is
           "window".
        
        Note:
           This method must be called before you launch the render application.
