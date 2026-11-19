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
| `__new__` | `(cls, log_level: str = 'WARN', headless: bool = False, enable_render_diagnostics: bool = False, blueprint: Optional[Any] = None) -> RenderApp` | Create a new RenderApp instance. |
| `_configure_deformable_geometry` | `(self, deformable_geometry: Optional[DeformableGeometryLayout] = None) -> None` | Configure the scene's deformable geometry for the next `launch`. |
| `_queue_deformable_geometry` | `(self, deformable_geometry: Optional[DeformableGeometryFrame] = None) -> None` | Queue one scene deformable geometry frame for the next render sync. |
| `close` | `(self) -> None` | Close the render app and release its backend resources. |
| `create_image` | `(self, pixels: numpy.typing.NDArray[numpy.uint8], is_srgb: bool = True, keep_in_cpu: bool = True) -> Image` | Create an image from a numpy array of pixel data. |
| `get_camera` | `(self, index: int) -> Optional[RenderCamera]` | Get a render camera instance. |
| `get_texture_image` | `(self, name: str) -> Image` | Get the image handle of a texture loaded by name. |
| `hide` | `(self, view: Optional[Any] = None, *, title: Optional[str] = None, include: Optional[Sequence[str]] = None, exclude: Optional[Sequence[str]] = None) -> None` | Hide one Viewer View declaration, or live Views selected by final title. |
| `launch` | `(self, model: SceneModel, batch: int = 1, render_offset: Optional[Sequence[Sequence[float]]] = None, render_settings: RenderSettings = ...) -> None` | Load a model into the render app. |
| `rebuild` | `(self, frame: Frame) -> None` | Mark one custom UI Frame dirty for rebuilding at the next synchronization point. |
| `set_all_scene_vis` | `(self, visible: bool) -> None` |  |
| `set_main_camera` | `(self, camera: Optional[Camera]) -> None` | Set the main camera of the render app. |
| `set_scene_vis` | `(self, indices: Sequence[int], visible: bool) -> None` |  |
| `show` | `(self, view: Optional[Any] = None, *, select: bool = False, title: Optional[str] = None, include: Optional[Sequence[str]] = None, exclude: Optional[Sequence[str]] = None) -> None` | Show one Viewer View declaration, or restore hidden Views selected by final title. |
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
def __new__(cls, log_level: str = 'WARN', headless: bool = False, enable_render_diagnostics: bool = False, blueprint: Optional[Any] = None) -> RenderApp
```

Create a new RenderApp instance.

        Args:
            log_level: The log level for the render app. Default is "WARN".
            headless: Whether to run in headless mode. Default is False.
            enable_render_diagnostics: Whether to enable Bevy GPU render diagnostics.
        Default is False.
            blueprint: Initial Viewer blueprint for the
                RenderApp window. Construction consumes the blueprint and its Views;
                keep the View objects for this app's show/hide calls. If construction fails,
                create new Views and a new blueprint before trying again.
                Non-empty blueprints are not yet supported on WASM.

        Note:
            Frame pacing is the caller's responsibility: in windowed mode the render
            service renders on client syncs and input events (reactive loop, capped by
            vsync), so pace the client loop against the wall clock (see
            motrixsim.run.render_loop).

        Raises:
            InvalidArgumentError: If `blueprint` is provided while `headless=True` or on WASM.

### _configure_deformable_geometry

```python
def _configure_deformable_geometry(self, deformable_geometry: Optional[DeformableGeometryLayout] = None) -> None
```

Configure the scene's deformable geometry for the next `launch`.

### _queue_deformable_geometry

```python
def _queue_deformable_geometry(self, deformable_geometry: Optional[DeformableGeometryFrame] = None) -> None
```

Queue one scene deformable geometry frame for the next render sync.

        This queues a command without sending `SyncTo`. The GPU bridge uses it to combine pose and
        deformable geometry updates into one sync frame, or to implement geometry-only
        synchronization.

### close

```python
def close(self) -> None
```

Close the render app and release its backend resources.

        Calling this method more than once has no effect.

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

### hide

```python
def hide(self, view: Optional[Any] = None, *, title: Optional[str] = None, include: Optional[Sequence[str]] = None, exclude: Optional[Sequence[str]] = None) -> None
```

Hide one Viewer View declaration, or live Views selected by final title.

        The command is sent to the render service by the next `sync()` call. Call `show()` with
        the same Python object to restore it.

        Args:
            view: One materialized View leaf.
            title: One exact final title to hide.
            include: Full-title regular expressions to include when
                `view` is omitted. Omitted selects all live titles; an empty sequence selects none.
            exclude: Full-title regular expressions to exclude. Excludes
                always take precedence over includes.

        Raises:
            RenderClosedError: If the render app is closed.
            InvalidArgumentError: If `view` is a blueprint container, title selection is invalid,
                `view` and title arguments are mixed, or the RenderApp is headless.

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

### rebuild

```python
def rebuild(self, frame: Frame) -> None
```

Mark one custom UI Frame dirty for rebuilding at the next synchronization point.

        The Frame is only a declaration handle. Dirty state belongs to this RenderApp, so repeated
        calls before `sync()` coalesce into one builder invocation.

        Raises:
            RenderClosedError: If the render app is closed.
            InvalidArgumentError: If `frame` is not managed by this RenderApp blueprint.

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

### show

```python
def show(self, view: Optional[Any] = None, *, select: bool = False, title: Optional[str] = None, include: Optional[Sequence[str]] = None, exclude: Optional[Sequence[str]] = None) -> None
```

Show one Viewer View declaration, or restore hidden Views selected by final title.

        Views are declared at construction in this RenderApp's `blueprint` and cannot be added at
        runtime. A hidden View is restored at its existing dock placement. If its runtime Entity
        was closed, the render service rebuilds the same logical View in the current tab group
        from the retained declaration. The command is sent by the next `sync()` call; ids outside
        the blueprint are ignored by the service with a logged error. Title selection only
        restores hidden live Views; it never recreates closed Views.

        Args:
            view: One View leaf. Reuse the same View leaf
                across hide/show calls so its stable ViewId is preserved.
            select: Whether to activate `view` after showing it. Defaults to False.
            title: One exact final title to restore.
            include: Full-title regular expressions to include when
                `view` is omitted. Omitted selects all live titles; an empty sequence selects none.
            exclude: Full-title regular expressions to exclude. Excludes
                always take precedence over includes.

        Raises:
            RenderClosedError: If the render app is closed.
            InvalidArgumentError: If `view` is a blueprint container, title selection is invalid,
                `view` and title arguments are mixed, or the RenderApp is headless.

### sync

```python
def sync(self, data: Any, wait: bool = False) -> None
```

Synchronize the render app backend with python data.

        This is the explicit synchronization point between the Python client loop and
        the render service. Call it at render cadence, after one or more physics steps,
        rather than from every physics step in a hot loop. Calling it more frequently than
        the service can consume frames will throttle the caller.

        Each successful call also drains service-to-client events queued since the previous
        sync call. Window input, UI events, and camera updates are only delivered to the
        Python side when sync is called often enough to consume them.

        Choice State setter calls update their Python snapshots immediately. Their latest coalesced
        element updates are submitted here, then returned by Rust through the same interaction
        stream used for user input so `is_changed()` and `on_change` follow one path.

        Args:
            data: The scene data to synchronize with the renderer.

                This argument accept following types:

                    - None: No data is provided, the render will use the last known transforms.
                    - SceneData: The scene data used to update the render. If you launched the
                      render with `repeat > 1`, the shape of the data must be `(repeat,)`.
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
