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
| `mesh_variant_sets` | `dict[str, list[str]]` | Compiled mesh variant sets keyed by their declared name. |
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
| `sensors` | `SensorCollection` | Read-only compiled sensor descriptors in model order. |
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

### mesh_variant_sets

```python
mesh_variant_sets: dict[str, list[str]]
```

Compiled mesh variant sets keyed by their declared name.

    Returns:
        Dict[str, List[str]]: Set name to the ordered mesh asset names declared in that set.
            The position of a name in the list is the set-local variant ordinal accepted by
            ``Geom.set_shape_override`` (``Shape.Mesh`` rows) and reported by
            ``Geom.get_mesh_variant_override``.

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

### sensors

```python
sensors: SensorCollection
```

Read-only compiled sensor descriptors in model order.

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
| `compile_query` | `(self, fields: Any) -> QueryPlan` | Compile a reusable model-bound physics data query plan. |
| `compile_write` | `(self, fields: Any, *, reset: bool = False, reset_overrides: bool = True, forward_kinematic: bool = False) -> WritePlan` | Compile a reusable model-bound physics data write plan. |
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
| `get_lidar_status` | `(self, id: str, data: SceneData) -> LidarScanStatus` | Get measurement status for a LiDAR sensor. |
| `get_link` | `(self, arg: Any) -> Optional[Link]` | Get a link by name or index. |
| `get_link_angular_velocities` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the world angular velocities of all links. |
| `get_link_index` | `(self, name: str) -> Optional[int]` | Get the link index by its name. |
| `get_link_linear_velocities` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the world linear velocities of all links. |
| `get_link_net_contact_forces` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the net contact force acting on each link, resolved at the link center of mass. |
| `get_link_poses` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the world poses of all links. |
| `get_link_rotation_mats` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get all link rotation matrices. |
| `get_link_states` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, quat_order: str = 'xyzw', out_pos: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_quat: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_linvel: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_angvel: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32]]` | Get the world states (pose and velocity) of links in a single call. |
| `get_link_velocities` | `(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the world velocities (linear and angular) of all links. |
| `get_sensor_value` | `(self, id: str, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the value of a specific sensor by its ID. |
| `get_sensor_values` | `(self, names: Sequence[str], data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the values of multiple sensors by their names, concatenated into a single array. |
| `get_site` | `(self, key: Any) -> Optional[Site]` | Get a site by name or index. |
| `get_site_index` | `(self, name: str) -> Optional[int]` | Get site index by name. |
| `raycast_closest` | `(self, data: SceneData, origin: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], direction: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], max_distance: float, *, out: Optional[tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.int64]]] = None) -> tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.int64]]` | Cast one ray per scene instance and return the nearest hits. |
| `set_gravity_override` | `(self, data: SceneData, gravity: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the gravity vector for the scene data. |
| `step` | `(self, data: SceneData, result: Optional[numpy.typing.NDArray[numpy.int32]] = None) -> None` | Advance the simulation by one step using the current model and data. |
| `step_n` | `(self, data: SceneData, n: int, result: Optional[numpy.typing.NDArray[numpy.int32]] = None) -> None` | Advance the simulation by `n` steps using the current model and data. |

### compile_query

```python
def compile_query(self, fields: Any) -> QueryPlan
```

Compile a reusable model-bound physics data query plan.

        Args:
            fields: Named fixed-width query sources. Mapping iteration
                order determines the contiguous output buffer layout.

        Returns:
            QueryPlan: Compiled query plan whose names, indices, shapes, and offsets are resolved.

        Raises:
            TypeError: If fields is not a mapping of names to QuerySource objects.
            ValueError: If a field name, link index, sensor name, or body name is invalid.

### compile_write

```python
def compile_write(self, fields: Any, *, reset: bool = False, reset_overrides: bool = True, forward_kinematic: bool = False) -> WritePlan
```

Compile a reusable model-bound physics data write plan.

        Args:
            fields: Named fixed-width write sources. Mapping iteration
                order determines the contiguous write buffer layout and the order in which the
                writes are applied during execution.
            reset: Whether every execution of programs allocated from this plan
                first restores each selected world to the model initial state before applying the
                writes. The reset also clears per-instance state not covered by the plan, such as
                actuator kp/damping, link mass/center-of-mass, and geom friction overrides; those
                are only restored if the plan writes them again. The initial state is built
                lazily per execution, so no allocation happens while reset is False. Defaults to
                False.
            reset_overrides: Whether the plan-level reset also restores the
                Data-side override buffers (inertias, physics materials, joint armatures,
                friction losses, geom shape overrides) to the Model defaults. Ignored when
                ``reset`` is False. Defaults to True; pass False to keep per-instance
                randomized overrides across executions.
            forward_kinematic: Whether every execution of programs allocated from
                this plan runs forward kinematics after applying the writes. Defaults to False.

        Note:
            ``AddBodyLinearVelocity`` adds world-frame XYZ increments to the current floating-base
            velocity DoF, or to the initial velocity after a plan-level reset. Its reusable buffer
            is not cleared on execution. Set/add and add/add writes to the same linear velocity
            channel are rejected at compile time.

        Returns:
            WritePlan: Compiled write plan whose names, indices, target types, and channels are
                resolved; duplicate writes to the same underlying channel are rejected.

        Raises:
            TypeError: If fields is not a mapping of names to WriteSource objects.
            ValueError: If a field name, target name, or target index is invalid, a target type
                does not support the requested write, or two fields write the same channel.

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
            Updates kinematic outputs without advancing simulation time or changing DoF positions
            and velocities. Measurements that require a physics step are not updated.

            Static LiDAR refreshes on every call. Raycast cameras capture only when no valid frame
            exists after initialization or reset. Once an image exists, repeated calls keep that
            image and do not bypass ``update_period``. Changing DoF positions directly does not
            invalidate the cached image, so it may not match the current pose.

            Rolling LiDAR is not measured by this method. After reset, ``get_lidar_status()``
            reports ``ready=False`` until physics steps complete a full new scan according to
            ``hz``. Cached pre-reset readings may remain available but are not valid observations
            of the new episode. Without reset, an unfinished scan continues on subsequent steps.
            Indexed data updates only the selected environments.

        Raises:
            RuntimeError: If the scene data belongs to a different model.

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

### get_lidar_status

```python
def get_lidar_status(self, id: str, data: SceneData) -> LidarScanStatus
```

Get measurement status for a LiDAR sensor.

        Args:
            id: LiDAR sensor name.
            data: Scene data, optionally batched or indexed.

        Returns:
            LidarScanStatus: Boolean ready and uint64 scan_seq arrays with data.shape.

        Note:
            Sensor payload remains available only through get_sensor_value(). Unknown names
            and non-LiDAR sensors raise RuntimeError. Fresh SceneData starts with ready=False and
            scan_seq=0. SceneData.reset() retains cached outputs but immediately makes ready=False
            for selected environments; sequence numbers remain monotonic. Forward kinematics
            refreshes static LiDAR, but does not measure rolling LiDAR. Rolling LiDAR becomes ready
            only after physics steps complete a full new scan. Repeated status queries do not
            trigger a measurement.

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
def get_link_angular_velocities(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the world angular velocities of all links.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 3)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 3)`. Each velocity is
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
def get_link_linear_velocities(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the world linear velocities of all links.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 3)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 3)`. Each velocity is
            composed of `[vx, vy, vz]`.

### get_link_net_contact_forces

```python
def get_link_net_contact_forces(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the net contact force acting on each link, resolved at the link center of mass.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 6)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 6)`. Each row is composed of
            `[fx, fy, fz, tx, ty, tz]`: the net contact force (3) and the net contact moment about
            the link center of mass (3), both expressed in world frame.

        Note:
            This query reads the contact force report, which is disabled by default. Enable it
            explicitly via `motrixsim.ReportFlags.contact_forces`
            (``model.reports.contact_forces = True``) and step the simulation once before reading;
            otherwise a ``RuntimeError`` is raised. The query is read-only and never toggles the
            switch itself.

### get_link_poses

```python
def get_link_poses(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the world poses of all links.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 7)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 7)`. Each pose is
            composed of `[x, y, z, i, j, k, w]`,

### get_link_rotation_mats

```python
def get_link_rotation_mats(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get all link rotation matrices.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 3, 3)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 3, 3)`. Each rotation
        matrix is in column-major order.

### get_link_states

```python
def get_link_states(self, data: SceneData, indices: Optional[Sequence[int]] = None, quat_order: str = 'xyzw', out_pos: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_quat: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_linvel: Optional[numpy.typing.NDArray[numpy.float32]] = None, out_angvel: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32]]
```

Get the world states (pose and velocity) of links in a single call.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            quat_order: Component order of the returned quaternions, either ``"xyzw"``
                (default) or ``"wxyz"``.

            out_pos: Pre-allocated output array of shape
                `(*data.shape, N, 3)` for positions. When provided, results are written into this
                array and it is returned directly, avoiding a per-call allocation.

            out_quat: Pre-allocated output array of shape
                `(*data.shape, N, 4)` for rotation quaternions, in ``quat_order`` component order.
                When provided, results are written into this array and it is returned directly,
                avoiding a per-call allocation.

            out_linvel: Pre-allocated output array of shape
                `(*data.shape, N, 3)` for linear velocities. When provided, results are written
                into this array and it is returned directly, avoiding a per-call allocation.

            out_angvel: Pre-allocated output array of shape
                `(*data.shape, N, 3)` for angular velocities. When provided, results are written
                into this array and it is returned directly, avoiding a per-call allocation.

        Returns:
            tuple[NDArray[float], NDArray[float], NDArray[float], NDArray[float]]: Four arrays
            `(pos, quat, linvel, angvel)` with shapes `(*data.shape, N, 3)`, `(*data.shape, N, 4)`,
            `(*data.shape, N, 3)` and `(*data.shape, N, 3)` respectively. Each position is
            `[x, y, z]`, each quaternion uses the requested ``quat_order`` (default
            `[qx, qy, qz, qw]`), each linear velocity is `[vx, vy, vz]` and each angular velocity is
            `[wx, wy, wz]`. The position/quaternion parts match `get_link_poses` and the
            velocity parts match `get_link_velocities`.

### get_link_velocities

```python
def get_link_velocities(self, data: SceneData, indices: Optional[Sequence[int]] = None, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the world velocities (linear and angular) of all links.

        Args:
            data: Scene data.

            indices: Link indices to query. When ``None`` (default), all
                links are returned in order. Otherwise only the selected links are returned, in the
                given order, and ``N`` below equals ``len(indices)``.

            out: Pre-allocated output array of shape
                `(*data.shape, N, 6)`. When provided, results are written into this array
                and it is returned directly, avoiding a per-call allocation.

        Returns:
            NDArray[float]: A numpy array with shape `(*data.shape, N, 6)`. Each velocity is
            composed of `[vx, vy, vz, wx, wy, wz]`.

### get_sensor_value

```python
def get_sensor_value(self, id: str, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the value of a specific sensor by its ID.

        Args:
            id: Sensor ID.
            data: Scene data.
            out: Contiguous preallocated array with shape
                ``(*data.shape, sensor_value_size)`` and the simulation scalar dtype.

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

### raycast_closest

```python
def raycast_closest(self, data: SceneData, origin: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], direction: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], max_distance: float, *, out: Optional[tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.int64]]] = None) -> tuple[numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.float32], numpy.typing.NDArray[numpy.int64]]
```

Cast one ray per scene instance and return the nearest hits.

        Args:
            data: Scene state, optionally batched or a selected view.
            origin: World-space origins with shape ``(3,)`` to broadcast,
                or ``(*data.shape, 3)`` for per-instance origins.
            direction: Finite, non-zero world-space directions with shape
                ``(3,)`` to broadcast, or ``(*data.shape, 3)`` for per-instance directions.
                Directions are normalized before querying.
            max_distance: Positive finite maximum distance in meters, shared by all rays.
            out: Pre-allocated distance, normal, and collider index arrays.
                Shapes and dtypes must match the returned arrays. Outputs must be writable,
                C-contiguous, and must not overlap each other or the inputs.
                Results are written directly into them.

        Returns:
            tuple[NDArray[float], NDArray[float], NDArray[int]]: Distance, outward
            normal, and collider index. Distance and index have shape
            ``data.shape``; normals have shape ``(*data.shape, 3)``.
            Non-batched scalar results are zero-dimensional arrays.
            Misses contain ``inf``, zero normal, and index ``-1``.
            A hit mask can be computed as ``collider_index >= 0``.
            Collider indices use int64; distances and normals use the engine precision.
            When out is provided, the same three array objects are returned.

        Note:
            Origin and direction broadcast independently and accept non-contiguous arrays.
            Call ``motrixsim.low.enable_immediate_raycast(model)`` before preparing snapshots
            with ``model.step(data)`` or ``model.forward_kinematic(data)``. After direct state
            edits, explicitly refresh the state before querying. This method does not enable
            snapshots or run forward kinematics. Empty batches do not require snapshots.
            Inputs, outputs, and snapshots are validated before any output is written.

        Raises:
            TypeError: An output array has an incorrect dtype.
            ValueError: Query values or output shape, layout, writability, or borrowing are invalid.
            RuntimeError: The data belongs to a different model or a broadphase snapshot is missing.

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
def step(self, data: SceneData, result: Optional[numpy.typing.NDArray[numpy.int32]] = None) -> None
```

Advance the simulation by one step using the current model and data.

        Args:
            data: Scene data.
            result: Optional writable C-contiguous output with shape
                ``data.shape``; use a zero-dimensional array for a single environment.

        Note:
            Status codes are 0 for success, 1 for LargeVelocity, 2 for NonFinite,
            3 for NonPositiveDefinite, and 4 for SingularSystem.
            Healthy instances continue even if another fails. Failure does not roll back state;
            reset failed instances before reuse. The output is overwritten on every call.
            With result=None, numerical failure raises RuntimeError after healthy instances finish.
            With an output array, numerical failures only write status codes.

        Raises:
            RuntimeError: If data belongs to a different model, or a numerical failure occurs
                without a result array.
            TypeError: If result is not an int32 ndarray.
            ValueError: If result has invalid shape, layout, writability, or borrowing.

### step_n

```python
def step_n(self, data: SceneData, n: int, result: Optional[numpy.typing.NDArray[numpy.int32]] = None) -> None
```

Advance the simulation by `n` steps using the current model and data.

        Args:
            data: Scene data.
            n: Number of steps to advance the simulation.
            result: Optional writable C-contiguous output with shape
                ``data.shape``; use a zero-dimensional array for a single environment.

        Note:
            Status codes are 0 for success, 1 for LargeVelocity, 2 for NonFinite,
            3 for NonPositiveDefinite, and 4 for SingularSystem.
            This method skips Python overhead between substeps. A failed instance stops its
            remaining substeps; healthy instances continue. Failure does not roll back state;
            reset failed instances before reuse. A zero-step call writes success without changing
            state. The output is overwritten on every call.
            With result=None, numerical failure raises RuntimeError after healthy instances finish.
            With an output array, numerical failures only write status codes.

        Raises:
            RuntimeError: If data belongs to a different model, or a numerical failure occurs
                without a result array.
            TypeError: If result is not an int32 ndarray.
            ValueError: If n exceeds u32::MAX, or result has invalid shape, layout,
                writability, or borrowing.
