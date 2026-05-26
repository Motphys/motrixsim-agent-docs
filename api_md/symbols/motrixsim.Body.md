# motrixsim.Body

Module: [`motrixsim`](../modules/motrixsim.md)

The Body object represents a rigid body in the scene.
    
    This class provides access to the properties and state of a rigid body in the simulation.
    It allows you to retrieve information about the body's name, floating base, pose, and DoF
    positions and velocities.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `actuators` | `list[Actuator]` | List[Actuator]: The list of actuators associated with this body. |
| `base_link` | `Link` | The base link of this body. |
| `floatingbase` | `Optional[FloatingBase]` | The floating base object. |
| `index` | `int` |  |
| `is_mocap` | `bool` | Whether the body is a mocap (kinematic) body. |
| `mocap` | `Optional[Mocap]` | Convert this body to a mocap object if it is a mocap body. |
| `model` | `SceneModel` |  |
| `name` | `Optional[str]` | The name of the body. |
| `num_actuators` | `int` | The number of actuators associated with this body. |
| `num_joint_dof_pos` | `int` | The number of DoF positions of all joints on the body. |
| `num_joint_dof_vel` | `int` | The number of DoF velocities of all joints on the body. |
| `num_joints` | `int` | The number of joints that belong to this body. |
| `num_links` | `int` | The number of links that belong to this body. |

### actuators

```python
actuators: list[Actuator]
```

List[Actuator]: The list of actuators associated with this body.
    
    Returns an empty list if the body has no actuators.
    
    Note:
        Actuators are associated with a body through the joints on the body.
        Each actuator targets a specific joint, and this method returns all
        actuators that target joints belonging to this body.

### base_link

```python
base_link: Link
```

The base link of this body.

### floatingbase

```python
floatingbase: Optional[FloatingBase]
```

The floating base object.
    
    Return `None` if not present.
    
    Note:
      In mjcf, a body is free moving if it has `<freejoint>`

### index

```python
index: int
```

### is_mocap

```python
is_mocap: bool
```

Whether the body is a mocap (kinematic) body.
    
    Return True if the body has no joints and fixed to the world, `False` otherwise.

### mocap

```python
mocap: Optional[Mocap]
```

Convert this body to a mocap object if it is a mocap body.
    
    Returns:
        Optional[PyMocap]: The mocap object if this body is a mocap, `None` otherwise.

### model

```python
model: SceneModel
```

### name

```python
name: Optional[str]
```

The name of the body.
    
    Return `None` if not present.

### num_actuators

```python
num_actuators: int
```

The number of actuators associated with this body.

### num_joint_dof_pos

```python
num_joint_dof_pos: int
```

The number of DoF positions of all joints on the body.
    
    Note:
       If the body has floating base, the floating base DoF positions are NOT included

### num_joint_dof_vel

```python
num_joint_dof_vel: int
```

The number of DoF velocities of all joints on the body.
    
    Note:
        If the body has floating base, the floating base DoF velocities are NOT included

### num_joints

```python
num_joints: int
```

The number of joints that belong to this body.
    
    Note:
        The `<freejoint>` is not counted as a joint in motrixsim but a floating base.

### num_links

```python
num_links: int
```

The number of links that belong to this body.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_dof_pos_indices` | `(self, include_floatingbase: bool = True) -> numpy.typing.NDArray[numpy.uint32]` | Get the indices of the DoF positions of the body. |
| `get_dof_vel_indices` | `(self, include_floatingbase: bool = True) -> numpy.typing.NDArray[numpy.uint32]` | Get the indices of the DoF velocities of the body. |
| `get_joint_dof_pos` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF positions of all joints on the body. |
| `get_joint_dof_vel` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF velocities of all joints on the body. |
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world pose of the body. |
| `get_position` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world position of the body. |
| `get_rotation` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world rotation of the body as a quaternion. |
| `get_rotation_mat` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world rotation of the body as a rotation matrix. |
| `set_actuator_ctrls` | `(self, data: SceneData, ctrls: Any) -> None` | Set the control values for all actuators on this body. |
| `set_dof_pos` | `(self, data: SceneData, dof_pos: Any, include_floatingbase: bool = True) -> None` | Set the DoF positions of the body. |
| `set_dof_vel` | `(self, data: SceneData, dof_vel: Any, include_floatingbase: bool = True) -> None` | Set the DoF velocities of the body. |

### get_dof_pos_indices

```python
def get_dof_pos_indices(self, include_floatingbase: bool = True) -> numpy.typing.NDArray[numpy.uint32]
```

Get the indices of the DoF positions of the body.
        
        Args:
            include_floatingbase: Whether to include the floating base DoF positions
                indices. If `False`, only the joint DoF positions indices are returned.
        Returns:
           NDArray[int]: The DoF position indices. if include_floatingbase is true, shape =
                (`num_joint_dof_pos` + 6,), else shape = (`num_joint_dof_pos`,).

### get_dof_vel_indices

```python
def get_dof_vel_indices(self, include_floatingbase: bool = True) -> numpy.typing.NDArray[numpy.uint32]
```

Get the indices of the DoF velocities of the body.
        
        Args:
            include_floatingbase: Whether to include the floating base DoF velocities
                indices. If `False`, only the joint DoF velocities indices are returned.
        Returns:
           NDArray[int]: The DoF velocity indices. if include_floatingbase is true, shape =
                (`num_joint_dof_vel` + 6,), else shape = (`num_joint_dof_vel`,).

### get_joint_dof_pos

```python
def get_joint_dof_pos(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF positions of all joints on the body.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF positions. shape = (`*data.shape`, `num_joint_dof_pos`).
        
        Note:
            If the body has floating base, the floating base DoF positions are NOT included.

### get_joint_dof_vel

```python
def get_joint_dof_vel(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF velocities of all joints on the body.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF velocities. shape = (`*data.shape`,:meth:
                `body.num_joint_dof_vel`).
        
        Note:
            If the body has floating base, the floating base DoF velocities are NOT included.

### get_pose

```python
def get_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world pose of the body.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 7)``.  Each pose is a 7-element array with `[x,
        y,     z, i, j, k, w]`.

### get_position

```python
def get_position(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world position of the body.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3)``.

### get_rotation

```python
def get_rotation(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world rotation of the body as a quaternion.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 4)``. Each rotation is a 4-element array with
        `[i,     j, k, w]`.

### get_rotation_mat

```python
def get_rotation_mat(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world rotation of the body as a rotation matrix.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3, 3)``.

### set_actuator_ctrls

```python
def set_actuator_ctrls(self, data: SceneData, ctrls: Any) -> None
```

Set the control values for all actuators on this body.
        
        Args:
            data: The scene data to modify.
            ctrls: The control values to set. Shape = `(len(body.actuators),)`.
                If the data has batch dimension, `ctrls` must have the same shape as the data.
        
        Note:
            The number of control values must match the number of actuators on the body.
            Use `body.actuators` to get the list of actuators and their count.
        
        Example:
        
        .. code:: python
        
            # For a body with 3 actuators:
            body.set_actuator_ctrls(data, [1.0, 0.5, -0.3])  # Set controls for all 3 actuators

### set_dof_pos

```python
def set_dof_pos(self, data: SceneData, dof_pos: Any, include_floatingbase: bool = True) -> None
```

Set the DoF positions of the body.
        
        Args:
            data: The scene data to modify.
            dof_pos: The DoF positions to set. Shape = `(num_joint_dof_pos + 7,)`
                if `include_floatingbase` is `True`, else shape = (num_joint_dof_pos,).
            include_floatingbase: Whether the provided `dof_pos` includes the floating base
              DoF positions. If `True`, the first 7 elements of `dof_pos` are treated as the
              floating base DoF positions.

### set_dof_vel

```python
def set_dof_vel(self, data: SceneData, dof_vel: Any, include_floatingbase: bool = True) -> None
```

Set the DoF velocities of the body.
        
        Args:
            data: The scene data to modify.
            dof_vel: The DoF velocities to set. Shape = (`num_joint_dof_vel`
                + 6,) if `include_floatingbase` is `True`, else shape =(`num_joint_dof_vel`,).
            include_floatingbase: Whether the provided `dof_vel` includes the floating base
              DoF velocities. If `True`, the first 6 elements of `dof_vel` are treated as the
              floating base DoF velocities.
