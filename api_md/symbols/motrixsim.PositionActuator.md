# motrixsim.PositionActuator

Module: [`motrixsim`](../modules/motrixsim.md)

Position actuator (MJCF ``<position>``).
    
    MJCF parameter mapping:
    
    - ``kp`` -> kp (writes both gain and stiffness internally)
    - ``kv`` -> kd (writes damping internally, defaults to 0)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_kd_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kd override value from the scene data. |
| `get_kp_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kp override value from the scene data. |
| `set_kd_override` | `(self, data: SceneData, kd: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the kd value for a position actuator. Writes damping. |
| `set_kp_override` | `(self, data: SceneData, kp: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the kp value for a position actuator. Writes both gain and stiffness. |

### get_kd_override

```python
def get_kd_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the kd override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The kd value. Shape: ``(*data.shape,)``

### get_kp_override

```python
def get_kp_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the kp override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The kp value. Shape: ``(*data.shape,)``

### set_kd_override

```python
def set_kd_override(self, data: SceneData, kd: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the kd value for a position actuator. Writes damping.
        
        Args:
            data: The scene data to modify.
            kd: The new kd value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the value is negative, NaN, or infinite, the override will be ignored.

### set_kp_override

```python
def set_kp_override(self, data: SceneData, kp: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the kp value for a position actuator. Writes both gain and stiffness.
        
        Args:
            data: The scene data to modify.
            kp: The new kp value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values
        
        Note:
            If the value is negative, NaN, or infinite, the override will be ignored.
