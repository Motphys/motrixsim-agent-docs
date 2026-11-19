# motrixsim.render.RenderCamera

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `capture` | `(self) -> CaptureTask` | Request a capture from this camera. This operation is asynchronous and you need to query the |
| `capture_buffer` | `(self) -> CaptureTask` | Request a capture from this camera. This operation is asynchronous and you need to query the |

### capture

```python
def capture(self) -> CaptureTask
```

Request a capture from this camera. This operation is asynchronous and you need to query the
        result by the returned `CaptureTask`.

        Returns:
            CaptureTask: An async task that can be used to check the capture state and get the
            captured image.

### capture_buffer

```python
def capture_buffer(self) -> CaptureTask
```

Request a capture from this camera. This operation is asynchronous and you need to query the
        result by the returned `CaptureTask`.

        This function captures a buffer. Typically, you only need to capture once at the very
        beginning, and can then access the data in this buffer directly — it always holds the
        latest data.

        Returns:
            CaptureTask: An async task that can be used to check the capture state and get the
            captured buffer.
