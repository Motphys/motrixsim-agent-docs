# motrixsim.ActuatorSensor

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `actuator_index` | `int` | The compiled apparent actuator index bound by this sensor. |

### actuator_index

```python
actuator_index: int
```

The compiled apparent actuator index bound by this sensor.

    This index also identifies the actuator's control slot: it matches
    `SceneModel.get_actuator_index(name)`, indexes `SceneData.actuator_ctrls`, and indexes
    `SceneModel.actuators`. It is not the sensor's output position and is not inferred from
    sensor ordering. Multiple sensors may therefore expose the same `actuator_index`.
