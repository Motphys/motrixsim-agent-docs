# motrixsim.osc.OscSolver

Module: [`motrixsim.osc`](../modules/motrixsim.osc.md)

Operational Space Controller Solver.
    
    Pure functional interface - no internal state.
    Users manage IkChain and targets themselves.
    
    Args:
        control_ori: Whether to control orientation. Default True.
        uncouple_pos_ori: Whether to decouple position/orientation. Default True.
        kp: Position/orientation gains. Default 150.0.
        damping_ratio: Damping ratio for velocity gains. Default 1.0.
        nullspace_kp: Nullspace position gain. Default 10.0.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, control_ori: bool = True, uncouple_pos_ori: bool = True, kp: Optional[Any] = None, damping_ratio: float = 1.0, nullspace_kp: float = 10.0) -> OscSolver` |  |
| `solve` | `(self, chain: IkChain, ee_target_pos: Any, ee_target_ori: Any, nullspace_joint_pos: Any, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Compute joint torques to track end-effector target. |

### __new__

```python
def __new__(cls, control_ori: bool = True, uncouple_pos_ori: bool = True, kp: Optional[Any] = None, damping_ratio: float = 1.0, nullspace_kp: float = 10.0) -> OscSolver
```

### solve

```python
def solve(self, chain: IkChain, ee_target_pos: Any, ee_target_ori: Any, nullspace_joint_pos: Any, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Compute joint torques to track end-effector target.
        
        Args:
            chain: The kinematic chain (user manages this).
            ee_target_pos: Target position in world frame.
                Shape: ``(*data.shape, 3)`` [x, y, z]
            ee_target_ori: Target orientation as axis-angle.
                Shape: ``(*data.shape, 3)`` [ax, ay, az]
            nullspace_joint_pos: Target joint positions for nullspace control.
                Shape: ``(*data.shape, num_dof)``
            data: Current simulation data.
        
        Returns:
            ndarray: Joint torques. Shape: ``(*data.shape, num_dof)``.
