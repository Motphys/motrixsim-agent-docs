# motrixsim.ui.View

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

A View declaration usable as a Viewer blueprint leaf.

    Built-in factories such as ``Viewport()`` and ``Options()`` return this type.
    Use ``with View(title=...)`` to declare a custom UI View.

    Note:
        Adding a View to a layout transfers its declaration and contents to that blueprint.
        A View can be transferred only once, either to a layout or directly to an app.
        Keep it for that app's ``show()`` and ``hide()`` calls.
        Create new Views for a new app, even after closing the first.
        If composition or acceptance fails, create new Views before trying again.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__enter__` | `(self) -> View` |  |
| `__exit__` | `(self, exception_type: Optional[Any], _exception: Optional[Any], _traceback: Optional[Any]) -> bool` |  |
| `__new__` | `(cls, *, title: str, visible: bool = True) -> View` | Start a Python-defined View declaration. |
| `__repr__` | `(self) -> str` |  |

### __enter__

```python
def __enter__(self) -> View
```

### __exit__

```python
def __exit__(self, exception_type: Optional[Any], _exception: Optional[Any], _traceback: Optional[Any]) -> bool
```

### __new__

```python
def __new__(cls, *, title: str, visible: bool = True) -> View
```

Start a Python-defined View declaration.

        Args:
            title: The panel title.
            visible: Initial visibility in the blueprint. Defaults to True.
                Hidden panels keep their dock placement. Use RenderApp.show() to reveal them.

### __repr__

```python
def __repr__(self) -> str
```
