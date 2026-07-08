# motrixsim.render.RenderCamera

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `capture` | `(self) -> CaptureTask` | Request a capture from this camera. This operation is asynchronous and you need to query the |

### capture

```python
def capture(self) -> CaptureTask
```

Request a capture from this camera. This operation is asynchronous and you need to query the
        result by the returned `CaptureTask`.

        Returns:
            CaptureTask: An async task that can be used to check the capture state and get the
            captured image.
