# motrixsim.VelocityActuator

Module: [`motrixsim`](../modules/motrixsim.md)

Velocity actuator (MJCF ``<velocity>``).

    MJCF parameter mapping:

    - ``kv`` -> kv (writes both gain and damping internally)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_kv_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kv override value from the scene data. |
| `set_kv_override` | `(self, data: SceneData, kv: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the kv value for a velocity actuator. Writes both gain and damping. |

### get_kv_override

```python
def get_kv_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the kv override value from the scene data.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The kv value. Shape: ``(*data.shape,)``

### set_kv_override

```python
def set_kv_override(self, data: SceneData, kv: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the kv value for a velocity actuator. Writes both gain and damping.

        Args:
            data: The scene data to modify.
            kv: The new kv value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values

        Note:
            Raises ValueError if the value is negative, NaN, infinite, or the actuator is not a
            velocity actuator.
