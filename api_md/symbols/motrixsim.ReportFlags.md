# motrixsim.ReportFlags

Module: [`motrixsim`](../modules/motrixsim.md)

Toggles for runtime report generation, accessed via `motrixsim.SceneModel.reports`.

    Reports are step-after instance-side snapshots used for debugging, visualization and queries.
    Each toggle is a model-wide persistent switch; the corresponding report is produced starting
    from the next step.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `contacting_geoms` | `bool` | Whether the contacting-geoms report is enabled. |

### contacting_geoms

```python
contacting_geoms: bool
```

Whether the contacting-geoms report is enabled.

    Note:
        Must be enabled before `motrixsim.ContactQuery.contacting_geoms` returns results.
