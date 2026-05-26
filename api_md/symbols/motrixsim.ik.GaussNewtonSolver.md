# motrixsim.ik.GaussNewtonSolver

Module: [`motrixsim.ik`](../modules/motrixsim.ik.md)

Use gauss newton iterative method to solve inverse kinematics problem.
    
    Args:
       max_iter: Maximum number of iterations (default: 100).
       step_size: Step size for each iteration (default: 0.5).
       tolerance: Tolerance for convergence (default: 1e-3).

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, max_iter: int = 100, step_size: float = 0.5, tolerance: float = 0.0010000000474974513) -> GaussNewtonSolver` |  |
| `solve` | `(self, ik_model: Any, data: SceneData, target_pose: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> numpy.typing.NDArray[numpy.float32]` | Solve the IK problem for the given chain and target pose. |

### __new__

```python
def __new__(cls, max_iter: int = 100, step_size: float = 0.5, tolerance: float = 0.0010000000474974513) -> GaussNewtonSolver
```

### solve

```python
def solve(self, ik_model: Any, data: SceneData, target_pose: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> numpy.typing.NDArray[numpy.float32]
```

Solve the IK problem for the given chain and target pose.
        
        Args:
            ik_model: The IK model. Currently only `IkChain` is supported.
            data: The scene data containing the current state.
                target_pose: The target pose the end effector want to reach.  It is
                a 7-element array with (x, y, z, i, j, k, w) format.
        
        Returns:
          A numpy array with shape `(data.shape, ik_model.num_dof_pos + 2,)`. For each row, the
          first element   is the number of iterations used, the second element is the final
          residual, and the   remaining elements are the solved DOF positions.
