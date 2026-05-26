# motrixsim.Actuator

Module: [`motrixsim`](../modules/motrixsim.md)

The base Actuator class provides access to common actuator properties and control.
    
    All actuator types share the same underlying force generation equation:
    
        force = gain * activation + bias - stiffness * position - damping * velocity
    
    where ``activation`` is derived from the control signal (possibly filtered by activation
    dynamics), and ``position`` / ``velocity`` are the current state of the actuator target
    (e.g., joint angle and joint velocity).
    
    Typed subclasses provide type-specific parameter override methods:

## Properties

| Name | Type | Description |
|------|------|-------------|
| `ctrl_range` | `Optional[list[float]]` | Optional[Tuple[float, float]]: The control range of the actuator. |
| `index` | `int` | The index of the actuator in the simulation world. |
| `name` | `Optional[str]` | The name of the actuator. |
| `target_name` | `str` | The name of the actuator target. (e.g., joint name, tendon name). |
| `target_type` | `str` | The type of the actuator target. |
| `typ` | `str` | The type of the actuator. |

### ctrl_range

```python
ctrl_range: Optional[list[float]]
```

Optional[Tuple[float, float]]: The control range of the actuator.
    
    Returns None if not set.

### index

```python
index: int
```

The index of the actuator in the simulation world.

### name

```python
name: Optional[str]
```

The name of the actuator.
    
    Return "None" if not set.

### target_name

```python
target_name: str
```

The name of the actuator target. (e.g., joint name, tendon name).

### target_type

```python
target_type: str
```

The type of the actuator target.
    
    valid values are:
    
    - "floating_base": For floating base actuators.
    - "joint": For joint actuators.
    - "tendon": For tendon actuators.

### typ

```python
typ: str
```

The type of the actuator.
    
    valid values are:
    
    - "general":  General actuator.
    - "position": Position servo. The ctrl represents the target position
    - "velocity": Velocity servo. The ctrl represents the target velocity
    - "motor": The ctrl represents the torque or force

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_ctrl` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the control value of the actuator. |
| `set_ctrl` | `(self, data: SceneData, ctrl: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Set the control value of the actuator. |

### get_ctrl

```python
def get_ctrl(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the control value of the actuator.
        
        Args:
            data: The scene data.
        Returns:
            NDArray[float]: The current control value of the actuator. Shape: ``(*data.shape, )``

### set_ctrl

```python
def set_ctrl(self, data: SceneData, ctrl: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Set the control value of the actuator.
        
        Args:
            data: The scene data to store the control value.
            ctrl: The control value to set.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
