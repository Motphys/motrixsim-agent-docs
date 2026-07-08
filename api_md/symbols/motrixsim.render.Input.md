# motrixsim.render.Input

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

The Input object represents the input events of the render app.

    This class provides access to the input events of the render app.
    It allows you to check if a key or mouse button is pressed, and get the mouse ray.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `is_ctrl_clicked` | `(self, ctrl_id: int) -> bool` | Check whether a control with the given ID is clicked. |
| `is_key_just_pressed` | `(self, key: str) -> bool` | Check if a key is just pressed. |
| `is_key_pressed` | `(self, key: str) -> bool` | Check if a key is just pressed. |
| `is_mouse_just_pressed` | `(self, mouse: str) -> bool` | Check if a mouse button is just pressed. |
| `mouse_ray` | `(self) -> list[float]` | Returns a ray from camera to mouse click position. |

### is_ctrl_clicked

```python
def is_ctrl_clicked(self, ctrl_id: int) -> bool
```

Check whether a control with the given ID is clicked.

        Args:
            ctrl_id: The ID of the control.

        Returns:
            bool: True if the control is clicked, False otherwise.

### is_key_just_pressed

```python
def is_key_just_pressed(self, key: str) -> bool
```

Check if a key is just pressed.
        Check by inputting the lowercase form of the keyboard keys, such as 'a' 's' 'w' 'd' 'f5' and
        'esc'. The details can be found in the "Supported Keyboard Keys Table" under the "IO
        Input Events" section of the /user_guide/main_function/render.

        Args:
            key: The key to check.

        Returns:
            bool: True if the key is pressed, False otherwise.

### is_key_pressed

```python
def is_key_pressed(self, key: str) -> bool
```

Check if a key is just pressed.
        Check by inputting the lowercase form of the keyboard keys, such as 'a' 's' 'w' 'd' 'f5' and
        'esc'. The details can be found in the "Supported Keyboard Keys Table" under the "IO
        Input Events" section of the /user_guide/main_function/render.

        Args:
            key: The key to check.

        Returns:
            bool: True if the key is pressed, False otherwise.

### is_mouse_just_pressed

```python
def is_mouse_just_pressed(self, mouse: str) -> bool
```

Check if a mouse button is just pressed.

        Args:
            mouse: The mouse button to check.

        Returns:
            bool: True if the mouse button is pressed, False otherwise.

### mouse_ray

```python
def mouse_ray(self) -> list[float]
```

Returns a ray from camera to mouse click position.

        Returns:
            List[float]: The ray from camera to mouse click position.
            It is a 6-element array:
            - Origin : (array[0],array[1],array[2])
            - Direction : (array[3],array[4],array[5])
