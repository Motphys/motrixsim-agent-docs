# motrixsim.Mocap

Module: [`motrixsim`](../modules/motrixsim.md)

The Mocap object represents a motion capture body in the scene. it can will participate in the
    collision and apply force to other bodies, but will not be affected by the physics simulation.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `body` | `Body` | The body associated with this mocap. |
| `model` | `SceneModel` | The scene model this mocap belongs to. |

### body

```python
body: Body
```

The body associated with this mocap.

### model

```python
model: SceneModel
```

The scene model this mocap belongs to.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `set_pose` | `(self, data: SceneData, pose: Any) -> None` | Set the pose of the mocap. |

### set_pose

```python
def set_pose(self, data: SceneData, pose: Any) -> None
```

Set the pose of the mocap.

        Args:
          data: The scene data to store the pose.
          pose: The pose to set, as a 7-element array (x, y, z, qx, qy, qz, qw).
            shape = (data.shape,7)
