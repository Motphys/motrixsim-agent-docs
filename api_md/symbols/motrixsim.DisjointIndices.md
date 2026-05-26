# motrixsim.DisjointIndices

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `size` | `int` | The number of elements in the disjoint index set. Alias to `len(set)`. |

### size

```python
size: int
```

The number of elements in the disjoint index set. Alias to `len(set)`.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__len__` | `(self) -> int` |  |
| `__new__` | `(cls, indices: Any) -> DisjointIndices` | Create disjoint indices from a list of indices or a bool mask. |

### __len__

```python
def __len__(self) -> int
```

### __new__

```python
def __new__(cls, indices: Any) -> DisjointIndices
```

Create disjoint indices from a list of indices or a bool mask.
        
        Args:
            indices: The list of indices.
            - If type is `ArrayLike[int]`, it creates disjoint indices from the list of indices.
            - If type is `ArrayLike[bool]`, it creates disjoint indices from the index of the true
              values.
