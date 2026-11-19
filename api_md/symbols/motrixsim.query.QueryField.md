# motrixsim.query.QueryField

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

Read-only metadata for one compiled query field.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `dtype` | `str` | NumPy dtype name used by this field. |
| `name` | `str` | Name used to address this field in a `QueryProgram`. |
| `offset` | `int` | Starting offset of this field in the last axis of the query buffer. |
| `shape` | `list[int]` | Logical field shape, excluding the `SceneData` batch dimensions. |
| `size` | `int` | Number of scalar values occupied by this field per scene instance. |

### dtype

```python
dtype: str
```

NumPy dtype name used by this field.

### name

```python
name: str
```

Name used to address this field in a `QueryProgram`.

### offset

```python
offset: int
```

Starting offset of this field in the last axis of the query buffer.

    Fields backed by an identical canonical source may have the same offset.

### shape

```python
shape: list[int]
```

Logical field shape, excluding the `SceneData` batch dimensions.

### size

```python
size: int
```

Number of scalar values occupied by this field per scene instance.
