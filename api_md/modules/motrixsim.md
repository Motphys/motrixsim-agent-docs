# motrixsim

## Classes

- [`Actuator`](../symbols/motrixsim.Actuator.md) - The base Actuator class provides access to common actuator properties and control.
- [`AdhesionActuator`](../symbols/motrixsim.AdhesionActuator.md) - Adhesion actuator (MJCF ``<adhesion>``). Generates adhesion force on contact surfaces.
- [`Body`](../symbols/motrixsim.Body.md) - The Body object represents a rigid body in the scene.
- [`Camera`](../symbols/motrixsim.Camera.md) - The Camera object in the scene.
- [`CameraMgr`](../symbols/motrixsim.CameraMgr.md)
- [`ContactQuery`](../symbols/motrixsim.ContactQuery.md)
- [`DisjointIndices`](../symbols/motrixsim.DisjointIndices.md)
- [`FloatingBase`](../symbols/motrixsim.FloatingBase.md) - The FloatingBase object represents a floating base in the scene.
- [`GeneralActuator`](../symbols/motrixsim.GeneralActuator.md) - General actuator (MJCF ``<general>``).
- [`Geom`](../symbols/motrixsim.Geom.md) - The Geom object represents a geometry in the scene.
- [`HField`](../symbols/motrixsim.HField.md) - The HField object represents a height field terrain in the scene.
- [`Joint`](../symbols/motrixsim.Joint.md) - The Joint object represents a joint in the scene.
- [`Keyframe`](../symbols/motrixsim.Keyframe.md) - The Keyframe object represents a keyframe in the scene.
- [`Link`](../symbols/motrixsim.Link.md) - The Link object represents a kinematic link in the scene.
- [`Mocap`](../symbols/motrixsim.Mocap.md) - The Mocap object represents a motion capture body in the scene. it can will participate in the
- [`MotorActuator`](../symbols/motrixsim.MotorActuator.md) - Motor actuator (MJCF ``<motor>``). Direct torque/force control with fixed gain = 1.0.
- [`Options`](../symbols/motrixsim.Options.md) - The Options object represents the simulation options.
- [`PositionActuator`](../symbols/motrixsim.PositionActuator.md) - Position actuator (MJCF ``<position>``).
- [`SceneData`](../symbols/motrixsim.SceneData.md) - The SceneData object represents the simulation state.
- [`SceneModel`](../symbols/motrixsim.SceneModel.md) - The SceneModel object represents the entire simulation world.
- [`Shape`](../symbols/motrixsim.Shape.md) - The shape type of a collider.
- [`Site`](../symbols/motrixsim.Site.md) - The Site object represents a reference point or marker in the scene.
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
def load_model(path: str) -> SceneModel
```

Load a model from the given file path.
    
    Args:
        path: The path to the model file.
        currently mjcf and urdf are supported.
    
    Returns:
        SceneModel: The loaded scene model.

### load_usd

```python
def load_usd(usd_path: str | Path, deduplicate_vertices: bool = True) -> SceneModel
```

Load a USD file and return a SceneModel ready for simulation.

    Args:
        usd_path: Path to the USD file (.usd, .usda, .usdc, .usdz).
        deduplicate_vertices: If True (default), merge vertices with identical attributes.

### step

```python
def step(model: SceneModel, data: SceneData) -> None
```

Advance the simulation by one step.
    
    Args:
        model: The scene model.
        data: The scene data.
