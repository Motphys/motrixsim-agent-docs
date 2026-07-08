# motrixsim.CameraMgr

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `cameras` | `list[Camera]` | List[Camera]: All the cameras defined in the model. |
| `model` | `SceneModel` | The scene model that this camera manager belongs to. |
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

### system_render_target

```python
system_render_target: str
```

Get the render target of the system camera, either "window" or "image".

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, index: Any) -> Any` | Get a camera by index, name, or slice. |
| `__len__` | `(self) -> int` | Get the number of cameras in the manager. |
| `get_index` | `(self, name: str) -> Optional[int]` | Get the camera index by name. |
| `set_system_render_target` | `(self, target: str, w: int = 400, h: int = 300) -> None` | Set the render target of the system camera. |
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

### set_system_render_target

```python
def set_system_render_target(self, target: str, w: int = 400, h: int = 300) -> None
```

Set the render target of the system camera.

        Args:
           target: The render target, either "window" or "image".

           w: The width of the image if the target is "image". ignored if the target is
           "window".

           h: The height of the image if the target is "image". ignored if the target is
           "window".

        Note:
           This method must be called before you launch the render application.

### tolist

```python
def tolist(self) -> list[Camera]
```

Convert the camera manager to a list of cameras.
