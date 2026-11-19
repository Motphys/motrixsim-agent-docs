# motrixsim.ui.TextInputState

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `value` | `str` | Return the latest synchronized text value. |

### value

```python
value: str
```

Return the latest synchronized text value.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `is_changed` | `(self) -> bool` | Return whether this input changed in the latest successful synchronization. |
| `is_submitted` | `(self) -> bool` | Return whether this input was submitted in the latest successful synchronization. |

### is_changed

```python
def is_changed(self) -> bool
```

Return whether this input changed in the latest successful synchronization.

### is_submitted

```python
def is_submitted(self) -> bool
```

Return whether this input was submitted in the latest successful synchronization.
