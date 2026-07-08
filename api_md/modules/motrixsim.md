# motrixsim

## Classes

- [`Actuator`](../symbols/motrixsim.Actuator.md) - The base Actuator class provides access to common actuator properties and control.
- [`ActuatorOverrideDampingTypeError`](../symbols/motrixsim.ActuatorOverrideDampingTypeError.md)
- [`ActuatorOverrideError`](../symbols/motrixsim.ActuatorOverrideError.md)
- [`ActuatorOverrideInvalidValueError`](../symbols/motrixsim.ActuatorOverrideInvalidValueError.md)
- [`ActuatorOverrideUnsupportedTypeError`](../symbols/motrixsim.ActuatorOverrideUnsupportedTypeError.md)
- [`AdhesionActuator`](../symbols/motrixsim.AdhesionActuator.md) - Adhesion actuator (MJCF ``<adhesion>``). Generates adhesion force on contact surfaces.
- [`Body`](../symbols/motrixsim.Body.md) - The Body object represents a rigid body in the scene.
- [`Camera`](../symbols/motrixsim.Camera.md) - The Camera object in the scene.
- [`CameraMgr`](../symbols/motrixsim.CameraMgr.md)
- [`ContactQuery`](../symbols/motrixsim.ContactQuery.md)
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
- [`Keyframe`](../symbols/motrixsim.Keyframe.md) - The Keyframe object represents a keyframe in the scene.
- [`Link`](../symbols/motrixsim.Link.md) - The Link object represents a kinematic link in the scene.
- [`Mocap`](../symbols/motrixsim.Mocap.md) - The Mocap object represents a motion capture body in the scene. it can will participate in the
- [`MotorActuator`](../symbols/motrixsim.MotorActuator.md) - Motor actuator (MJCF ``<motor>``). Direct torque/force control with fixed gain = 1.0.
- [`Options`](../symbols/motrixsim.Options.md) - The Options object represents the simulation options.
- [`PositionActuator`](../symbols/motrixsim.PositionActuator.md) - Position actuator (MJCF ``<position>``).
- [`ReportFlags`](../symbols/motrixsim.ReportFlags.md) - Toggles for runtime report generation, accessed via `motrixsim.SceneModel.reports`.
- [`SceneData`](../symbols/motrixsim.SceneData.md) - The SceneData object represents the simulation state.
- [`SceneModel`](../symbols/motrixsim.SceneModel.md) - The SceneModel object represents the entire simulation world.
- [`Shape`](../symbols/motrixsim.Shape.md) - The source shape type of a high-level geometry.
- [`Site`](../symbols/motrixsim.Site.md) - The Site object represents a reference point or marker in the scene.
- [`SiteShape`](../symbols/motrixsim.SiteShape.md) - Site shape type in the simulation.
- [`TerrainScanner`](../symbols/motrixsim.TerrainScanner.md) - A scanner object for batched frame-relative terrain height sampling.
- [`VelocityActuator`](../symbols/motrixsim.VelocityActuator.md) - Velocity actuator (MJCF ``<velocity>``).

## Functions

### forward_kinematic

```python
def forward_kinematic(model: SceneModel, data: SceneData) -> None
```

Run forward kinematic only.

    Args:
        model: The scene model.
        data: The scene data.

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

### step

```python
def step(model: SceneModel, data: SceneData) -> None
```

Advance the simulation by one step.

    Args:
        model: The scene model.
        data: The scene data.
