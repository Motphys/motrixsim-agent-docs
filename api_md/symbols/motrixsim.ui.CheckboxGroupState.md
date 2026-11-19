# motrixsim.ui.CheckboxGroupState

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `options` | `list[str]` | Return the current options. |
| `value` | `list[str]` | Return the current checkbox group value. |

### options

```python
options: list[str]
```

Return the current options.

### value

```python
value: list[str]
```

Return the current checkbox group value.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `is_changed` | `(self) -> bool` | Return whether this checkbox group changed in the latest successful synchronization. |
| `set_options` | `(self, options: Sequence[str], *, value: Optional[Sequence[str]] = None) -> None` | Replace all options immediately and enqueue the new state for the next RenderApp.sync(). |
| `set_value` | `(self, value: Sequence[str]) -> None` | Select zero or more options and enqueue the new state for the next RenderApp.sync(). |

### is_changed

```python
def is_changed(self) -> bool
```

Return whether this checkbox group changed in the latest successful synchronization.

### set_options

```python
def set_options(self, options: Sequence[str], *, value: Optional[Sequence[str]] = None) -> None
```

Replace all options immediately and enqueue the new state for the next RenderApp.sync().

        Options must be unique and may be empty. When `value` is omitted, the intersection of the
        current selection and new options is preserved. Options and values change atomically in
        Python and are normalized to option order. After Rust applies the update, it is returned
        through the regular interaction stream like any other change.

        Raises:
            ValueError: If options or values are invalid.
            ReferenceError: If a Frame rebuild replaced this element.
            RuntimeError: If the owning View is unavailable.

### set_value

```python
def set_value(self, value: Sequence[str]) -> None
```

Select zero or more options and enqueue the new state for the next RenderApp.sync().

        Values must be unique and are normalized to option order. Each call is submitted as its
        own update: a later synchronization reports every applied update through the regular
        interaction stream, setting `is_changed()` and invoking `on_change` once per update
        during a later synchronization.

        Raises:
            ValueError: If a value is duplicated or is not present in the current options.
            ReferenceError: If a Frame rebuild replaced this element.
            RuntimeError: If the owning View is unavailable.
