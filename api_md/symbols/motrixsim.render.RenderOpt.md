# motrixsim.render.RenderOpt

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

The RenderOpt object represents the options of the render app.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `is_left_panel_vis` | `(self) -> bool` | Check if the left panel is visible. |
| `is_lidar_point_vis` | `(self) -> bool` | Check whether lidar / raycast sensor point clouds are rendered. |
| `set_group_vis` | `(self, group: int, visible: bool) -> None` | Set the visibility of a geometry group. |
| `set_left_panel_vis` | `(self, enabled: bool) -> None` | Set the visibility of the left panel. |
| `set_lidar_point_vis` | `(self, visible: bool) -> None` | Set whether lidar / raycast sensor point clouds are rendered. |

### is_left_panel_vis

```python
def is_left_panel_vis(self) -> bool
```

Check if the left panel is visible.

        Returns:
            bool: True if the left panel is visible, False otherwise.

### is_lidar_point_vis

```python
def is_lidar_point_vis(self) -> bool
```

Check whether lidar / raycast sensor point clouds are rendered.

        Returns:
            bool: True if lidar point cloud visualization is enabled, False otherwise.

### set_group_vis

```python
def set_group_vis(self, group: int, visible: bool) -> None
```

Set the visibility of a geometry group.

        Args:
            group: The geometry group index (0-MAX_GROUP_SIZE-1).
            visible: True to make the group visible, False to hide it.

        Raises:
            Exception: If group index is out of valid range.

### set_left_panel_vis

```python
def set_left_panel_vis(self, enabled: bool) -> None
```

Set the visibility of the left panel.

        Args:
            enabled: True to show the left panel, False to hide it.

### set_lidar_point_vis

```python
def set_lidar_point_vis(self, visible: bool) -> None
```

Set whether lidar / raycast sensor point clouds are rendered.

        Streams the simulation's lidar / raycast sensor data to the render service and draws the
        resulting point clouds. Can be toggled at runtime; disabled by default.

        Args:
            visible: True to stream and show lidar point clouds, False to stop.
