# motrixsim.coacd

## Classes

- [`DecomposeReport`](../symbols/motrixsim.coacd.DecomposeReport.md) - Aggregate report for offline CoACD decomposition.
- [`FileReport`](../symbols/motrixsim.coacd.FileReport.md) - Per-file report for offline CoACD decomposition.
- [`MeshReport`](../symbols/motrixsim.coacd.MeshReport.md) - Per-mesh report for offline CoACD decomposition.

## Functions

### decompose

```python
def decompose(path: str, *, threshold: float = 0.1, max_convex_hull: int = 64, output: str = 'convex_parts', dry_run: bool = False) -> DecomposeReport
```

Decompose mesh assets (.obj/.stl) into source-file-level convex-part output files.

    Args:
        path: Mesh file (.obj/.stl), or a directory searched recursively.
        threshold: CoACD threshold.
        max_convex_hull: CoACD max convex hull count.
        output: Output directory, or a single `.obj` / `.stl` file for single-file input.
            The default `convex_parts` writes one `{source_stem}_convex.obj` next to each source
            mesh file.
        dry_run: Decompose and report planned output files but do not write them.

    Returns:
        DecomposeReport: Structured report. Each source mesh file produces at most one merged
        output file; if a source OBJ contains multiple `o`/`g` meshes, they are decomposed
        separately and written into that same output file.
