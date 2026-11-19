# motrixsim.PositionActuator

Module: [`motrixsim`](../modules/motrixsim.md)

Position actuator (MJCF ``<position>``).

    MJCF parameter mapping:

    - ``kp`` -> kp (writes both gain and stiffness internally)
    - ``kv`` -> kd (writes damping internally, defaults to 0)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `kd` | `float` | The derivative gain (kd) configured in the model. |
| `kp` | `float` | The proportional gain (kp) configured in the model. |

### kd

```python
kd: float
```

The derivative gain (kd) configured in the model.

    Unlike `get_kd_override`, this property reads the static model configuration and
    does not require scene data.

### kp

```python
kp: float
```

The proportional gain (kp) configured in the model.

    Unlike `get_kp_override`, this property reads the static model configuration and
    does not require scene data.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_kd_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kd override value from the scene data. |
| `get_kp_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the kp override value from the scene data. |
| `set_damping_override` | `(self, data: SceneData, damping: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the damping value for a position actuator. |
| `set_kp_override` | `(self, data: SceneData, kp: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the kp value for a position actuator. Writes both gain and stiffness. |

### get_kd_override

```python
def get_kd_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the kd override value from the scene data.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The kd value. Shape: ``(*data.shape,)``.

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

        Args:
            data: The scene data to modify.
            damping: The new damping value.
                - Shape (): Single value applied to all batches
                - Shape: ``(*data.shape,)``: Per-batch values

        Note:
            if the value is negative, NaN, or infinite, the override will be ignored.

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
            if the value is negative, NaN, or infinite, the override will be ignored.
