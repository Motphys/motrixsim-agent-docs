# motrixsim.ui.RadioGroupState

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `options` | `list[str]` | Return the current options. |
| `value` | `str` | Return the current radio group value. |

### options

```python
options: list[str]
```

Return the current options.

### value

```python
value: str
```

Return the current radio group value.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `is_changed` | `(self) -> bool` | Return whether this radio group changed in the latest successful synchronization. |
| `set_options` | `(self, options: Sequence[str], *, value: Optional[str] = None) -> None` | Replace all options immediately and enqueue the new state for the next RenderApp.sync(). |
| `set_value` | `(self, value: str) -> None` | Select one existing option and enqueue the new state for the next RenderApp.sync(). |

### is_changed

```python
def is_changed(self) -> bool
```

Return whether this radio group changed in the latest successful synchronization.

### set_options

```python
def set_options(self, options: Sequence[str], *, value: Optional[str] = None) -> None
```

Replace all options immediately and enqueue the new state for the next RenderApp.sync().

        Options must be non-empty and unique. When `value` is omitted, the current value is
        preserved by name when possible, otherwise the first option is selected. Options and value
        are changed atomically in Python. After Rust applies the update, it is returned through the
        regular interaction stream like any other change.

        Raises:
            ValueError: If options are invalid or value is not present in them.
            ReferenceError: If a Frame rebuild replaced this element.
            RuntimeError: If the owning View is unavailable.

### set_value

```python
def set_value(self, value: str) -> None
```

Select one existing option and enqueue the new state for the next RenderApp.sync().

        Each call is submitted as its own update: a later synchronization reports every applied
        update through the regular interaction stream, setting `is_changed()` and invoking
        `on_change` once per update during a later synchronization.

        Raises:
            ValueError: If the value is not present in the current options.
            ReferenceError: If a Frame rebuild replaced this element.
            RuntimeError: If the owning View is unavailable.
