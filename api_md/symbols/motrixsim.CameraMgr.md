# motrixsim.CameraMgr

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `cameras` | `list[Camera]` | List[Camera]: All the cameras defined in the model. |
| `model` | `SceneModel` | The scene model that this camera manager belongs to. |
| `system_camera` | `Camera` | The system (default free) camera of the scene. |
| `system_render_target` | `str` | Get the render target of the system camera, either "window" or "image". |

### cameras

```python
cameras: list[Camera]
```

List[Camera]: All the cameras defined in the model.

### model

```python
model: SceneModel
```

The scene model that this camera manager belongs to.

### system_camera

```python
system_camera: Camera
```

The system (default free) camera of the scene.

    Note:
        The returned camera's ``index`` is ``None``. The camera is a read-only view of
        the built model: configure its near/far plane, render target, ``depth_only`` and
        ``segmentation`` on the MSD layer (``msd.SystemCamera``) before ``build()``.
        ``depth_only`` / ``segmentation`` follow the scene camera semantics and only take
        effect on the ``"image"`` render target. ``get_pose`` is not available for the
        system camera.

### system_render_target

```python
system_render_target: str
```

Get the render target of the system camera, either "window" or "image".

    Note:
        The render target is configured on the MSD layer (``msd.SystemCamera.render_target``)
        before ``build()``; the built model is immutable.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, index: Any) -> Any` | Get a camera by index, name, or slice. |
| `__len__` | `(self) -> int` | Get the number of cameras in the manager. |
| `get_index` | `(self, name: str) -> Optional[int]` | Get the camera index by name. |
| `tolist` | `(self) -> list[Camera]` | Convert the camera manager to a list of cameras. |

### __getitem__

```python
def __getitem__(self, index: Any) -> Any
```

Get a camera by index, name, or slice.

        Args:
            index: The index, name, or slice selecting cameras.

        Returns:
            Camera | list[Camera]: The single camera for ``int`` / ``str`` indexing,
            or a list of cameras for ``slice`` indexing.

        Raises:
            IndexError: If the index is out of range or name not found.
            TypeError: If the index is not an int, str, or slice.

### __len__

```python
def __len__(self) -> int
```

Get the number of cameras in the manager.

        Returns:
            int: The number of cameras.

### get_index

```python
def get_index(self, name: str) -> Optional[int]
```

Get the camera index by name.

        Args:
            name: The name of the camera.

        Returns:
            int: The index of the camera.

        Panics:
            If the camera name does not exist.

### tolist

```python
def tolist(self) -> list[Camera]
```

Convert the camera manager to a list of cameras.
