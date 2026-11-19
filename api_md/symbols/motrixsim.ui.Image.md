# motrixsim.ui.Image

Module: [`motrixsim.ui`](../modules/motrixsim.ui.md)

A mutable Image presentation embedded in a declaration or used as a standalone Viewer leaf.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, *, title: Optional[str] = None, width: Optional[float] = None, height: Optional[float] = None, fit_to_size: bool = True, keep_aspect_ratio: bool = True, toolbar: bool = True, image: Optional[motrixsim.render.Image] = None) -> Image` | Create a mutable Image presentation slot. |
| `__repr__` | `(self) -> str` |  |
| `set_image` | `(self, image: Optional[motrixsim.render.Image]) -> None` | Set or clear the image displayed by this slot. |

### __new__

```python
def __new__(cls, *, title: Optional[str] = None, width: Optional[float] = None, height: Optional[float] = None, fit_to_size: bool = True, keep_aspect_ratio: bool = True, toolbar: bool = True, image: Optional[motrixsim.render.Image] = None) -> Image
```

Create a mutable Image presentation slot.

        Args:
            title: Standalone Image View title. Only valid outside a declaration.
            width: Preferred slot width.
            height: Preferred slot height.
            fit_to_size: Standalone-only; stretch to fill the View. Defaults to True.
            keep_aspect_ratio: Preserve the source aspect ratio. Defaults to True.
            toolbar: Standalone-only; show the image toolbar initially. Defaults to True.
            image: Initial image. Registered when the owning app
                receives the content; `set_image` also works after binding.

### __repr__

```python
def __repr__(self) -> str
```

### set_image

```python
def set_image(self, image: Optional[motrixsim.render.Image]) -> None
```

Set or clear the image displayed by this slot.

        Note:
            Requires a bound RenderApp: ownership is checked and CPU images register with this
            slot's RenderApp at call time, updating the original Image to reference the registered
            resource. Later pixel changes appear after synchronization without calling set_image
            again. The slot retains only the resource handle. Pass None to clear the slot.

        Args:
            image: The image resource to display, or None to clear the slot.

        Raises:
            ReferenceError: If a Frame rebuild replaced this slot or its RenderApp was closed.
            RuntimeError: If the slot is not bound to a RenderApp yet, or when submitting a
                camera GPU target or an Image from another app.
