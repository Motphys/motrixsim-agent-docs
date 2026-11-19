# motrixsim.LidarScanStatus

Module: [`motrixsim`](../modules/motrixsim.md)

Lightweight LiDAR measurement status for a SceneData selection.

    Note:
        Both arrays have data.shape, including scalar shape for a single instance.
        Values describe the currently available measurement. Query again after stepping, resetting,
        or refreshing the data.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `ready` | `numpy.typing.NDArray[numpy.bool_]` | NDArray[bool]: Whether at least one complete scan has been published. |
| `scan_seq` | `numpy.typing.NDArray[numpy.uint64]` | NDArray[uint64]: Monotonically increasing measurement sequence, initially zero. |

### ready

```python
ready: numpy.typing.NDArray[numpy.bool_]
```

NDArray[bool]: Whether at least one complete scan has been published.

### scan_seq

```python
scan_seq: numpy.typing.NDArray[numpy.uint64]
```

NDArray[uint64]: Monotonically increasing measurement sequence, initially zero.
