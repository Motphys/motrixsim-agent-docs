# motrixsim.coacd.FileReport

Module: [`motrixsim.coacd`](../modules/motrixsim.coacd.md)

Per-file report for offline CoACD decomposition.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `fatal_error` | `Optional[str]` | Fatal file-level error, or `None` when the file was processed. |
| `meshes` | `list[MeshReport]` | Per-mesh reports for this file. |
| `path` | `str` | Source mesh file path. |

### fatal_error

```python
fatal_error: Optional[str]
```

Fatal file-level error, or `None` when the file was processed.

### meshes

```python
meshes: list[MeshReport]
```

Per-mesh reports for this file.

### path

```python
path: str
```

Source mesh file path.
