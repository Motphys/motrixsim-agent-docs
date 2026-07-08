# motrixsim.Options

Module: [`motrixsim`](../modules/motrixsim.md)

The Options object represents the simulation options.

    This class is used to configure the simulation options. You can access it through
    `model.options`.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `_convex_strategy` | `str` | The convex hull generation strategy. |
| `disable_contacts` | `bool` | Is all contact constraints disabled in the simulation? |
| `disable_gravity` | `bool` | Is the gravity disabled in the simulation? |
| `gravity` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The gravity vector applied to the simulation. |
| `max_iterations` | `int` | The maximum number of iterations for the solver. |
| `solver_tolerance` | `float` | The tolerance for the solver. |
| `timestep` | `float` | The delta time for each simulation step. |

### _convex_strategy

```python
_convex_strategy: str
```

The convex hull generation strategy.

    Returns "quick_convex" or "q_hull".

    Note:
        - quick_convex: Fast approximation algorithm (default)
        - q_hull: Exact algorithm (only available if compiled with qhull feature)

### disable_contacts

```python
disable_contacts: bool
```

Is all contact constraints disabled in the simulation?

### disable_gravity

```python
disable_gravity: bool
```

Is the gravity disabled in the simulation?

### gravity

```python
gravity: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The gravity vector applied to the simulation.

    A numpy array of shape (3,) or a list of three floats representing the  gravity vector.

### max_iterations

```python
max_iterations: int
```

The maximum number of iterations for the solver.

    Raises:
        `ValueError`: The set max iterations is zero.

### solver_tolerance

```python
solver_tolerance: float
```

The tolerance for the solver.

    Raises:
        `ValueError`: The set tolerance is not positive.

### timestep

```python
timestep: float
```

The delta time for each simulation step.

    Raises:
        `ValueError`: The set timestep is not positive.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__str__` | `(self) -> str` |  |

### __str__

```python
def __str__(self) -> str
```
