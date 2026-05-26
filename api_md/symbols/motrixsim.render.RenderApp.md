# motrixsim.render.RenderApp

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

The RenderApp class is responsible for rendering the simulation scene.
    
    This class provides functionality to load models, update their transformations, and render the
    scene. It also handles the creation and management of the render application.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `gizmos` | `RenderGizmos` | The gizmos module of the render app. |
| `input` | `Input` | The input module of the render app. |
| `is_closed` | `bool` | Check if the render app is closed. |
| `opt` | `RenderOpt` | The options of the render app. |
| `system_camera` | `SystemCamera` | The system camera |
| `ui` | `RenderUI` | The UI module of the render app. |
| `widgets` | `RenderWidgets` | The widgets module of the render app. |

### gizmos

```python
gizmos: RenderGizmos
```

The gizmos module of the render app.
    
    Return the gizmos module for rendering simple shapes in immediate mode.

### input

```python
input: Input
```

The input module of the render app.
    
    Return the input module for handling user input events.

### is_closed

```python
is_closed: bool
```

Check if the render app is closed.

### opt

```python
opt: RenderOpt
```

The options of the render app.
    
    Return the options of the render app, which can be used to configure various settings.

### system_camera

```python
system_camera: SystemCamera
```

The system camera

### ui

```python
ui: RenderUI
```

The UI module of the render app.

### widgets

```python
widgets: RenderWidgets
```

The widgets module of the render app.
    
    Return the widgets module for creating UI widgets.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__enter__` | `(self) -> RenderApp` |  |
| `__exit__` | `(self, exc_type: Any, _exc_val: Any, _exc_tb: Any) -> bool` |  |
| `__new__` | `(cls, log_level: str = 'WARN', headless: bool = False, fps: Optional[int] = None) -> RenderApp` | Create a new RenderApp instance. |
| `create_image` | `(self, pixels: numpy.typing.NDArray[numpy.uint8], is_srgb: bool = True, keep_in_cpu: bool = True) -> Image` | Create an image from a numpy array of pixel data. |
| `get_camera` | `(self, index: int) -> Optional[RenderCamera]` | Get a render camera instance. |
| `get_texture_image` | `(self, name: str) -> Image` | Get the image handle of a texture loaded by name. |
| `launch` | `(self, model: SceneModel, batch: int = 1, render_offset: Optional[Sequence[Sequence[float]]] = None, render_settings: RenderSettings = ...) -> None` | Load a model into the render app. |
| `set_all_scene_vis` | `(self, visible: bool) -> None` |  |
| `set_main_camera` | `(self, camera: Optional[Camera]) -> None` | Set the main camera of the render app. |
| `set_scene_vis` | `(self, indices: Sequence[int], visible: bool) -> None` |  |
| `sync` | `(self, data: Any, wait: bool = False) -> None` | Synchronize the render app backend with python data. |

### __enter__

```python
def __enter__(self) -> RenderApp
```

### __exit__

```python
def __exit__(self, exc_type: Any, _exc_val: Any, _exc_tb: Any) -> bool
```

### __new__

```python
def __new__(cls, log_level: str = 'WARN', headless: bool = False, fps: Optional[int] = None) -> RenderApp
```

Create a new RenderApp instance.
        
        Args:
            log_level: The log level for the render app. Default is "WARN".
            headless: Whether to run in headless mode. Default is False.
            fps: Target frame rate for the renderer in headless mode. If None, uses
        unlimited FPS. Default is None.

### create_image

```python
def create_image(self, pixels: numpy.typing.NDArray[numpy.uint8], is_srgb: bool = True, keep_in_cpu: bool = True) -> Image
```

Create an image from a numpy array of pixel data.
        
        Args:
            pixels: A 3D numpy array with shape `(height, width, channels)`
                where channels is either 3 (RGB) or 4 (RGBA). The array must be contiguous and
                contain uint8 values in the range [0, 255].
            is_srgb: Whether the image is in sRGB color space. Default is True.
            keep_in_cpu: Whether to keep the image data in CPU memory after uploading
                to GPU. If False, pixel data cannot be accessed after upload. Default is True.
        
        Returns:
            Image: A handle to the created image asset that can be used for textures,
                materials, etc.
        
        Raises:
            InvalidArgumentError: If the array shape is invalid or not contiguous.
            OtherRenderError: If image creation fails.

### get_camera

```python
def get_camera(self, index: int) -> Optional[RenderCamera]
```

Get a render camera instance.

### get_texture_image

```python
def get_texture_image(self, name: str) -> Image
```

Get the image handle of a texture loaded by name.
        
        This is typically used to access `TextureSource.Pixels` textures at runtime
        so their pixel data can be read or updated.
        
        Args:
            name: The texture name as defined in the MSD assets.
        
        Returns:
            Image: A handle to the texture's image. Updating its pixels will update the
                rendered texture in the scene.
        
        Raises:
            InvalidArgumentError: If no texture with the given name was found.

### launch

```python
def launch(self, model: SceneModel, batch: int = 1, render_offset: Optional[Sequence[Sequence[float]]] = None, render_settings: RenderSettings = ...) -> None
```

Load a model into the render app.
        
        Args:
            model: The scene model to load into the render app.
            batch: The number of instances to create. Default is 1.
            render_offset: The offset of each instance in
                render space. Default is None.
        
        Raises:
            RenderClosedError: If the render app is closed.
            InvalidArgumentError: If the file is invalid.
            InvalidFileError: If there are issues with file operations.
            OtherRenderError: For other unexpected errors.

### set_all_scene_vis

```python
def set_all_scene_vis(self, visible: bool) -> None
```

### set_main_camera

```python
def set_main_camera(self, camera: Optional[Camera]) -> None
```

Set the main camera of the render app.
        
        Args:
            camera: The camera to set as the main camera. If None, the system
            camera will be used.

### set_scene_vis

```python
def set_scene_vis(self, indices: Sequence[int], visible: bool) -> None
```

### sync

```python
def sync(self, data: Any, wait: bool = False) -> None
```

Synchronize the render app backend with python data.
        
        Args:
            data: The scene data to synchronize with the renderer.
        
                This argument accept following types:
        
                    - None: No data is provided, the render will use the last known transforms.
                    - SceneData: The scene data used to update the render. If you lanched the render
                      with `repeat > 1`, the shape the of data must be `(repeat,)`.
                    - NDArray: A 3D numpy array with shape `(num_instances, num_links, 7)`, where
                      the last dimension represents the pose of each link in the format `[x, y, z,
                      qx, qy, qz, qw]`.
            wait: If True, block until all pending capture tasks are completed.
                Default is False.
        Raises:
            RenderClosedError: If the render app is closed.
            InvalidArgumentError: If neither datas nor poses is provided correctly.
            InvalidFileError: If there are issues with file operations.
            OtherRenderError: Not launched with model file.
