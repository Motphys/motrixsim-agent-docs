# motrixsim.render.CaptureTask

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `state` | `str` | The state of the capture task. |

### state

```python
state: str
```

The state of the capture task.

    - `pending` if the capture is processing.
    - `done` if the capture was completed. In this status, you can retrieve the captured result.
    - `closed` if the result has been received or the task has been dropped by remote.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `take_image` | `(self) -> Optional[Image]` | Try take the image from the capture task. |

### take_image

```python
def take_image(self) -> Optional[Image]
```

Try take the image from the capture task.

        Returns:
           Option[Image]: The captured image.
           - If the capture is successful, it will return the image and close the task.
           - Otherwise, it will return `None` and the state will remain unchanged.

        Raise:
            PyRuntimeError: If the task is closed or some internal error happend.
