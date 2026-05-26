# motrixsim.render.Image

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `pixels` | `Any` | NDArray[byte]: Get the pixels of the image as a numpy array. |

### pixels

```python
pixels: Any
```

NDArray[byte]: Get the pixels of the image as a numpy array.
    
    Note:
        For regular images, returns a 3D array with shape
        ``(height, width, channels)`` where channels is 3 (RGB) or 4 (RGBA)
        depending on the underlying image format.
        For per-instance atlas images, returns a 4D array with shape
        ``(num_instances, tile_height, tile_width, channels)``.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `save_to_disk` | `(self, path: str) -> None` | Save the image to disk with the specified path. |

### save_to_disk

```python
def save_to_disk(self, path: str) -> None
```

Save the image to disk with the specified path.
        
        Raise:
            PyIOError: If saving the image fails.
