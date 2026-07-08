# motrixsim.PositionActuator

Module: [`motrixsim`](../modules/motrixsim.md)

Position actuator (MJCF ``<position>``).

    MJCF parameter mapping:

    - ``kp`` -> kp (writes both gain and stiffness internally)
    - ``kv`` -> kd (writes damping internally, defaults to 0)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_dampratio_override` | `(self, data: SceneData) -> Optional[numpy.typing.NDArray[numpy.float32]]` | Get the dampratio override value from the scene data. |
| `get_kd_override` | `(self, data: SceneData) -> Optional[numpy.typing.NDArray[numpy.float32]]` | Get the kd override value from the scene data. |
| `get_kp_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kp override value from the scene data. |
| `set_damping_override` | `(self, data: SceneData, damping: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the damping value for a position actuator. |
| `set_kp_override` | `(self, data: SceneData, kp: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the kp value for a position actuator. Writes both gain and stiffness. |

### get_dampratio_override

```python
def get_dampratio_override(self, data: SceneData) -> Optional[numpy.typing.NDArray[numpy.float32]]
```

Get the dampratio override value from the scene data.

        Args:
            data: The scene data to query.

        Returns:
            Optional[NDArray[float]]: The dampratio value. Shape: ``(*data.shape,)``.
                Returns None when this actuator stores DampingType.Kv in the model.

### get_kd_override

```python
def get_kd_override(self, data: SceneData) -> Optional[numpy.typing.NDArray[numpy.float32]]
```

Get the kd override value from the scene data.

        Args:
            data: The scene data to query.

        Returns:
            Optional[NDArray[float]]: The kd value. Shape: ``(*data.shape,)``.
                Returns None when this actuator stores DampingType.Dampratio in the model.

### get_kp_override

```python
def get_kp_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the kp override value from the scene data.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The kp value. Shape: ``(*data.shape,)``

### set_damping_override

```python
def set_damping_override(self, data: SceneData, damping: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the damping value for a position actuator.

        The meaning of the damping value depends on the actuator's
        `motrixsim.Actuator.damping_type`:

        - ``DampingType.Kv``: The value is the absolute damping coefficient (kv).
        - ``DampingType.Dampratio``: The value is the damping ratio relative to critical damping.

        Args:
            data: The scene data to modify.
            damping: The new damping value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values

        Note:
            if the value is negative, NaN, infinite, or the actuator type does
            not support independent damping overrides, the override will be ignored.

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
            if the value is negative, NaN, infinite, or the actuator is not a
            position actuator, the override will be ignored.
