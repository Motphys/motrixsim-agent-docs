# motrixsim.render.RenderWidgets

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

Widgets module for creating UI widgets in the render window.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `clear` | `(self) -> None` | Remove all widgets from the render window. |
| `create_camera_viewport` | `(self, camera: Camera, layout: Optional[Layout] = None, sim_world_index: int = 0) -> CameraViewport` | Create a camera viewport widget in the render window. |
| `create_image_widget` | `(self, image: Image, layout: Optional[Layout] = None) -> ImageWidget` | Create an image widget in the render window. |

### clear

```python
def clear(self) -> None
```

Remove all widgets from the render window.

        Note:
            Despawns every widget previously created on this render app (camera
            viewports, image widgets). Useful when reusing a single render app
            across scenes, to drop the previous scene's overlays.

### create_camera_viewport

```python
def create_camera_viewport(self, camera: Camera, layout: Optional[Layout] = None, sim_world_index: int = 0) -> CameraViewport
```

Create a camera viewport widget in the render window.

        Note:
            This creates a camera viewport overlay that displays the output of a sensor camera.
            The layout parameters accept multiple formats:

                - String: "50px" for pixels, "50%" for percentage, "auto" for automatic
                - Number: Interpreted as pixels (e.g., 50 = 50px)

        Args:
            camera: The camera object to display in the viewport.
            layout: The layout configuration for the viewport. If None,
                uses default layout (50px from top-left with 200x200 size).
            sim_world_index: The index of the simulation world. Default is 0.

        Example:

        .. code:: python

            renderer = motrixsim.render.RenderApp()
            renderer.launch(model)
            cameras = model.cameras
            # Create viewport with default layout
            vp = renderer.widgets.create_camera_viewport(cameras[0])
            # Create viewport with custom layout
            layout = motrixsim.render.Layout(left=50, top=50, width=400, height=300)
            vp = renderer.widgets.create_camera_viewport(cameras[0], layout=layout)
            # Create viewport with percentage-based layout
            layout = motrixsim.render.Layout(
                left="10%", top="10%", width="50%", height="50%"
            )
            vp = renderer.widgets.create_camera_viewport(cameras[1], sim_world_index=1,
                layout=layout)
            # Access camera properties
            print(f"Camera name: {vp.camera.name}")

### create_image_widget

```python
def create_image_widget(self, image: Image, layout: Optional[Layout] = None) -> ImageWidget
```

Create an image widget in the render window.

        Note:
            This creates an image widget overlay that displays the specified image.
            The layout parameters accept multiple formats:
            - String: "50px" for pixels, "50%" for percentage, "auto" for automatic
            - Number: Interpreted as pixels (e.g., 50 = 50px)

        Args:
            image: The image object to display in the widget.
            layout: The layout configuration for the widget. If None,
                uses default layout (0px from top-left with automatic size).

        Example:

        .. code:: python

            renderer = motrixsim.render.RenderApp()
            renderer.launch(model)
            # Load an image
            img = motrixsim.render.Image.from_file("path/to/image.png")
            # Create widget with default layout
            widget = renderer.widgets.create_image_widget(img)
            # Create widget with custom layout
            layout = motrixsim.render.Layout(left=100, top=100, width=200, height=200)
            widget = renderer.widgets.create_image_widget(img, layout=layout)
            # Update the widget
            widget.update(layout=new_layout)
