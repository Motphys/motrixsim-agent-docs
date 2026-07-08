# motrixsim.SceneModel

Module: [`motrixsim`](../modules/motrixsim.md)

The SceneModel object represents the entire simulation world.

    This class provides a high-level interface to access and manipulate the simulation world model,
    including all bodies, joints, actuators, links, and sites. Users can query the scene structure
    and configuration, modify simulation options, and access components through properties
    (`joints`, `options`) or methods (`get_body()`, `get_sensor_values()`).

## Properties

| Name | Type | Description |
|------|------|-------------|
| `actuator_ctrl_limits` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The actuator control ranges. |
| `actuator_names` | `list[Optional[str]]` | List[Optional[str]]: The list of actuator names in the world. |
| `actuators` | `list[Actuator]` | Get all actuators defined in the model. |
| `bodies` | `list[Body]` | List[Body]: The list of all bodies in the world. |
| `body_names` | `list[Optional[str]]` | List[Optional[str]]: The list of all body names in the world. |
| `cameras` | `CameraMgr` | The camera manager for accessing cameras by name. |
| `floating_bases` | `list[FloatingBase]` | List[FloatingBase]: The list of all floating bases in the world. |
| `geom_names` | `list[Optional[str]]` | List[Optional[str]]: The list of all geoms names in the world. |
| `geoms` | `list[Geom]` | List[Geom]: The list of all geoms in the world. |
| `joint_dof_pos_indices` | `list[int]` | List[int]: The start dof index for each joint in the dof positions array. |
| `joint_dof_pos_nums` | `list[int]` | List[int]: The number of DoF positions for each joint. |
| `joint_dof_vel_indices` | `list[int]` | List[int]: The start dof index for each joint in the dof velocities array. |
| `joint_dof_vel_nums` | `list[int]` | List[int]: The size of DoF velocities of each joint. |
| `joint_limits` | `numpy.typing.NDArray[numpy.float32]` | NDArray[float]: The joint position limits for each joint. |
| `joint_names` | `list[Optional[str]]` | List[Optional[str]]: The list of all joint names in the world. |
| `joints` | `list[Joint]` | List[Joint]: The list of all joints in the world. |
| `keyframes` | `list[Keyframe]` | List[Keyframe]: The list of all keyframes in the model. |
| `link_names` | `list[Optional[str]]` | List[Optional[str]]: The list of all link names in the world. |
| `links` | `list[Link]` | List[Link]: The list of all links in the world. |
| `low` | `LowSceneModel` | The low-level model for advanced or internal simulation access. |
| `num_actuators` | `int` | The number of actuators in the world. |
| `num_bodies` | `int` | The number of bodies in the world. |
| `num_dof_pos` | `int` | The number of DoF positions in the world. |
| `num_dof_vel` | `int` | The number of DoF velocities in the world. |
| `num_geoms` | `int` | The number of geoms in the world. |
| `num_hfields` | `int` | The number of height fields in the world. |
| `num_joints` | `int` | The number of joints in the world. |
| `num_keyframes` | `int` | The number of keyframes in the model. |
| `num_links` | `int` | The number of links in the world. |
| `num_sensors` | `int` | The number of sensors in the world. |
| `num_sites` | `int` | The number of sites in the world. |
| `options` | `Options` | The simulation options of the model. |
| `reports` | `ReportFlags` | Toggles for runtime report generation. |
| `site_names` | `list[str]` | List[str]: The list of all site names in the world. |
| `sites` | `list[Site]` | List[Site]: The list of all sites in the world. |

### actuator_ctrl_limits

```python
actuator_ctrl_limits: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The actuator control ranges.

    Return a 2-dimensional numpy array with shape (2, num_actuators).
    The first dimension is the minimum control value, and the second dimension is the
    maximum control value.
    If the limits do not set for a actuator, `(-inf, inf)` will be used as the limits.

### actuator_names

```python
actuator_names: list[Optional[str]]
```

List[Optional[str]]: The list of actuator names in the world.

    Return list of actuator names, can be `None` if the actuator does not have a name.

### actuators

```python
actuators: list[Actuator]
```

Get all actuators defined in the model.

    Returns:
      List[Actuator]: A list of all actuator objects in the world.

### bodies

```python
bodies: list[Body]
```

List[Body]: The list of all bodies in the world.

    Note:
        don't confuse the body in motrixsim with the body in mjcf. See
        /user_guide/kinematics/body for more details.

### body_names

```python
body_names: list[Optional[str]]
```

List[Optional[str]]: The list of all body names in the world.

    Return list of body names, can be `None` if the body does not have a name.

### cameras

```python
cameras: CameraMgr
```

The camera manager for accessing cameras by name.

### floating_bases

```python
floating_bases: list[FloatingBase]
```

List[FloatingBase]: The list of all floating bases in the world.

### geom_names

```python
geom_names: list[Optional[str]]
```

List[Optional[str]]: The list of all geoms names in the world.

    A list of geom names, can be `None` if the geom does not have a name.

### geoms

```python
geoms: list[Geom]
```

List[Geom]: The list of all geoms in the world.

### joint_dof_pos_indices

```python
joint_dof_pos_indices: list[int]
```

List[int]: The start dof index for each joint in the dof positions array.

    A list of start indices for each joint's dof positions in the dof positions array.
    size = num_joints.

    Note:
        The DoF of floating base is not included.

### joint_dof_pos_nums

```python
joint_dof_pos_nums: list[int]
```

List[int]: The number of DoF positions for each joint.

    List of position DoF sizes for each joint.
    size = num_joints

### joint_dof_vel_indices

```python
joint_dof_vel_indices: list[int]
```

List[int]: The start dof index for each joint in the dof velocities array.

    A list of start indices for each joint's dof velocities in the dof velocities array.

    Note:
        The DoF of floating base is not included.

### joint_dof_vel_nums

```python
joint_dof_vel_nums: list[int]
```

List[int]: The size of DoF velocities of each joint.

    List of velocity DoF sizes for each joint.
    size = num_joints.

### joint_limits

```python
joint_limits: numpy.typing.NDArray[numpy.float32]
```

NDArray[float]: The joint position limits for each joint.

    A 2-dimensional numpy array with shape (2, num_joints).

    The first dimension is the minimum position limit, and the second dimension is the
    maximum position limit.
    If the limits are not set for a joint, `-inf, inf` will be used as the limits.

### joint_names

```python
joint_names: list[Optional[str]]
```

List[Optional[str]]: The list of all joint names in the world.

    Return list of joint names, can be `None` if the joint does not have a name.

### joints

```python
joints: list[Joint]
```

List[Joint]: The list of all joints in the world.

### keyframes

```python
keyframes: list[Keyframe]
```

List[Keyframe]: The list of all keyframes in the model.

### link_names

```python
link_names: list[Optional[str]]
```

List[Optional[str]]: The list of all link names in the world.

    A list of link names, can be `None` if the link does not have a name.

### links

```python
links: list[Link]
```

List[Link]: The list of all links in the world.

### low

```python
low: LowSceneModel
```

The low-level model for advanced or internal simulation access.

    This property exposes the underlying low-level scene model, which provides direct access
    to internal simulation data and advanced features.

    Note:
        Do not use this property unless you know what you are doing.

### num_actuators

```python
num_actuators: int
```

The number of actuators in the world.

### num_bodies

```python
num_bodies: int
```

The number of bodies in the world.

### num_dof_pos

```python
num_dof_pos: int
```

The number of DoF positions in the world.

### num_dof_vel

```python
num_dof_vel: int
```

The number of DoF velocities in the world.

    Note:
        This value may be different from the [`num_dof_pos`] because for some joint (like ball
        joint), we use Quaternion to represent the rotation, which has 4 components.

### num_geoms

```python
num_geoms: int
```

The number of geoms in the world.

### num_hfields

```python
num_hfields: int
```

The number of height fields in the world.

### num_joints

```python
num_joints: int
```

The number of joints in the world.

    Note:
        `freejoint` in MJCF is not considered as a joint but a floating base.

### num_keyframes

```python
num_keyframes: int
```

The number of keyframes in the model.

### num_links

```python
num_links: int
```

The number of links in the world.

    Note:
        The `worldbody` in MJCF is not considered as a link.

### num_sensors

```python
num_sensors: int
```

The number of sensors in the world.

### num_sites

```python
num_sites: int
```

The number of sites in the world.

### options

```python
options: Options
```

The simulation options of the model.

### reports

```python
reports: ReportFlags
```

Toggles for runtime report generation.

### site_names

```python
site_names: list[str]
```

List[str]: The list of all site names in the world.

### sites

```python
sites: list[Site]
```

List[Site]: The list of all sites in the world.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `compute_init_dof_pos` | `(self) -> numpy.typing.NDArray[numpy.float32]` | Compute the initial DoF positions for the world. |
| `forward_kinematic` | `(self, data: SceneData) -> None` | Perform forward kinematic calculations using the current model and data. |
| `get_actuator` | `(self, arg: Any) -> Optional[Actuator]` | Get an actuator by name or index. |
| `get_actuator_ctrls` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Alias to `SceneData.actuator_ctrls` |
| `get_actuator_index` | `(self, name: str) -> Optional[int]` | Get actuator index by its name. |
| `get_body` | `(self, key: Any) -> Optional[Body]` | Get a body by name or index. |
| `get_body_index` | `(self, name: str) -> Optional[int]` | Get the body index by its name. |
| `get_camera_poses` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world poses of all cameras. |
| `get_contact_query` | `(self, data: SceneData) -> ContactQuery` | Get a contact query object for the current model and data. |
| `get_geom` | `(self, arg: Any) -> Optional[Geom]` | Get a geom by name or index. |
| `get_geom_index` | `(self, name: str) -> Optional[int]` | Get the geometry index by its name. |
| `get_gravity_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the effective gravity override from the scene data. |
| `get_hfield` | `(self, slf: SceneModel, arg: Any) -> Optional[HField]` | Get an hfield by name or index. |
| `get_hfield_index` | `(self, name: str) -> Optional[int]` | Get hfield index by its name. |
| `get_joint` | `(self, key: Any) -> Optional[Joint]` | Get a joint by name or index. |
| `get_joint_index` | `(self, name: str) -> Optional[int]` | Get the joint index by its name. |
| `get_link` | `(self, arg: Any) -> Optional[Link]` | Get a link by name or index. |
| `get_link_angular_velocities` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world angular velocities of all links. |
| `get_link_index` | `(self, name: str) -> Optional[int]` | Get the link index by its name. |
| `get_link_linear_velocities` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world linear velocities of all links. |
| `get_link_poses` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world poses of all links. |
| `get_link_rotation_mats` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get all link rotation matrices. |
| `get_link_velocities` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world velocities (linear and angular) of all links. |
| `get_sensor_value` | `(self, id: str, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the value of a specific sensor by its ID. |
| `get_sensor_values` | `(self, names: Sequence[str], data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the values of multiple sensors by their names, concatenated into a single array. |
| `get_site` | `(self, key: Any) -> Optional[Site]` | Get a site by name or index. |
| `get_site_index` | `(self, name: str) -> Optional[int]` | Get site index by name. |
| `set_gravity_override` | `(self, data: SceneData, gravity: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the gravity vector for the scene data. |
| `step` | `(self, data: SceneData) -> None` | Advance the simulation by one step using the current model and data. |
| `step_n` | `(self, data: SceneData, n: int) -> None` | Advance the simulation by `n` steps using the current model and data. |

### compute_init_dof_pos

```python
def compute_init_dof_pos(self) -> numpy.typing.NDArray[numpy.float32]
```

Compute the initial DoF positions for the world.

        Returns:
            NDArray[float]: shape=(num_dof_pos,). Initial DoF positions.

### forward_kinematic

```python
def forward_kinematic(self, data: SceneData) -> None
```

Perform forward kinematic calculations using the current model and data.

        Note:
          This method only updates the world poses of all links and bodies based on the current
          joint positions.

### get_actuator

```python
def get_actuator(self, arg: Any) -> Optional[Actuator]
```

Get an actuator by name or index.

        Args:
            key: Name or index of the actuator.

        Returns:
            Optional[Actuator]: The actuator object, or `None` if not found.

### get_actuator_ctrls

```python
def get_actuator_ctrls(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Alias to `SceneData.actuator_ctrls`

### get_actuator_index

```python
def get_actuator_index(self, name: str) -> Optional[int]
```

Get actuator index by its name.

        Args:
            name: Name of the actuator.

        Returns:
            Optional[int]: Index of the actuator, or `None` if not found.

### get_body

```python
def get_body(self, key: Any) -> Optional[Body]
```

Get a body by name or index.

        Args:
            key: Name or index of the body.

        Returns:
            Optional[Body]: The body object, or `None` if not found.

### get_body_index

```python
def get_body_index(self, name: str) -> Optional[int]
```

Get the body index by its name.

        Args:
            name: Name of the body.

        Returns:
            Optional[int]: Index of the body, or `None` if not found.

### get_camera_poses

```python
def get_camera_poses(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world poses of all cameras.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape,num_cameras, 7)`. Each pose is
            composed of `[x, y, z, qx, qy, qz, qw]`,

        Note:
            If there are no cameras in the scene, returns an array with shape `(*data.shape, 0, 7)`.

### get_contact_query

```python
def get_contact_query(self, data: SceneData) -> ContactQuery
```

Get a contact query object for the current model and data.

        Args:
           data: Scene data.

        Returns:
          ContactQuery: A contact query object that can be used to query contacts in the world.

### get_geom

```python
def get_geom(self, arg: Any) -> Optional[Geom]
```

Get a geom by name or index.

        Args:
            key: Name or index of the geom.

        Returns:
            Optional[Geom]: The geom object, or `None` if not found.

### get_geom_index

```python
def get_geom_index(self, name: str) -> Optional[int]
```

Get the geometry index by its name.

        Args:
            name: Name of the geometry.

        Returns:
            Optional[int]: Index of the geometry, or `None` if not found.

### get_gravity_override

```python
def get_gravity_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective gravity override from the scene data.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: Gravity vector. Shape: ``(*data.shape, 3)``.

### get_hfield

```python
def get_hfield(self, slf: SceneModel, arg: Any) -> Optional[HField]
```

Get an hfield by name or index.

        Args:
            key: Name or index of the hfield.

        Returns:
            Optional[HField]: The hfield object, or `None` if not found.

### get_hfield_index

```python
def get_hfield_index(self, name: str) -> Optional[int]
```

Get hfield index by its name.

        Args:
            name: Name of the hfield.

        Returns:
            Optional[int]: Index of the hfield, or `None` if not found.

### get_joint

```python
def get_joint(self, key: Any) -> Optional[Joint]
```

Get a joint by name or index.

        Args:
            key: Name or index of the joint.

        Returns:
            Optional[Joint]: The joint object, or `None` if not found.

### get_joint_index

```python
def get_joint_index(self, name: str) -> Optional[int]
```

Get the joint index by its name.

        Args:
            name: Name of the joint.

        Returns:
            Optional[int]: Index of the joint, or `None` if not found.

### get_link

```python
def get_link(self, arg: Any) -> Optional[Link]
```

Get a link by name or index.

        Args:
            key: Name or index of the link.

        Returns:
            Optional[Link]: The link object, or `None` if not found.

### get_link_angular_velocities

```python
def get_link_angular_velocities(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world angular velocities of all links.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, num_links, 3)`. Each velocity is
            composed of `[wx, wy, wz]`.

### get_link_index

```python
def get_link_index(self, name: str) -> Optional[int]
```

Get the link index by its name.

        Args:
            name: Name of the link.

        Returns:
            Optional[int]: Index of the link, or `None` if not found.

### get_link_linear_velocities

```python
def get_link_linear_velocities(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world linear velocities of all links.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, num_links, 3)`. Each velocity is
            composed of `[vx, vy, vz]`.

### get_link_poses

```python
def get_link_poses(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world poses of all links.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape,num_links, 7)`. Each pose is
            composed of `[x, y, z, i, j, k, w]`,

### get_link_rotation_mats

```python
def get_link_rotation_mats(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get all link rotation matrices.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape,num_links, 3, 3)`. Each rotation
        matrix is in column-major order.

### get_link_velocities

```python
def get_link_velocities(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world velocities (linear and angular) of all links.

        Args:
            data: Scene data.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, num_links, 6)`. Each velocity is
            composed of `[vx, vy, vz, wx, wy, wz]`.

### get_sensor_value

```python
def get_sensor_value(self, id: str, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the value of a specific sensor by its ID.

        Args:
            id: Sensor ID.
            data: Scene data.

        Returns:
            NDArray[float]: Sensor values. Shape: ``(*data.shape, sensor_value_size)``

### get_sensor_values

```python
def get_sensor_values(self, names: Sequence[str], data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the values of multiple sensors by their names, concatenated into a single array.

        Args:
            names: List of sensor names.
            data: Scene data.

        Returns:
            NDArray[float]: Concatenated sensor values with shape
            ``(*data.shape, total_sensor_values)`` where ``total_sensor_values`` is the sum of
            all queried sensors' value sizes.

### get_site

```python
def get_site(self, key: Any) -> Optional[Site]
```

Get a site by name or index.

        Args:
            key: Name or index of the site.

        Returns:
            Optional[Site]: The site object, or `None` if not found.

### get_site_index

```python
def get_site_index(self, name: str) -> Optional[int]
```

Get site index by name.

        Args:
            name: Name of the site.

        Returns:
            Optional[int]: Index of the site, or `None` if not found.

### set_gravity_override

```python
def set_gravity_override(self, data: SceneData, gravity: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the gravity vector for the scene data.

        Args:
            data: Scene data to modify.
            gravity: The new gravity vector.
                - Shape ``(3,)``: Single value applied to all batches
                - Shape ``(*data.shape, 3)``: Per-batch values

        Note:
            If any gravity component is NaN or infinite, the override will be ignored.

### step

```python
def step(self, data: SceneData) -> None
```

Advance the simulation by one step using the current model and data.

        Note:
            If the data has batch dimension, motrixsim will run simulation in parallel

### step_n

```python
def step_n(self, data: SceneData, n: int) -> None
```

Advance the simulation by `n` steps using the current model and data.

        Args:
            data: Scene data.
            n: Number of steps to advance the simulation.

        Note:
            This method can skip the python overhead when stepping multiple times.
