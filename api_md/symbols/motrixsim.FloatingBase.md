# motrixsim.FloatingBase

Module: [`motrixsim`](../modules/motrixsim.md)

The FloatingBase object represents a floating base in the scene.
    
    This class provides access to the properties and state of a floating base in the scene.
    It allows you to retrieve information about the base's name, DoF velocities and positions,
    and to set its world translation and rotation.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `dof_pos_indices` | `list[int]` | List[int]: The DoF position indices of the floating base. size = 7. |
| `dof_pos_start` | `int` | The DoF position address of the floating base in the |
| `dof_vel_indices` | `list[int]` | List[int]: The DoF velocity indices of the floating base. size = 6. |
| `dof_vel_start` | `int` | The DoF velocity address of the floating base in the |
| `index` | `int` | The index of the floatingbase in the `motrixsim.SceneModel.floating_bases`. |
| `model` | `SceneModel` | The scene model this floating base belongs to. |
| `name` | `Optional[str]` | The name of the floating base. |

### dof_pos_indices

```python
dof_pos_indices: list[int]
```

List[int]: The DoF position indices of the floating base. size = 7.

### dof_pos_start

```python
dof_pos_start: int
```

The DoF position address of the floating base in the
        `motrixsim.SceneData.dof_pos`.

### dof_vel_indices

```python
dof_vel_indices: list[int]
```

List[int]: The DoF velocity indices of the floating base. size = 6.

### dof_vel_start

```python
dof_vel_start: int
```

The DoF velocity address of the floating base in the
        `motrixsim.SceneData.dof_vel`.

### index

```python
index: int
```

The index of the floatingbase in the `motrixsim.SceneModel.floating_bases`.

### model

```python
model: SceneModel
```

The scene model this floating base belongs to.

### name

```python
name: Optional[str]
```

The name of the floating base.
    
    Return `None` if not set.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_dof_pos` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF positions of the floating base. |
| `get_dof_vel` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF velocities of the floating base. |
| `get_global_angular_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Extract the world angular velocity of the floating base from the dof velocity array. |
| `get_global_linear_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Extract the world linear velocity of the floating base from the dof velocity array. |
| `get_local_angular_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Extract the local angular velocity of the floating base from the dof velocity array. |
| `get_rotation` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Extract the world rotation of the floating base from the dof position array. |
| `get_translation` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Extract the world translation of the floating base from the dof position array. |
| `set_global_angular_velocity` | `(self, data: SceneData, vel: Any) -> None` | Set the global angular velocity of the floating base to dof velocity array directly. |
| `set_global_linear_velocity` | `(self, data: SceneData, vel: Any) -> None` | Set the global linear velocity of the floating base to dof velocity array directly. |
| `set_local_angular_velocity` | `(self, data: SceneData, vel: Any) -> None` | Set the local angular velocity of the floating base to dof velocity array directly. |
| `set_rotation` | `(self, data: SceneData, quat: Any) -> None` | Set the world rotation of the floating base. |
| `set_translation` | `(self, data: SceneData, translation: Any) -> None` | Set the world translation of the floating base. |

### get_dof_pos

```python
def get_dof_pos(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF positions of the floating base.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF positions with (x,y,z, i,j,k,w) format. shape = (data.shape, 7).

### get_dof_vel

```python
def get_dof_vel(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF velocities of the floating base.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF velocities with (vx,vy,vz wx,wy,wz) format. shape = (data.shape,
            6).

### get_global_angular_velocity

```python
def get_global_angular_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Extract the world angular velocity of the floating base from the dof velocity array.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The world angular velocity. shape = (data.shape, 3)

### get_global_linear_velocity

```python
def get_global_linear_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Extract the world linear velocity of the floating base from the dof velocity array.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The world linear velocity. shape = (data.shape, 3)

### get_local_angular_velocity

```python
def get_local_angular_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Extract the local angular velocity of the floating base from the dof velocity array.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray(float): The local angular velocity. shape = (data.shape, 3)

### get_rotation

```python
def get_rotation(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Extract the world rotation of the floating base from the dof position array.
        
        Args:
            data: The scene data.
        
        Returns:
            NDArray[float]: A quaternion representing the rotation in the format `[i, j, k, w]`.

### get_translation

```python
def get_translation(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Extract the world translation of the floating base from the dof position array.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The world translation. shape = (data.shape, 3)

### set_global_angular_velocity

```python
def set_global_angular_velocity(self, data: SceneData, vel: Any) -> None
```

Set the global angular velocity of the floating base to dof velocity array directly.
        
        Args:
            data: The scene data to store the velocity.
            vel: The global angular velocity to set. shape = (data.shape, 3)
        
        Note:
            This method only updates the dof velocity array.

### set_global_linear_velocity

```python
def set_global_linear_velocity(self, data: SceneData, vel: Any) -> None
```

Set the global linear velocity of the floating base to dof velocity array directly.
        
        Args:
            data: The scene data to store the velocity.
            vel: The world linear velocity to set. shape = (data.shape, 3)
        
        Note:
          This method only updates the dof velocity array.

### set_local_angular_velocity

```python
def set_local_angular_velocity(self, data: SceneData, vel: Any) -> None
```

Set the local angular velocity of the floating base to dof velocity array directly.
        
        Args:
            data: The scene data to store the velocity.
            vel (ArrayLink(float)): The local angular velocity, shape = (data.shape, 3).
        
        Note:
            This method only updates the dof velocity array.

### set_rotation

```python
def set_rotation(self, data: SceneData, quat: Any) -> None
```

Set the world rotation of the floating base.
        
        Args:
            data: The scene data to store the rotation.
            quat: The quaternion [i, j, k, w]. shape = (data.shape, 4).
        
        Notes:
            This function only updates the DoF position of the floating base. The actual rotation
            is updated through the forward kinematic phase.

### set_translation

```python
def set_translation(self, data: SceneData, translation: Any) -> None
```

Set the world translation of the floating base.
        
        Args:
            data: The scene data to store the translation.
            translation: The translation [x, y, z]. shape = (data.shape, 3).
        
        Notes:
            This function only updates the DoF position of the floating base. The actual
            translation of links is updated through the forward kinematic phase.
