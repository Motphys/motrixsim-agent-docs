# motrixsim.write.GeomFrictionOverride

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A write source for friction overrides of selected geoms.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `selection` | `Optional[list[Any]]` | list[str] \| list[int] \| None: Target geoms given by names or indices, or `None` for |

### selection

```python
selection: Optional[list[Any]]
```

list[str] | list[int] | None: Target geoms given by names or indices, or `None` for
    all geoms in model order.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, selection: Optional[Any] = None) -> GeomFrictionOverride` | Create a write source for friction overrides of geoms selected by names or indices. |

### __new__

```python
def __new__(cls, selection: Optional[Any] = None) -> GeomFrictionOverride
```

Create a write source for friction overrides of geoms selected by names or indices.

        Args:
            selection: Geoms given by names or
                indices, or `None` for all geoms in model order. The given order defines the
                buffer layout; names and indices must not be mixed and duplicates are rejected
                at compile time.

        Note:
            Friction components are ``[slide, spin, roll]``. Per-instance values that are
            negative, NaN, or infinite are ignored during execution and keep the previous
            override.
