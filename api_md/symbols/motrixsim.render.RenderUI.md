# motrixsim.render.RenderUI

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

The RenderUI object represents the user interface of the render app.

    This class provides access to the user interface of the render app.
    It allows you to add buttons, toggles, and other UI elements to the render app.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `add_button` | `(self, label: str, on_click: Any) -> int` | Add a button to the user interface. |
| `add_toggle` | `(self, label: str, default: bool, on_changed: Any) -> int` | Add a toggle to the user interface. |

### add_button

```python
def add_button(self, label: str, on_click: Any) -> int
```

Add a button to the user interface.

        Args:
            label: The label of the button.
            on_click: The callback function to be called when the button is clicked.

        Returns:
            int: The ID of the button.

### add_toggle

```python
def add_toggle(self, label: str, default: bool, on_changed: Any) -> int
```

Add a toggle to the user interface.

        Args:
            label: The label of the toggle.
            default: The default state of the toggle.
            on_changed: The callback function to be called when the toggle is changed.
