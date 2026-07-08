# motrixsim.TerrainScanner

Module: [`motrixsim`](../modules/motrixsim.md)

A scanner object for batched frame-relative terrain height sampling.

    ``TerrainScanner`` caches all static parameters (terrain geom, reference
    frame, scan offsets, alignment mode, output mode) at construction time so
    that the hot-path `scan` call only reads batched poses and writes
    results — no parameter parsing, no temporary array allocation.

    Typical usage for RL locomotion height-scan::

        scanner = motrixsim.TerrainScanner(
            terrain=hfield_geom,
            frame=base_link,
            offsets=scan_offsets,       # shape (N, 2)
            alignment="yaw",
            output="height",
        )

        # in step loop (hot path)
        heights = scanner.scan(data, out=buffer)

    Args:
        terrain: The height-field geom to sample.
        frame: The reference frame whose pose drives the scan.
        offsets: Frame-local XY scan points, shape ``(N, 2)``.
        alignment: How the frame orientation is projected.
            ``"yaw"`` — only the heading (rotation about world Z) is used;
            roll and pitch are ignored.
        output: What quantity to return.
            ``"height"`` — terrain surface world-Z coordinate.
            ``"clearance"`` — ``frame_z - terrain_height``, i.e. vertical
            distance from the frame origin to the terrain surface below each
            scan point.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, terrain: GeomHField, frame: Link, offsets: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], alignment: str = 'yaw', output: str = 'height') -> TerrainScanner` |  |
| `scan` | `(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Perform a batched terrain height scan. |

### __new__

```python
def __new__(cls, terrain: GeomHField, frame: Link, offsets: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], alignment: str = 'yaw', output: str = 'height') -> TerrainScanner
```

### scan

```python
def scan(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Perform a batched terrain height scan.

        For each batch instance the method reads the frame link pose, extracts
        the yaw heading, rotates each local offset into world XY, samples the
        terrain height via bilinear interpolation, and writes the result.

        Args:
            data: The scene data (batched or single).
            out: Pre-allocated output buffer of shape
                ``(*data.shape, N)`` where ``N`` is the number of scan points.
                When provided, the result is written in-place and returned
                directly, avoiding an internal allocation.

        Returns:
            NDArray[float]: Shape ``(*data.shape, N)``.
                When ``output="height"``, each element is the terrain surface
                world-Z at the corresponding scan point.
                When ``output="clearance"``, each element is
                ``frame_z - terrain_height``.
