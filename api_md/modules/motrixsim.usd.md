# motrixsim.usd

## Functions

### load_usd

```python
def load_usd(usd_path: str | Path, deduplicate_vertices: bool = True) -> SceneModel
```

Load a USD file and return a SceneModel ready for simulation.

    Args:
        usd_path: Path to the USD file (.usd, .usda, .usdc, .usdz).
        deduplicate_vertices: If True (default), merge vertices with identical attributes.
