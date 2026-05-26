# motrixsim.HField

Module: [`motrixsim`](../modules/motrixsim.md)

The HField object represents a height field terrain in the scene.
    
    This class provides access to height field (terrain) data used for ground interactions,
    terrain following, and surface-based physics. Height fields provide an efficient way
    to represent large terrain surfaces with elevation data.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `bound` | `numpy.typing.NDArray[numpy.float32]` | Get the bounding box of the height field in local space. |
| `height_matrix` | `numpy.typing.NDArray[numpy.float32]` | Get the height matrix data as a numpy array. |
| `index` | `int` | The index of the hfield in the scene. |
| `model` | `SceneModel` | The scene model that this hfield belongs to. |
| `name` | `Optional[str]` | The name of the hfield. Must be unique within the scene. |
| `ncol` | `int` | The number of columns in the height field grid. |
| `nrow` | `int` | The number of rows in the height field grid. |

### bound

```python
bound: numpy.typing.NDArray[numpy.float32]
```

Get the bounding box of the height field in local space.
    
    Returns:
        NDArray[float]: A 1D numpy array of shape (6,) representing the bounding box
            in the format `[-extent_x, -extent_y, 0, extent_x, extent_y, size_z]`.

### height_matrix

```python
height_matrix: numpy.typing.NDArray[numpy.float32]
```

Get the height matrix data as a numpy array.
    
    Note:
        The returned array is a copy of the internal data. Modifying it will not affect the
        hfield.
    
    Returns:
        NDArray[float]: A 2D numpy array of shape (nrow, ncol) containing the height values.

### index

```python
index: int
```

The index of the hfield in the scene.

### model

```python
model: SceneModel
```

The scene model that this hfield belongs to.

### name

```python
name: Optional[str]
```

The name of the hfield. Must be unique within the scene.
    
    Returns:
        Optional[str]: The name of the hfield, or "None" if not set.

### ncol

```python
ncol: int
```

The number of columns in the height field grid.

### nrow

```python
nrow: int
```

The number of rows in the height field grid.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get` | `(self, row: int, col: int) -> float` | Get the height value at the specified row and column. |

### get

```python
def get(self, row: int, col: int) -> float
```

Get the height value at the specified row and column.
        
        Args:
            row: The row index (0-based).
            col: The column index (0-based).
        Returns:
            float: The height value at the specified grid cell.
