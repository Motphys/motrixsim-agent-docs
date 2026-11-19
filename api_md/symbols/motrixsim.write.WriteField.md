# motrixsim.write.WriteField

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

Read-only metadata for one compiled write field.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `dtype` | `str` | NumPy dtype name used by this field. |
| `name` | `str` | Name used to address this field in a `WriteProgram`. |
| `offset` | `int` | Starting offset of this field in the last axis of the write buffer. |
| `shape` | `tuple` | list[int]: Logical field shape, excluding the `SceneData` batch dimensions. |
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

Name used to address this field in a `WriteProgram`.

### offset

```python
offset: int
```

Starting offset of this field in the last axis of the write buffer.

### shape

```python
shape: tuple
```

list[int]: Logical field shape, excluding the `SceneData` batch dimensions.

### size

```python
size: int
```

Number of scalar values occupied by this field per scene instance.
