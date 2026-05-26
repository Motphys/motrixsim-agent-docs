# motrixsim.ik.IkChain

Module: [`motrixsim.ik`](../modules/motrixsim.ik.md)

Represents a kinematic chain for inverse kinematics (IK) solving.
    
    Args:
        model: The scene model containing the kinematic structure.
        end_link: The name of the end link of the IK chain.
        start_link: The name of the start link of the IK chain. If not provided,
            the root link will be used.
        end_effector_offset: A 7-element array representing the end-effector
            offset as a pose (x, y, z, i, j, k, w) in end link's local space. If not provided, no
            offset will be applied.
    Raises:
       RuntimeError: If the IK chain contains unsupported joint types. (Currently only hinge and
            slider are supported.)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `num_dof_pos` | `int` | Get the number of DoF positions in the IK chain. |
| `num_dof_vel` | `int` | Get the number of DoF velocities in the IK chain. |
| `num_links` | `int` | Get the number of links in the IK chain. |

### num_dof_pos

```python
num_dof_pos: int
```

Get the number of DoF positions in the IK chain.
    
    Returns:
        int: The number of degree of freedom positions.

### num_dof_vel

```python
num_dof_vel: int
```

Get the number of DoF velocities in the IK chain.
    
    Returns:
        int: The number of degree of freedom velocities.

### num_links

```python
num_links: int
```

Get the number of links in the IK chain.
    
    Returns:
        int: The number of links in the chain.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, model: SceneModel, end_link: str, start_link: Optional[str] = None, end_effector_offset: Optional[Any] = None) -> IkChain` |  |
| `get_bias_force` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the joint space bias force of the chain. |
| `get_dof_pos` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF positions of the IK chain from the simulation data. |
| `get_dof_vel` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the DoF velocities of the IK chain from the simulation data. |
| `get_end_effector_jac` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the Jacobian matrix of the end effector. |
| `get_end_effector_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the end effector pose in world coordinates. |
| `get_end_effector_vel` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the end effector velocity in world coordinates. |
| `get_end_point_jac` | `(self, data: SceneData, end_point: Any) -> numpy.typing.NDArray[numpy.float32]` | Get the Jacobian matrix of a specific point fixed to the end link. |
| `get_inertia_matrix` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the joint space inertia matrix of the chain. |
| `get_link` | `(self, index: int) -> Link` | Get the link at the specified index in the IK chain. |

### __new__

```python
def __new__(cls, model: SceneModel, end_link: str, start_link: Optional[str] = None, end_effector_offset: Optional[Any] = None) -> IkChain
```

### get_bias_force

```python
def get_bias_force(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the joint space bias force of the chain.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The joint space bias force of the chain. Shape: ``(*data.shape, num_dof_vel)``.

### get_dof_pos

```python
def get_dof_pos(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF positions of the IK chain from the simulation data.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The DoF positions of the chain. Shape: ``(*data.shape, num_dof_pos)``.

### get_dof_vel

```python
def get_dof_vel(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the DoF velocities of the IK chain from the simulation data.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The DoF velocities of the chain. Shape: ``(*data.shape, num_dof_vel)``.

### get_end_effector_jac

```python
def get_end_effector_jac(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the Jacobian matrix of the end effector.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The Jacobian matrix of the end effector. Shape: ``(*data.shape, 6,
        num_dof_vel)``.         The first 3 rows are angular velocity, the last 3 rows are
        linear         velocity.

### get_end_effector_pose

```python
def get_end_effector_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the end effector pose in world coordinates.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The end effector pose array. Shape: ``(*data.shape, 7)``. Each pose is a
        7-element         array with `[x, y, z, i, j, k, w]` format.

### get_end_effector_vel

```python
def get_end_effector_vel(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the end effector velocity in world coordinates.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The end effector velocity array. Shape: ``(*data.shape, 6)``. Each velocity is
        a 6-element array with first 3 elements representing angular velocity and last 3
        elements representing linear velocity.

### get_end_point_jac

```python
def get_end_point_jac(self, data: SceneData, end_point: Any) -> numpy.typing.NDArray[numpy.float32]
```

Get the Jacobian matrix of a specific point fixed to the end link.
        
        Args:
            data: The scene data containing the current state.
            end_point: A 3-element array representing the point in the end link's local
        frame.
        
        Returns:
            ndarray: The Jacobian matrix of the specified point. Shape: ``(*data.shape, 6,
        num_dof_vel)``.         The first 3 rows are angular velocity, the last 3 rows are
        linear         velocity.

### get_inertia_matrix

```python
def get_inertia_matrix(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the joint space inertia matrix of the chain.
        
        Args:
            data: The scene data containing the current state.
        
        Returns:
            ndarray: The joint space inertia matrix of the chain. Shape: ``(*data.shape,
        chain.num_dof_vel, chain.num_dof_vel)``.

### get_link

```python
def get_link(self, index: int) -> Link
```

Get the link at the specified index in the IK chain.
        
        Args:
            index: The index of the link in the chain (0-based).
        
        Returns:
            Link: The link object at the specified index.
        
        Raises:
            IndexError: If the index is out of bounds.
