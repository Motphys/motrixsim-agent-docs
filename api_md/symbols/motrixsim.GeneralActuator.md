# motrixsim.GeneralActuator

Module: [`motrixsim`](../modules/motrixsim.md)

General actuator (MJCF ``<general>``).
    
    MJCF parameter mapping (assumes ``gaintype="fixed"`` and ``biastype="affine"``):
    
    - ``gainprm[0]`` -> gain
    - ``biasprm[0]`` -> bias
    - ``-biasprm[1]`` -> stiffness (sign is negated because the force equation subtracts stiffness *
      position)
    - ``-biasprm[2]`` -> damping (sign is negated because the force equation subtracts damping *
      velocity)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_bias_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the bias override value from the scene data. |
| `get_damping_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the damping override value from the scene data. |
| `get_gain_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the gain override value from the scene data. |
| `get_stiffness_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the stiffness override value from the scene data. |
| `set_bias_override` | `(self, data: SceneData, bias: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the bias value of the actuator. |
| `set_damping_override` | `(self, data: SceneData, damping: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the damping value of the actuator. |
| `set_gain_override` | `(self, data: SceneData, gain: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the gain value of the actuator. |
| `set_stiffness_override` | `(self, data: SceneData, stiffness: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the stiffness value of the actuator. |

### get_bias_override

```python
def get_bias_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the bias override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The bias value. Shape: ``(*data.shape,)``

### get_damping_override

```python
def get_damping_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the damping override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The damping value. Shape: ``(*data.shape,)``

### get_gain_override

```python
def get_gain_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the gain override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The gain value. Shape: ``(*data.shape,)``

### get_stiffness_override

```python
def get_stiffness_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the stiffness override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The stiffness value. Shape: ``(*data.shape,)``

### set_bias_override

```python
def set_bias_override(self, data: SceneData, bias: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the bias value of the actuator.
        
        Args:
            data: The scene data to modify.
            bias: The new bias value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the bias is NaN or infinite, the override will be ignored.

### set_damping_override

```python
def set_damping_override(self, data: SceneData, damping: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the damping value of the actuator.
        
        Args:
            data: The scene data to modify.
            damping: The new damping value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the damping is negative, NaN, or infinite, the override will be ignored.

### set_gain_override

```python
def set_gain_override(self, data: SceneData, gain: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the gain value of the actuator.
        
        Args:
            data: The scene data to modify.
            gain: The new gain value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the gain is NaN or infinite, the override will be ignored.

### set_stiffness_override

```python
def set_stiffness_override(self, data: SceneData, stiffness: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the stiffness value of the actuator.
        
        Args:
            data: The scene data to modify.
            stiffness: The new stiffness value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the stiffness is negative, NaN, or infinite, the override will be ignored.
