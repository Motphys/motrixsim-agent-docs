# motrixsim.coacd.MeshReport

Module: [`motrixsim.coacd`](../modules/motrixsim.coacd.md)

Per-mesh report for offline CoACD decomposition.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `name` | `str` | In-file mesh name, or the file stem for single-mesh files. |
| `part_count` | `int` | Number of convex parts produced or planned. |
| `part_files` | `list[str]` | Source-file-level convex-part output paths. With default output, these are |
| `skipped_reason` | `str` | Skip or failure reason; empty when successful. |

### name

```python
name: str
```

In-file mesh name, or the file stem for single-mesh files.

### part_count

```python
part_count: int
```

Number of convex parts produced or planned.

### part_files

```python
part_files: list[str]
```

Source-file-level convex-part output paths. With default output, these are
    relative to the source mesh directory. With a custom output directory, these are relative
    to that output directory. With explicit file output, this is the output file name.

### skipped_reason

```python
skipped_reason: str
```

Skip or failure reason; empty when successful.
