# motrixsim

## Classes

- [`Actuator`](../symbols/motrixsim.Actuator.md) - The base Actuator class provides access to common actuator properties and control.
- [`ActuatorOverrideError`](../symbols/motrixsim.ActuatorOverrideError.md)
- [`ActuatorOverrideInvalidValueError`](../symbols/motrixsim.ActuatorOverrideInvalidValueError.md)
- [`ActuatorOverrideUnsupportedTypeError`](../symbols/motrixsim.ActuatorOverrideUnsupportedTypeError.md)
- [`ActuatorSensor`](../symbols/motrixsim.ActuatorSensor.md)
- [`AdhesionActuator`](../symbols/motrixsim.AdhesionActuator.md) - Adhesion actuator (MJCF ``<adhesion>``). Generates adhesion force on contact surfaces.
- [`BaseSensor`](../symbols/motrixsim.BaseSensor.md)
- [`Body`](../symbols/motrixsim.Body.md) - The Body object represents a rigid body in the scene.
- [`Camera`](../symbols/motrixsim.Camera.md) - The Camera object in the scene.
- [`CameraMgr`](../symbols/motrixsim.CameraMgr.md)
- [`ContactQuery`](../symbols/motrixsim.ContactQuery.md)
- [`ContactSensor`](../symbols/motrixsim.ContactSensor.md)
- [`DisjointIndices`](../symbols/motrixsim.DisjointIndices.md)
- [`FloatingBase`](../symbols/motrixsim.FloatingBase.md) - The FloatingBase object represents a floating base in the scene.
- [`GeneralActuator`](../symbols/motrixsim.GeneralActuator.md) - General actuator (MJCF ``<general>``).
- [`Geom`](../symbols/motrixsim.Geom.md) - The Geom object represents a geometry in the scene.
- [`GeomCapsule`](../symbols/motrixsim.GeomCapsule.md) - Capsule geometry.
- [`GeomCuboid`](../symbols/motrixsim.GeomCuboid.md) - Cuboid (box) geometry.
- [`GeomCylinder`](../symbols/motrixsim.GeomCylinder.md) - Cylinder geometry.
- [`GeomEllipsoid`](../symbols/motrixsim.GeomEllipsoid.md) - Ellipsoid geometry.
- [`GeomHField`](../symbols/motrixsim.GeomHField.md) - Height field geometry.
- [`GeomInfinitePlane`](../symbols/motrixsim.GeomInfinitePlane.md) - Infinite plane geometry.
- [`GeomMesh`](../symbols/motrixsim.GeomMesh.md) - Mesh geometry.
- [`GeomPlane`](../symbols/motrixsim.GeomPlane.md) - Sized plane geometry.
- [`GeomSphere`](../symbols/motrixsim.GeomSphere.md) - Sphere geometry.
- [`HField`](../symbols/motrixsim.HField.md) - The HField object represents a height field terrain in the scene.
- [`Joint`](../symbols/motrixsim.Joint.md) - The Joint object represents a joint in the scene.
- [`JointSensor`](../symbols/motrixsim.JointSensor.md)
- [`Keyframe`](../symbols/motrixsim.Keyframe.md) - The Keyframe object represents a keyframe in the scene.
- [`LidarReturns`](../symbols/motrixsim.LidarReturns.md) - Compiled per-beam output layout of a lidar sensor, in distance, point, time offset, normal
- [`LidarScanStatus`](../symbols/motrixsim.LidarScanStatus.md) - Lightweight LiDAR measurement status for a SceneData selection.
- [`LidarSensor`](../symbols/motrixsim.LidarSensor.md)
- [`Link`](../symbols/motrixsim.Link.md) - The Link object represents a kinematic link in the scene.
- [`Mocap`](../symbols/motrixsim.Mocap.md) - The Mocap object represents a motion capture body in the scene. it can will participate in the
- [`MotorActuator`](../symbols/motrixsim.MotorActuator.md) - Motor actuator (MJCF ``<motor>``). Direct torque/force control with fixed gain = 1.0.
- [`Options`](../symbols/motrixsim.Options.md) - The Options object represents the simulation options.
- [`PositionActuator`](../symbols/motrixsim.PositionActuator.md) - Position actuator (MJCF ``<position>``).
- [`RaycastCameraReturns`](../symbols/motrixsim.RaycastCameraReturns.md) - Compiled per-ray output layout of a raycast camera, in depth, distance, point, normal order.
- [`RaycastCameraSensor`](../symbols/motrixsim.RaycastCameraSensor.md)
- [`ReportFlags`](../symbols/motrixsim.ReportFlags.md) - Toggles for runtime report generation, accessed via `motrixsim.SceneModel.reports`.
- [`SceneData`](../symbols/motrixsim.SceneData.md) - The SceneData object represents the simulation state.
- [`SceneModel`](../symbols/motrixsim.SceneModel.md) - The SceneModel object represents the entire simulation world.
- [`SensorCollection`](../symbols/motrixsim.SensorCollection.md)
- [`Shape`](../symbols/motrixsim.Shape.md) - The source shape type of a high-level geometry.
- [`Site`](../symbols/motrixsim.Site.md) - The Site object represents a reference point or marker in the scene.
- [`SiteSensor`](../symbols/motrixsim.SiteSensor.md)
- [`SiteShape`](../symbols/motrixsim.SiteShape.md) - Site shape type in the simulation.
- [`SubtreeSensor`](../symbols/motrixsim.SubtreeSensor.md)
- [`TerrainScanner`](../symbols/motrixsim.TerrainScanner.md) - A scanner object for batched frame-relative terrain height sampling.
- [`TouchSensor`](../symbols/motrixsim.TouchSensor.md)
- [`VelocityActuator`](../symbols/motrixsim.VelocityActuator.md) - Velocity actuator (MJCF ``<velocity>``).

## Functions

### forward_kinematic

```python
def forward_kinematic(model: SceneModel, data: SceneData) -> None
```

Update kinematics without advancing simulation time.

    Args:
        model: The scene model.
        data: The scene data, optionally batched or indexed.

    Note:
        Equivalent to ``model.forward_kinematic(data)``. Static LiDAR refreshes on each call;
        raycast cameras capture only their first frame after initialization or reset. Changing
        DoF positions alone does not invalidate an existing camera image, so the cached image
        may not match the current pose. This call does not bypass camera ``update_period``.

        Rolling LiDAR is not measured by this function. After reset, physics steps must
        complete a new full scan according to ``hz`` before LiDAR ``ready`` becomes true.
        Cached pre-reset values remain readable but are not valid observations.
        Only the environments in the supplied data view are updated.

    Raises:
        RuntimeError: If the scene data belongs to a different model.

### init_thread_pool

```python
def init_thread_pool(num_threads: Optional[int] = None, core_ids: Optional[Sequence[int]] = None) -> None
```

Initialize Motphys's shared Rayon thread pool with explicit options.

    Must be called before any model load: the shared pool can only be initialized once per
    process, and the first step call lazy-creates it with the default policy (one worker per
    available logical CPU, with core-affinity binding). Calling again raises RuntimeError.

    Note:
        Intended for benchmarking and experiments that need to control worker thread count or
        CPU pinning. Normal usage should leave the default pool alone.

    Args:
        num_threads: Number of worker threads. None or 0 uses the default logical CPU
            count. Automatic logical-CPU pinning is used only when core_ids is also None.
        core_ids: CPU core IDs to pin workers to. Worker i is bound
            to core_ids[i % len(core_ids)]. When num_threads is greater than zero, None does not
            change worker affinity beyond the process's existing affinity or cpuset constraints.

### load_mjcf_str

```python
def load_mjcf_str(mjcf: str) -> SceneModel
```

Load a model from a string containing MJCF data.

    Args:
       mjcf: The MJCF data as a string.

    Returns:
       SceneModel: The loaded scene model.

### load_model

```python
def load_model(path: str | Path) -> SceneModel
```

Load a MJCF, URDF, or USD file and return a SceneModel.

### real_dtype

```python
def real_dtype() -> str
```

Get the numpy dtype name of the scalar type used by this build.

    Returns:
        str: "float32" for the default build, "float64" for an f64 build.

    Note:
        Floating-point arrays exchanged with the simulation follow this dtype.
        Buffers and assertions can be aligned to the wheel width via
        np.dtype(motrixsim.real_dtype()).

### step

```python
def step(model: SceneModel, data: SceneData, result: Optional[numpy.typing.NDArray[numpy.int32]] = None) -> None
```

Advance the simulation by one step.

    Args:
        model: The scene model.
        data: The scene data.
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
