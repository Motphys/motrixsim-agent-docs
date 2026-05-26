# motrixsim.Geom

Module: [`motrixsim`](../modules/motrixsim.md)

The Geom object represents a geometry in the scene.
    
    This class provides access to the properties and state of a geometry in the scene.
    It allows you to retrieve information about the geom and colliders belong to it.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `collision_affinity` | `int` | The collision affinity of the geom. |
| `collision_group` | `int` | The collision group of the geom. |
| `gap` | `float` | The contact gap of the geom. |
| `hfield` | `Optional[HField]` | The height field associated with this geom, if the shape type is HField. |
| `index` | `int` | The index of the geom in the `motrixsim.SceneModel.geoms`. |
| `link` | `Optional[Link]` | The parent link this geometry is attached to. None if it is a world geometry. |
| `local_pose` | `numpy.typing.NDArray[numpy.float32]` | The local pose of the geom relative to its parent link or world. |
| `margin` | `float` | The contact margin of the geom. |
| `model` | `SceneModel` | The scene model that this geom belongs to. |
| `name` | `Optional[str]` | The name of the geom. Must be unique within the scene. |
| `shape` | `Shape` | The shape type of the geom. |
| `size` | `numpy.typing.NDArray[numpy.float32]` | The size parameters of the geom. |

### collision_affinity

```python
collision_affinity: int
```

The collision affinity of the geom.
    
    Returns:
        int: The collision affinity mask.
    
    Note:
        The collision affinity (also called collide_with) is a bitmask that specifies which
        collision groups this geom can collide with. Two geoms will collide if
        `(geom1.collision_group & geom2.collision_affinity) != 0` or
        `(geom1.collision_affinity & geom2.collision_group) != 0`.

### collision_group

```python
collision_group: int
```

The collision group of the geom.
    
    Returns:
        int: The collision group identifier.
    
    Note:
        The collision group is used to filter which geometries can collide with each other.
        Two geoms will collide if `(geom1.collision_group & geom2.collision_affinity) != 0`
        or `(geom1.collision_affinity & geom2.collision_group) != 0`.

### gap

```python
gap: float
```

The contact gap of the geom.
    
    Returns:
        float: The distance band that determines which contacts generate solver constraints.
    
    Note:
        The gap controls the distance threshold for generating solver constraints.
        Contacts within this distance will generate constraints in the physics solver.
        This can be tuned to balance stability and performance.

### hfield

```python
hfield: Optional[HField]
```

The height field associated with this geom, if the shape type is HField.
    
    Returns:
        Optional[HField]: The HField object if this geom's shape is HField and has an associated
            height field, otherwise ``None``.
    
    Note:
        This property only returns a valid HField object when:
    
            1. The geom's shape type is ``Shape.HField``
            2. The geom has an associated height field name
    
        For all other shape types, this returns ``None``. Height fields are used to represent
        terrain and elevation data for ground interactions and surface-based physics.

### index

```python
index: int
```

The index of the geom in the `motrixsim.SceneModel.geoms`.

### link

```python
link: Optional[Link]
```

The parent link this geometry is attached to. None if it is a world geometry.

### local_pose

```python
local_pose: numpy.typing.NDArray[numpy.float32]
```

The local pose of the geom relative to its parent link or world.
    
    Returns:
        NDArray[float]: The local pose as a numpy array of shape `(7,)`
            with `[x, y, z, i, j, k, w]` format where the first 3 elements are
            translation and the last 4 are quaternion rotation.
    
    Note:
        The local pose represents the position and orientation of the geom in its parent frame.
        If the geom is attached to a link, this is relative to that link's frame.
        If the geom is a world geom (no parent link), this is in world coordinates.

### margin

```python
margin: float
```

The contact margin of the geom.
    
    Returns:
        float: The distance threshold for detecting contacts.
    
    Note:
        The margin is used to control when contact constraints are generated.
        A larger margin will detect contacts earlier, potentially improving stability
        but may also increase computational cost.

### model

```python
model: SceneModel
```

The scene model that this geom belongs to.

### name

```python
name: Optional[str]
```

The name of the geom. Must be unique within the scene.
    
    Returns:
        Optional[str]: The name of the geom, or "None" if not set.

### shape

```python
shape: Shape
```

The shape type of the geom.
    
    Returns:
        Shape: The shape type of the geom.
    
    Note:
        The shape type determines the geometric representation of the geom.
        Possible values include: Sphere, Cylinder, Capsule, Cuboid, InfinitePlane,
        HField, Mesh, and Plane. Each shape type has different parameters and
        uses in simulation and collision detection.

### size

```python
size: numpy.typing.NDArray[numpy.float32]
```

The size parameters of the geom.
    
    Returns:
        NDArray[float]: The size parameters as a numpy array of shape `(3,)`
            with `[s0, s1, s2]`.
    
    Note:
        The size represents half-size parameters for different shape types:
    
            - **Sphere**: `[radius, 0.0, 0.0]` - spherical radius
            - **Capsule**: `[radius, half_height, 0.0]` - radius and half-height
            - **Cylinder**: `[radius, half_height, 0.0]` - radius and half-height
            - **Cuboid**: `[half_x, half_y, half_z]` - half-extents in each axis
            - **Plane**: `[half_x, half_y, 0.0]` - half-extents in x and y directions
            - **Mesh/HField/InfinitePlane**: `[0.0, 0.0, 0.0]` - size is ignored for these types
    
        When a primitive shape references a mesh file, the size is automatically
        computed from the mesh geometry and the geom size parameters are ignored.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_angular_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world angular velocity of the geom. |
| `get_friction_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the friction override value from the scene data. |
| `get_linear_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world linear velocity of the geom. |
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world pose of the geom. |
| `set_friction_override` | `(self, data: SceneData, friction: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the friction value of the geom. |

### get_angular_velocity

```python
def get_angular_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world angular velocity of the geom.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 3)``. The last axis is the angular velocity with
                `[wx, wy, wz]` format.

### get_friction_override

```python
def get_friction_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the friction override value from the scene data.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: The friction override value. shape = `(*data.shape, 3)`.
                The last axis is `[slide, spin, roll]`.

### get_linear_velocity

```python
def get_linear_velocity(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world linear velocity of the geom.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]:  Shape: ``(*data.shape, 3)``. The last axis is the linear velocity with
                `[vx, vy, vz]` format.

### get_pose

```python
def get_pose(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]
```

Get the world pose of the geom.
        
        Args:
            data: The scene data to query.
        
        Returns:
            NDArray[float]: Shape: ``(*data.shape, 7)``. Each pose is represented as a 7 elements
                with `[x, y, z, i, j, k, w]` format.

### set_friction_override

```python
def set_friction_override(self, data: SceneData, friction: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Override the friction value of the geom.
        
        Args:
            data: The scene data to modify.
            friction: The new friction values `[slide, spin, roll]`.
                - Shape (3,): Single value applied to all batches
                - Shape (*data.shape, 3): Per-batch values
        
        Note:
            If any friction component is negative, NaN, or infinite, the override will be ignored.
