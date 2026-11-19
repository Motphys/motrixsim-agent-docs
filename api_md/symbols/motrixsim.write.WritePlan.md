# motrixsim.write.WritePlan

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A model-bound compiled plan for scattering multiple physics inputs in one call.

    Compile time resolves every target to its native index, validates target types, and rejects
    duplicate writes to the same underlying channel. Each field owns a disjoint region of the
    program buffer.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `fields` | `list[WriteField]` | Compiled fields in buffer layout order. |
| `forward_kinematic` | `bool` | Whether executions of programs from this plan run forward kinematics afterwards. |
| `reset` | `bool` | Whether executions of programs from this plan reset each selected world first. |
| `reset_overrides` | `bool` | Whether the plan-level reset also restores the Data-side override buffers to the |
| `total_width` | `int` | Width of the contiguous write buffer per scene instance. |

### fields

```python
fields: list[WriteField]
```

Compiled fields in buffer layout order.

### forward_kinematic

```python
forward_kinematic: bool
```

Whether executions of programs from this plan run forward kinematics afterwards.

### reset

```python
reset: bool
```

Whether executions of programs from this plan reset each selected world first.

### reset_overrides

```python
reset_overrides: bool
```

Whether the plan-level reset also restores the Data-side override buffers to the
    Model defaults. Ignored when `reset` is False. Defaults to True; pass False to keep
    per-instance randomized overrides across executions.

### total_width

```python
total_width: int
```

Width of the contiguous write buffer per scene instance.

    This is the length of the program buffer's last axis:
    ``program.buffer.shape == (*data.shape, total_width)``. It equals the sum of all field
    sizes — each field contributes the element count of its logical shape — and the fields
    occupy disjoint ``[offset, offset + size)`` ranges along this axis.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `allocate` | `(self, data: SceneData) -> WriteProgram` | Allocate a zero-initialized reusable write program for the data shape. |

### allocate

```python
def allocate(self, data: SceneData) -> WriteProgram
```

Allocate a zero-initialized reusable write program for the data shape.

        Args:
            data: Scene data whose batch shape determines the program buffer shape.

        Returns:
            WriteProgram: An executable program whose buffer is bound to this plan.

        Raises:
            ValueError: If data belongs to a different model.
