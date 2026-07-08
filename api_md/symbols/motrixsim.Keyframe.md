# motrixsim.Keyframe

Module: [`motrixsim`](../modules/motrixsim.md)

The Keyframe object represents a keyframe in the scene.

    This class provides access to the properties of a keyframe, including
    its name, simulation time, joint positions, velocities, and control values.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `ctrl` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The actuator control values of the keyframe. |
| `dof_pos` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The dof positions of the keyframe. |
| `dof_vel` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The joint velocities of the keyframe. |
| `index` | `int` | The index of the keyframe in the keyframe list. |
| `model` | `SceneModel` | The scene model this keyframe belongs to. |
| `name` | `Optional[str]` | The name of the keyframe, or `None` if not set. |
| `time` | `Optional[float]` | The simulation time of the keyframe, or `None` if not set. |

### ctrl

```python
ctrl: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The actuator control values of the keyframe.

    Returns a numpy array with shape (num_actuators,) containing the actuator
    control values for all actuators in the scene.

### dof_pos

```python
dof_pos: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The dof positions of the keyframe.

    Returns a numpy array with shape (num_dof_pos,) containing the dof positions
    for all degrees of freedom in the scene.

### dof_vel

```python
dof_vel: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The joint velocities of the keyframe.

    Returns a numpy array with shape (num_dof_vel,) containing the joint velocities
    for all degrees of freedom in the scene.

### index

```python
index: int
```

The index of the keyframe in the keyframe list.

### model

```python
model: SceneModel
```

The scene model this keyframe belongs to.

### name

```python
name: Optional[str]
```

The name of the keyframe, or `None` if not set.

### time

```python
time: Optional[float]
```

The simulation time of the keyframe, or `None` if not set.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `apply` | `(self, data: SceneData) -> None` | Apply the keyframe to scene data. |

### apply

```python
def apply(self, data: SceneData) -> None
```

Apply the keyframe to scene data.

        Args:
            data: Scene data to apply the keyframe to.

        Note:
            This method does NOT automatically call `forward_kinematic`. Users should
            call `model.forward_kinematic(data)` after applying the keyframe if they
            need to update the scene transforms (e.g., for visualization or getting
            correct link poses).

        Example:

        .. code:: python

            model = motrixsim.load_model("scene.xml")
            data = motrixsim.SceneData(model)
            # Apply first keyframe
            model.keyframes[0].apply(data)
            model.forward_kinematic(data)
