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
