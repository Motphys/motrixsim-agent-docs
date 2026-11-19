# motrixsim.write.WriteProgram

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A plan-bound write program that owns a reusable input buffer and executes the writes.

    The program carries the compiled write operations together with the buffer and its named
    zero-copy views. Users fill the views, then one `execute` call scatters every selected
    buffer row into the scene data and optionally runs forward kinematics once per selected
    world. Name lookups resolve through a hash index built at allocation time.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `buffer` | `numpy.typing.NDArray[numpy.float32]` | numpy.ndarray: Contiguous write buffer; every field owns a disjoint region. |
| `fields` | `list[WriteField]` | Read-only field metadata. |
| `forward_kinematic` | `bool` | Whether every execution runs forward kinematics after applying the writes. |
| `reset` | `bool` | Whether every execution resets each selected world before applying the writes. |
| `reset_overrides` | `bool` | Whether the plan-level reset also restores override buffers to the Model defaults. |
| `shape` | `tuple` | tuple[int, ...]: SceneData batch shape used to allocate this program. |

### buffer

```python
buffer: numpy.typing.NDArray[numpy.float32]
```

numpy.ndarray: Contiguous write buffer; every field owns a disjoint region.

### fields

```python
fields: list[WriteField]
```

Read-only field metadata.

### forward_kinematic

```python
forward_kinematic: bool
```

Whether every execution runs forward kinematics after applying the writes.

### reset

```python
reset: bool
```

Whether every execution resets each selected world before applying the writes.

### reset_overrides

```python
reset_overrides: bool
```

Whether the plan-level reset also restores override buffers to the Model defaults.

### shape

```python
shape: tuple
```

tuple[int, ...]: SceneData batch shape used to allocate this program.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, name: str) -> numpy.typing.NDArray[numpy.float32]` | Get the named field view from the write program. |
| `execute` | `(self, data: SceneData, env_ids: Optional[numpy.typing.NDArray[numpy.int64] \| Sequence[numpy.int64]] = None) -> WriteProgram` | Execute the compiled writes from this program's buffer into the scene data. |
| `items` | `(self) -> list[tuple[str, numpy.typing.NDArray[numpy.float32]]]` | Return write field names and views in layout order. |
| `keys` | `(self) -> list[str]` | Return the names of all write fields in layout order. |
| `values` | `(self) -> list[numpy.typing.NDArray[numpy.float32]]` | Return all write field views in layout order. |

### __getitem__

```python
def __getitem__(self, name: str) -> numpy.typing.NDArray[numpy.float32]
```

Get the named field view from the write program.

        Args:
            name: Name of the compiled write field.

        Returns:
            NDArray[float]: A zero-copy view of the field in the program buffer.

        Raises:
            KeyError: If name is not present in the write program.

### execute

```python
def execute(self, data: SceneData, env_ids: Optional[numpy.typing.NDArray[numpy.int64] | Sequence[numpy.int64]] = None) -> WriteProgram
```

Execute the compiled writes from this program's buffer into the scene data.

        The reset and forward kinematics behavior is fixed by the plan this program was
        allocated from (see ``SceneModel.compile_write``).

        Args:
            data: Scene data compatible with the model used to compile this program.
            env_ids: Optional one-dimensional environment
                indices into the first batch dimension of ``data``. Only the worlds of these
                environments are written; all other worlds are left untouched. Duplicate indices
                are allowed and idempotent, and an empty selection is a no-op. When None, the
                full batch is executed.

        Returns:
            WriteProgram: This program, so ``plan.allocate(data).execute(data)`` chains.

        Raises:
            ValueError: If data belongs to a different model or has an incompatible batch shape,
                ``env_ids`` is given for non-batched data, or an environment index is negative
                or out of range.

### items

```python
def items(self) -> list[tuple[str, numpy.typing.NDArray[numpy.float32]]]
```

Return write field names and views in layout order.

### keys

```python
def keys(self) -> list[str]
```

Return the names of all write fields in layout order.

### values

```python
def values(self) -> list[numpy.typing.NDArray[numpy.float32]]
```

Return all write field views in layout order.
