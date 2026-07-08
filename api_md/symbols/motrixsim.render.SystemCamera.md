# motrixsim.render.SystemCamera

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `active` | `bool` | Whether the system camera is active. |
| `pose` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The global pose of the system camera as a 7 element array with the format |

### active

```python
active: bool
```

Whether the system camera is active.

### pose

```python
pose: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The global pose of the system camera as a 7 element array with the format
    `[pos_x, pos_y, pos_z, rot_i, rot_j, rot_k, rot_w]`

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `capture` | `(self) -> CaptureTask` | Request a capture from the system camera. |
| `set_pose` | `(self, position: Optional[Sequence[float]] = None, rotation: Optional[Sequence[float]] = None) -> None` | Set the global pose of the system camera. |
| `set_view` | `(self, lookat: Sequence[float], distance: float, elevation: float, azimuth: float) -> None` | Set the system camera from orbit/look-at view parameters. |

### capture

```python
def capture(self) -> CaptureTask
```

Request a capture from the system camera.

        Returns:
            CaptureTask: An async task that can be used to check the capture state and get the
            captured image.

### set_pose

```python
def set_pose(self, position: Optional[Sequence[float]] = None, rotation: Optional[Sequence[float]] = None) -> None
```

Set the global pose of the system camera.

        Args:
            position: Optional world position `[x, y, z]`.
            rotation: Optional world rotation quaternion `[i, j, k, w]`.

### set_view

```python
def set_view(self, lookat: Sequence[float], distance: float, elevation: float, azimuth: float) -> None
```

Set the system camera from orbit/look-at view parameters.

        The camera looks at `lookat` from the given orbit distance and angles. The renderer applies
        the corresponding system camera transform and synchronizes the interactive orbit camera
        state, so subsequent mouse drags continue from the same view. This camera is the renderer
        system camera, not a model-defined MJCF camera.

        Args:
            lookat: World-space target point `[x, y, z]`.
            distance: Distance from the camera to `lookat`.
            elevation: Elevation angle in degrees. Negative values place the camera above
                `lookat` and look down; positive values place it below `lookat` and look up.
            azimuth: Azimuth angle around the world Z axis in degrees.
