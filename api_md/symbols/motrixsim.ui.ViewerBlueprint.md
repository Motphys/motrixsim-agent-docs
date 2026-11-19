# motrixsim.ui.ViewerBlueprint

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

A layout composed from Views and other layout containers.

    Note:
        Composition consumes its input Views and nested blueprints. An app then consumes the
        resulting blueprint. Reusing consumed input raises RuntimeError.
        Keep individual View objects for runtime show/hide calls in the owning app.
        If composition or acceptance fails, create new Views and a new blueprint.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__repr__` | `(self) -> str` |  |

### __repr__

```python
def __repr__(self) -> str
```
