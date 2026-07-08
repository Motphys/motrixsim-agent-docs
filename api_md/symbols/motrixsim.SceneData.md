# motrixsim.SceneData

Module: [`motrixsim`](../modules/motrixsim.md)

The SceneData object represents the simulation state.

    This class provides access to the dynamic state of the simulation, including joint positions,
    velocities, and other runtime data. Users can query or modify the simulation state, reset the
    scene to its initial state, and access low-level simulation data for advanced use cases. The
    state can be accessed via properties such as `qpos`, `qvel`, and via methods like `reset()`.
    For advanced control, the `low` property exposes the low-level data object.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `actuator_ctrls` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The all the actuator control values. (Get&Set) |
| `dof_pos` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The dof position array of the world. |
| `dof_vel` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The dof velocity array of the world. |
| `low` | `LowData` | The low-level data object for advanced simulation control. |
| `ndim` | `int` | The number of dimensions of the data. |
| `shape` | `tuple` | Tuple[int]: The shape of the data. |

### actuator_ctrls

```python
actuator_ctrls: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The all the actuator control values. (Get&Set)

    Array of actuator control values. Shape: ``(*data.shape, num_ctrls)``.


    Note:
        If the model is created from MJCF, the order of the control values matches the order
        of actuators in the MJCF file.

    Raises:
        TypeError: When the shape of the setted values is not invalid.

### dof_pos

```python
dof_pos: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The dof position array of the world.

    Array of DoF positions. Shape: ``(*data.shape, num_dof_pos)``

    Note:
        The dof_pos array contains position coordinates for all degrees of freedom in the
        simulation, with format varying by joint type:

            - **Floating base/free body**: 7 elements [tx, ty, tz, qx, qy, qz, qw]
            - **Ball joint**: 4 elements [qx, qy, qz, qw] for quaternion rotation
            - **Hinge joint**: 1 element for angular position
            - **Slide joint**: 1 element for linear position

        Elements are concatenated in order:
        [floating_base_dofs..., joint1_dofs..., joint2_dofs..., ...]

### dof_vel

```python
dof_vel: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The dof velocity array of the world.

    Array of DoF velocities. Shape: ``(*data.shape, num_dof_vel)``.

### low

```python
low: LowData
```

The low-level data object for advanced simulation control.

    Note:
        Only modify the low-level data if you understand the implications.
        Incorrect modifications may lead to unstable simulation behavior.

### ndim

```python
ndim: int
```

The number of dimensions of the data.

### shape

```python
shape: tuple
```

Tuple[int]: The shape of the data.

    If the data is batched, the shape is (batch_size,). If not batched, the shape is ().

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, index: Any) -> SceneData` | Args: |
| `__new__` | `(cls, model: SceneModel, batch: Sequence[int] = []) -> SceneData` | Create a new SceneData object. |
| `get` | `(self, index: Any) -> SceneData` | Get sub-data by index. Alias to `__getitem__` |
| `reset` | `(self, model: SceneModel) -> None` | Reset the scene data with the given model. |
| `set_dof_pos` | `(self, dof_pos: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], model: SceneModel) -> None` | Set the dof position for the whole world data. |
| `set_dof_vel` | `(self, dof_vel: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Set the dof velocity for the whole world data. |

### __getitem__

```python
def __getitem__(self, index: Any) -> SceneData
```

Args:
            index: The index to select.

### __new__

```python
def __new__(cls, model: SceneModel, batch: Sequence[int] = []) -> SceneData
```

Create a new SceneData object.

        Args:
            model: The scene model.
            batch: If provided, a batched SceneData will be created. It is
            useful when you want to simulate multiple independent instances of the same model in
            parallel.

        Returns:
            SceneData: The created scene data object.

### get

```python
def get(self, index: Any) -> SceneData
```

Get sub-data by index. Alias to `__getitem__`

        Args:
            index: The index to select. Following types are
        supported:
                 - int: Select a single element. Raise error if the data has no batch dimension.
                 - ndarray[bool]: Select multiple elements based on a boolean mask.
                 - DisjointIndices: Select multiple non-contiguous elements.

### reset

```python
def reset(self, model: SceneModel) -> None
```

Reset the scene data with the given model.

        Reinitializes all simulation state variables using the provided model.

        Args:
            model: The scene model to reset the data with.

### set_dof_pos

```python
def set_dof_pos(self, dof_pos: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], model: SceneModel) -> None
```

Set the dof position for the whole world data.

        Args:
            dof_pos: The dof position array to set. If Shape: ``(*data.shape,
                num_dof_pos)``, each data will use the corresponding slice. If Shape:
                ``(num_dof_pos,)``, all data will use the same dof position.
            model: The scene model to validate the dof position.
        Raises:
           Exception: When the dof position data is invalid.(e.g. quaternion not normalized)

        Note:
            The dof_pos array must follow the same format as the getter method:

                - **Floating base/free body**: 7 elements [tx, ty, tz, qx, qy, qz, qw]
                - **Ball joint**: 4 elements [qx, qy, qz, qw] for quaternion rotation
                - **Hinge joint**: 1 element for angular position
                - **Slide joint**: 1 element for linear position

            Elements should be concatenated in order:
            [floating_base_dofs..., joint1_dofs..., joint2_dofs..., ...]

### set_dof_vel

```python
def set_dof_vel(self, dof_vel: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Set the dof velocity for the whole world data.

        Args:
            dof_vel: The dof velocity array to set. Shape: ``(*data.shape,
        num_dof_vel)``.
