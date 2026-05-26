# motrixsim.Link

Module: [`motrixsim`](../modules/motrixsim.md)

The Link object represents a kinematic link in the scene.
    
    This class provides access to the properties and state of a kinematic link in the scene.
    It allows you to retrieve information about the link's name, index, joint indices, number of
    joints, and the joints associated with the link.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `center_of_mass` | `numpy.typing.NDArray[numpy.float32]` | Get the center of mass of the link in the link local frame. |
| `index` | `int` | The index of the link in the `motrixsim.SceneModel.links`. |
| `joint_indices` | `list[int]` | The joint indices of this link in the `motrixsim.SceneModel.joints`. |
| `mass` | `float` | Get the mass of the link in the model. |
| `model` | `SceneModel` | The scene model that this link belongs to. |
| `name` | `Optional[str]` | The name of the link. Must be unique within the scene. |
| `num_joints` | `int` | The number of joints associated with this link. |

### center_of_mass

```python
center_of_mass: numpy.typing.NDArray[numpy.float32]
```

Get the center of mass of the link in the link local frame.
    
    Returns:
        NDArray[float]: shape = (3,). The center of mass position

### index

```python
index: int
```

The index of the link in the `motrixsim.SceneModel.links`.

### joint_indices

```python
joint_indices: list[int]
```

The joint indices of this link in the `motrixsim.SceneModel.joints`.
    
    Returns:
        List[int]: The size of the list must be equal to `num_joints`

### mass

```python
mass: float
```

Get the mass of the link in the model.
    
    Returns:
        Real: The mass of the link.

### model

```python
model: SceneModel
```

The scene model that this link belongs to.

### name

```python
name: Optional[str]
```

The name of the link. Must be unique within the scene.
    
    Returns:
        Optional[str]: The name of the link, or "None" if not set.

### num_joints

```python
num_joints: int
```

The number of joints associated with this link.
    
    Returns:
        int: number of joints associated with this link.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `add_external_force` | `(self, data: SceneData, force: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], point: Optional[numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]] = None, local: bool = True) -> None` | Add an external force to the link. |
| `add_external_torque` | `(self, data: SceneData, torque: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], local: bool = True) -> None` | Add an external torque to the link. |
| `get_angular_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world angular velocity of the link. |
| `get_center_of_mass_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the center of mass override of the link in the link local frame. |
| `get_joint` | `(self, index: int) -> Optional[Joint]` | Get the joint at the specified index if the link has multiple joints. |
| `get_linear_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world linear velocity of the link. |
| `get_mass_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the overrided mass of the link in the scene data. |
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world pose of the link. |
| `get_position` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world position of the link. |
| `get_rotation` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world rotation of the link as a quaternion (i, j, k, w). |
| `get_rotation_mat` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world rotation matrix of the link. |
| `joints` | `(self) -> list[Joint]` | The joints associated with this link. |
| `set_center_of_mass_override` | `(self, data: SceneData, center_of_mass: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the center of mass of the link. |
| `set_mass_override` | `(self, data: SceneData, mass: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the mass of the link. |

### add_external_force

```python
def add_external_force(self, data: SceneData, force: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], point: Optional[numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]] = None, local: bool = True) -> None
```

Add an external force to the link.
        
        Args:
            data: The scene data to modify.
            force: The force vector.
                - Shape: ``(*data.shape, 3)``: Per-batch force vectors
            point: Application point.
                - Shape: ``(*data.shape, 3)``: Per-batch points
            local: Whether the force and point are in local coordinates. Default: True.
        
        Note:
            The force is applied at the specified point in link coordinates.
            If point is None, force is applied at the link's center of mass.
            Forces applied to mocap-type links will be ignored.

### add_external_torque

```python
def add_external_torque(self, data: SceneData, torque: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], local: bool = True) -> None
```

Add an external torque to the link.
        
        Args:
            data: The scene data to modify.
            torque: The torque vector.
                - Shape: ``(*data.shape, 3)``: Per-batch torque vectors
            local: Whether the torque is in local coordinates. Default: True.
        
        Note:
            Torques applied to mocap-type links will be ignored.

### get_angular_velocity

```python
def get_angular_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world angular velocity of the link.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3)``. The last axis is the angular velocity with
                `[wx, wy, wz]` format.

### get_center_of_mass_override

```python
def get_center_of_mass_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the center of mass override of the link in the link local frame.
        
        Args:
            data: The scene data to query.
        Returns:
           NDArray[float]: Shape: ``(*data.shape, 3)``. The center of mass override value.

### get_joint

```python
def get_joint(self, index: int) -> Optional[Joint]
```

Get the joint at the specified index if the link has multiple joints.
        
        Args:
            index: The local index of the joint.
        
        Returns:
            Optional[Joint]: The joint object, or "None" if not found.

### get_linear_velocity

```python
def get_linear_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world linear velocity of the link.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3)``. The last axis is the linear velocity with
                `[vx, vy, vz]` format.

### get_mass_override

```python
def get_mass_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the overrided mass of the link in the scene data.
        
        Args:
            data: The scene data to query.
        Returns:
           NDArray[float]: shape = (1,). The mass override value.

### get_pose

```python
def get_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world pose of the link.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 7)``. Each pose is represented as a 7 elements
                with `[x, y, z, i, j, k, w]` format.

### get_position

```python
def get_position(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world position of the link.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3)``.

### get_rotation

```python
def get_rotation(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world rotation of the link as a quaternion (i, j, k, w).
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, 4)`.

### get_rotation_mat

```python
def get_rotation_mat(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world rotation matrix of the link.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, 3, 3)`.

### joints

```python
def joints(self) -> list[Joint]
```

The joints associated with this link.
        
        Returns:
            List[Joint]: A list of joint objects.

### set_center_of_mass_override

```python
def set_center_of_mass_override(self, data: SceneData, center_of_mass: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the center of mass of the link.
        
        Args:
            data: The scene data to modify.
            center_of_mass: The new center of mass.
                - Shape (3,): Single center of mass value applied to all batches
                - Shape: ``(*data.shape, 3)``: Per-batch center of mass vectors
        
        Note:
            If the center_of_mass components are not finite (NaN or infinity), or the link is
            mocap type, or the link is fixed to world, the override will be ignored.

### set_mass_override

```python
def set_mass_override(self, data: SceneData, mass: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the mass of the link.
        
        Args:
            data: The scene data to modify.
            mass: The new mass.
                - Shape (): Single mass value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch mass values
        
        Note:
            If the mass is non-positive or the link is mocap type, or the link is fixed to world,
            the override will be ignored.
