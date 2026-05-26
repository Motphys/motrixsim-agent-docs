# motrixsim.CameraMgr

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `cameras` | `list[Camera]` | List[Camera]: All the cameras defined in the model. |
| `model` | `SceneModel` | The scene model that this camera manager belongs to. |

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

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, index: Any) -> Any` | Get a camera by index or name. |
| `__len__` | `(self) -> int` | Get the number of cameras in the manager. |
| `get_index` | `(self, name: str) -> Optional[int]` | Get the camera index by name. |
| `tolist` | `(self) -> list[Camera]` | Convert the camera manager to a list of cameras. |

### __getitem__

```python
def __getitem__(self, index: Any) -> Any
```

Get a camera by index or name.
        
        Args:
            index: The index or name of the camera.
        
        Returns:
            Camera: The camera object.
        
        Raises:
            IndexError: If the index is out of range or name not found.
            TypeError: If the index is not an int or str.

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
