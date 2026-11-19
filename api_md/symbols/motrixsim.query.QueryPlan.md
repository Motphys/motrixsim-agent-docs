# motrixsim.query.QueryPlan

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A model-bound compiled plan for gathering multiple physics outputs in one call.

    Identical model-resolved query sources share one output region and are filled only once per
    scene instance, while public fields retain their individual names and views.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `fields` | `list[QueryField]` | Compiled fields in output layout order. |
| `total_width` | `int` | Width of the contiguous output buffer per scene instance. |

### fields

```python
fields: list[QueryField]
```

Compiled fields in output layout order.

### total_width

```python
total_width: int
```

Width of the contiguous output buffer per scene instance.

    This is the length of the program buffer's last axis:
    ``program.buffer.shape == (*data.shape, total_width)``. It equals the sum of all field
    sizes — each field contributes the element count of its logical shape — and the fields
    occupy disjoint ``[offset, offset + size)`` ranges along this axis. Identical sources
    are deduplicated when computing this width.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `allocate` | `(self, data: SceneData) -> QueryProgram` | Allocate a zero-initialized reusable query program for the data shape. |

### allocate

```python
def allocate(self, data: SceneData) -> QueryProgram
```

Allocate a zero-initialized reusable query program for the data shape.

        Args:
            data: Scene data whose batch shape determines the program buffer shape.

        Returns:
            QueryProgram: An executable program whose buffer is bound to this plan.

        Raises:
            ValueError: If data belongs to a different model.
