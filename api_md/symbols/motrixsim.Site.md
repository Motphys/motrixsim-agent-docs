# motrixsim.Site

Module: [`motrixsim`](../modules/motrixsim.md)

The Site object represents a reference point or marker in the scene.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `dof_vel_indices` | `numpy.typing.NDArray[numpy.int64]` | Global DoF velocity indices that affect this site. |
| `index` | `int` | The index of the site in the site list. |
| `local_pos` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The local position of the site in the parent frame in (x, y, z). |
| `local_quat` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The local orientation of the site as a quaternion (i, j, k, w). |
| `model` | `SceneModel` | The model that this site belongs to. |
| `name` | `Optional[str]` | The name of the site, or `None` if not set. |
| `parent_link` | `Optional[Link]` | The parent link of the site, or `None` if the site is attached to the world frame. |

### dof_vel_indices

```python
dof_vel_indices: numpy.typing.NDArray[numpy.int64]
```

Global DoF velocity indices that affect this site.

    Returns:
        NDArray[int]: Shape ``(k,)`` where k is the number of DoFs on the kinematic path
            from root to this site's parent link.

    Note:
        This is a model property determined by the kinematic tree topology. It does not
        depend on simulation state and can be cached by the user.

### index

```python
index: int
```

The index of the site in the site list.

### local_pos

```python
local_pos: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The local position of the site in the parent frame in (x, y, z).

### local_quat

```python
local_quat: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The local orientation of the site as a quaternion (i, j, k, w).

### model

```python
model: SceneModel
```

The model that this site belongs to.

### name

```python
name: Optional[str]
```

The name of the site, or `None` if not set.

### parent_link

```python
parent_link: Optional[Link]
```

The parent link of the site, or `None` if the site is attached to the world frame.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_jacobian` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the compact Jacobian matrix of the site. |
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the pose of the site in the world frame. |
| `get_position` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the position of the site in the world frame. |
| `get_rotation_mat` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the rotation matrix of the site in the world frame. |

### get_jacobian

```python
def get_jacobian(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the compact Jacobian matrix of the site.

        The Jacobian maps DoF velocities to the site's spatial velocity in world frame.
        Only columns corresponding to ``dof_vel_indices`` are included.

        Args:
            data: The scene data containing the current state.

        Returns:
            NDArray[float]: Shape ``(*data.shape, 6, k)`` where k equals
                ``len(self.dof_vel_indices)``. The first 3 rows are angular velocity,
                the last 3 rows are linear velocity.

### get_pose

```python
def get_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the pose of the site in the world frame.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The pose of the site in the world frame. Shape: ``(*data.shape,7)``. The
            last axis is 7-element array with `[x, y, z, i, j, k, w]`.

### get_position

```python
def get_position(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the position of the site in the world frame.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The position of the site in the world frame. Shape: ``(*data.shape,3)``.

### get_rotation_mat

```python
def get_rotation_mat(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the rotation matrix of the site in the world frame.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[float]: The rotation matrix of the site in the world frame. shape =
                `(*data.shape,3,3)`.
