# motrixsim.query.QueryProgram

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A plan-bound query program that owns reusable output storage and executes the query.

    The program carries the compiled queries together with the output buffer and its named
    zero-copy views, so executing it never has to re-validate plan/result pairing: only the
    scene-data identity and batch shape are checked. Fields backed by identical query sources
    share the corresponding region of `buffer` while retaining separate named views. Name lookups
    resolve through a hash index built at allocation time, so `__getitem__` stays constant-time
    regardless of the field count.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `buffer` | `numpy.typing.NDArray[numpy.float32]` | numpy.ndarray: Contiguous query output buffer; identical query sources share one region. |
| `fields` | `list[QueryField]` | Read-only field metadata. |
| `shape` | `tuple` | tuple[int, ...]: SceneData batch shape used to allocate this program. |

### buffer

```python
buffer: numpy.typing.NDArray[numpy.float32]
```

numpy.ndarray: Contiguous query output buffer; identical query sources share one region.

### fields

```python
fields: list[QueryField]
```

Read-only field metadata.

### shape

```python
shape: tuple
```

tuple[int, ...]: SceneData batch shape used to allocate this program.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__getitem__` | `(self, name: str) -> numpy.typing.NDArray[numpy.float32]` | Get the named field view from the query program. |
| `execute` | `(self, data: SceneData, env_ids: Optional[numpy.typing.NDArray[numpy.int64] \| Sequence[numpy.int64]] = None) -> QueryProgram` | Execute the compiled query into this program's buffer. |
| `items` | `(self) -> list[tuple[str, numpy.typing.NDArray[numpy.float32]]]` | Return query field names and views in layout order. |
| `keys` | `(self) -> list[str]` | Return the names of all query fields in layout order. |
| `values` | `(self) -> list[numpy.typing.NDArray[numpy.float32]]` | Return all query field views in layout order. |

### __getitem__

```python
def __getitem__(self, name: str) -> numpy.typing.NDArray[numpy.float32]
```

Get the named field view from the query program.

        Args:
            name: Name of the compiled query field.

        Returns:
            NDArray[float]: A zero-copy view of the field in the program buffer.

        Raises:
            KeyError: If name is not present in the query program.

### execute

```python
def execute(self, data: SceneData, env_ids: Optional[numpy.typing.NDArray[numpy.int64] | Sequence[numpy.int64]] = None) -> QueryProgram
```

Execute the compiled query into this program's buffer.

        Args:
            data: Scene data compatible with the model used to compile this program.
            env_ids: Optional one-dimensional environment
                indices into the first batch dimension of ``data``. Only the worlds of these
                environments are read and only the matching rows of ``buffer`` are written; all
                other rows are left untouched. Duplicate indices are allowed and idempotent. When
                None, the full batch is executed.

        Returns:
            QueryProgram: This program, so ``plan.allocate(data).execute(data)`` chains.

        Raises:
            RuntimeError: If this program requires a report that is not enabled on the model.
            ValueError: If data belongs to a different model or has an incompatible batch shape,
                ``env_ids`` is given for non-batched data, or an environment index is negative or
                out of range.

### items

```python
def items(self) -> list[tuple[str, numpy.typing.NDArray[numpy.float32]]]
```

Return query field names and views in layout order.

### keys

```python
def keys(self) -> list[str]
```

Return the names of all query fields in layout order.

### values

```python
def values(self) -> list[numpy.typing.NDArray[numpy.float32]]
```

Return all query field views in layout order.
