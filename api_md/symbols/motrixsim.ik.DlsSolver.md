# motrixsim.ik.DlsSolver

Module: [`motrixsim.ik`](../modules/motrixsim.ik.md)

Use Damped Least Squares (DLS) method to solve inverse kinematics problem.

    DLS is a robust optimization method that adds regularization to handle singular
    configurations and improve numerical stability. It's also known as Levenberg-Marquardt
    for IK applications.

    Args:
       max_iter: Maximum number of iterations (default: 100).
       step_size: Step size for each iteration when adaptive_damping is False
           (default: 0.5).
       tolerance: Tolerance for convergence (default: 1e-3).
       damping: Initial damping parameter for regularization (default: 1e-3).
           - Small values (1e-6 to 1e-4): Near Gauss-Newton behavior
           - Medium values (1e-4 to 1e-2): Good balance for most applications
           - Large values (1e-2 to 1.0): More stable but slower convergence
       adaptive_damping: Whether to adapt damping with Levenberg-Marquardt
           trust-region logic. When True, step_size is ignored (default: True).

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, max_iter: int = 100, step_size: float = 0.5, tolerance: float = 0.0010000000474974513, damping: float = 0.0010000000474974513, adaptive_damping: bool = True) -> DlsSolver` |  |
| `solve` | `(self, ik_model: Any, data: SceneData, target_pose: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> numpy.typing.NDArray[numpy.float32]` | Solve the IK problem for the given chain and target pose. |

### __new__

```python
def __new__(cls, max_iter: int = 100, step_size: float = 0.5, tolerance: float = 0.0010000000474974513, damping: float = 0.0010000000474974513, adaptive_damping: bool = True) -> DlsSolver
```

### solve

```python
def solve(self, ik_model: Any, data: SceneData, target_pose: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> numpy.typing.NDArray[numpy.float32]
```

Solve the IK problem for the given chain and target pose.

        Args:
            ik_model: The IK model. Currently only `IkChain` is supported.
            data: The scene data containing the current state.
            target_pose: The target pose the end effector want to reach.
                It is a 7-element array with (x, y, z, i, j, k, w) format.

        Returns:
          A numpy array with shape `(data.shape, ik_model.num_dof_pos + 2,)`. For each row, the
          first element is the number of iterations used, the second element is the final
          residual, and the remaining elements are the solved DOF positions.
