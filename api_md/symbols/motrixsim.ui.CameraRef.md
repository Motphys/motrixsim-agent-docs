# motrixsim.ui.CameraRef

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

A blueprint-local Camera source resolved by the RenderApp that owns the blueprint.

    Construct ``CameraRef(index)`` for a RenderApp Camera slot, or use
    `CameraRef.system` for the System Camera. The reference can be created before either
    Camera has been materialized.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, index: int) -> CameraRef` | Create a blueprint-local reference to a Camera slot in the owning RenderApp. |
| `__repr__` | `(self) -> str` |  |
| `system` | `() -> CameraRef` | Create a blueprint-local reference to the owning RenderApp's System Camera. |

### __new__

```python
def __new__(cls, index: int) -> CameraRef
```

Create a blueprint-local reference to a Camera slot in the owning RenderApp.

### __repr__

```python
def __repr__(self) -> str
```

### system

```python
def system() -> CameraRef
```

Create a blueprint-local reference to the owning RenderApp's System Camera.
