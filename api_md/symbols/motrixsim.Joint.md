# motrixsim.Joint

Module: [`motrixsim`](../modules/motrixsim.md)

The Joint object represents a joint in the scene.
    
    This class provides access to the properties and state of a joint in the scene.
    It allows you to retrieve information about the joint's name, link index, number of DoF
    velocities and positions, and DoF velocity and position addresses.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `armature` | `float` | The model armature value of the joint. |
| `axis` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The motion axis of the joint. |
| `dof_pos_index` | `int` | The position DoF address of the joint. |
| `dof_vel_index` | `int` | The velocity DoF address of the joint. |
| `frictionloss` | `float` | The model friction loss value of the joint. |
| `index` | `int` | The index of the joint in the `motrixsim.SceneModel.joints`. |
| `link` | `Link` | The link this joint is attached to. |
| `link_index` | `int` | The index of the link this joint is attached to. |
| `model` | `SceneModel` | The scene model this joint belongs to. |
| `name` | `Optional[str]` | The name of the joint. |
| `num_dof_pos` | `int` | The number of position DoFs of the joint. |
| `num_dof_vel` | `int` | The number of velocity DoFs of the joint. |
| `range` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The range limits of the joint. |

### armature

```python
armature: float
```

The model armature value of the joint.

### axis

```python
axis: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The motion axis of the joint.
    
    Returns a 3-element array representing the motion axis of the joint in the
    successor body coordinate frame. This is primarily used for hinge and slide joints.
    
    Note:
        The axis is normalized automatically when the joint is created.
        For spherical joints, the axis concept doesn't apply in the same way
        as they have full rotational freedom.

### dof_pos_index

```python
dof_pos_index: int
```

The position DoF address of the joint.
    
    Return the starting index of the position DoFs.

### dof_vel_index

```python
dof_vel_index: int
```

The velocity DoF address of the joint.
    
    Return the starting index of the velocity DoFs.

### frictionloss

```python
frictionloss: float
```

The model friction loss value of the joint.

### index

```python
index: int
```

The index of the joint in the `motrixsim.SceneModel.joints`.

### link

```python
link: Link
```

The link this joint is attached to.

### link_index

```python
link_index: int
```

The index of the link this joint is attached to.

### model

```python
model: SceneModel
```

The scene model this joint belongs to.

### name

```python
name: Optional[str]
```

The name of the joint.
    
    Return the name of the joint, or `None` if not set.

### num_dof_pos

```python
num_dof_pos: int
```

The number of position DoFs of the joint.

### num_dof_vel

```python
num_dof_vel: int
```

The number of velocity DoFs of the joint.

### range

```python
range: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The range limits of the joint.
    
    Returns a 2-element array containing the lower and upper bounds of the joint range.
    Array format: [lower_bound, upper_bound]
    If the joint has no limits, returns [f32::NEG_INFINITY, f32::INFINITY].
    
    Example:
    
    .. code:: python
    
        joint.range
        # array([[-1.57,  1.57]])  # Hinge joint with ±π/2 limits

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_armature_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the armature override value from the scene data. |
| `get_dof_pos` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF positions of the joint. |
| `get_dof_vel` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF velocities of the joint. |
| `get_frictionloss_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the friction loss override value from the scene data. |
| `set_armature_override` | `(self, data: SceneData, armature: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the armature value of the joint. |
| `set_dof_pos` | `(self, data: SceneData, position: Any) -> None` | Set the DoF positions of the joint. |
| `set_dof_vel` | `(self, data: SceneData, velocity: Any) -> None` | Set the DoF velocities of the joint. |
| `set_frictionloss_override` | `(self, data: SceneData, frictionloss: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the friction loss value of the joint. |

### get_armature_override

```python
def get_armature_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the armature override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The armature override value. Shape: ``(*data.shape,)``

### get_dof_pos

```python
def get_dof_pos(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF positions of the joint.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF positions. shape = (data.shape, `num_dof_pos`)

### get_dof_vel

```python
def get_dof_vel(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF velocities of the joint.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The DoF velocities. shape = (data.shape, `num_dof_vel`)

### get_frictionloss_override

```python
def get_frictionloss_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the friction loss override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The friction loss override value. Shape: ``(*data.shape,)``

### set_armature_override

```python
def set_armature_override(self, data: SceneData, armature: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the armature value of the joint.
        
        Args:
            data: The scene data to modify.
            armature: The new armature value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the armature is negative, NaN, or infinite, the override will be ignored.

### set_dof_pos

```python
def set_dof_pos(self, data: SceneData, position: Any) -> None
```

Set the DoF positions of the joint.
        
        Args:
            data: The scene data to store the new positions.
            position: The new DoF positions. shape = (data.shape,
                `num_dof_pos`)

### set_dof_vel

```python
def set_dof_vel(self, data: SceneData, velocity: Any) -> None
```

Set the DoF velocities of the joint.
        
        Args:
            data: The scene data to store the new velocities.
            velocity: The new DoF velocities. shape = (data.shape,
                `num_dof_vel`)

### set_frictionloss_override

```python
def set_frictionloss_override(self, data: SceneData, frictionloss: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the friction loss value of the joint.
        
        Args:
            data: The scene data to modify.
            frictionloss: The new friction loss value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the value is negative, NaN, or infinite, the override will be ignored.
