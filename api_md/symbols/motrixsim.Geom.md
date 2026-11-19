# motrixsim.Geom

Module: [`motrixsim`](../modules/motrixsim.md)

The Geom object represents a geometry in the scene.

    This class provides access to the properties and state of a geometry in the scene.
    It allows you to retrieve information about the geom and colliders belong to it.

    Typed subclasses provide shape-specific properties:

    - `GeomSphere` - spherical geometry with ``radius``
    - `GeomCapsule` - capsule geometry with ``radius`` and ``half_height``
    - `GeomCylinder` - cylindrical geometry with ``radius`` and ``half_height``
    - `GeomCuboid` - box geometry with ``half_extents``
    - `GeomEllipsoid` - ellipsoidal geometry with ``half_extents``
    - `GeomPlane` - sized plane geometry
    - `GeomMesh` - mesh geometry with ``mesh_name`` and ``mesh_transform``
    - `GeomHField` - height field geometry with ``hfield``
    - `GeomInfinitePlane` - infinite plane geometry

## Properties

| Name | Type | Description |
|------|------|-------------|
| `body` | `Optional[Body]` | The body this geometry belongs to. None if it is a world geometry. |
| `collision_affinity` | `int` | The collision affinity of the geom. |
| `collision_group` | `int` | The collision group of the geom. |
| `friction` | `numpy.typing.NDArray[numpy.float32]` | Get the friction value from the model. |
| `gap` | `float` | The contact gap of the geom. |
| `hfield` | `Optional[HField]` | The height field associated with this geom. |
| `index` | `int` | The index of the geom in the `motrixsim.SceneModel.geoms`. |
| `link` | `Optional[Link]` | The parent link this geometry is attached to. None if it is a world geometry. |
| `local_pose` | `numpy.typing.NDArray[numpy.float32]` | The local pose of the geom relative to its parent link or world. |
| `margin` | `float` | The contact margin of the geom. |
| `mesh_variant_set` | `Optional[str]` | Name of the mesh variant set referenced by this geometry, if any. |
| `model` | `SceneModel` | The scene model that this geom belongs to. |
| `name` | `Optional[str]` | The name of the geom. Must be unique within the scene. |
| `shape` | `Shape` | The shape type of the geom. |
| `size` | `numpy.typing.NDArray[numpy.float32]` | The size parameters of the geom. |
| `visual_only` | `bool` | Whether this geom is visual-only and does not generate low-level colliders. |

### body

```python
body: Optional[Body]
```

The body this geometry belongs to. None if it is a world geometry.

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

### friction

```python
friction: numpy.typing.NDArray[numpy.float32]
```

Get the friction value from the model.

    Returns:
        NDArray[float]: The model-level friction value. shape = (3,).
            The array is `[slide, spin, roll]`, compiled into the model
            before any per-instance override.

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

The height field associated with this geom.

    Returns:
        Optional[HField]: The HField object if this geom is a height field
            geometry, otherwise ``None``.

    Note:
        This is a convenience accessor on the base `Geom` class so that
        code iterating over ``model.geoms`` can check ``g.hfield is not None``
        without first testing the concrete subclass type.  The same property is
        also available on `GeomHField`.

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

### mesh_variant_set

```python
mesh_variant_set: Optional[str]
```

Name of the mesh variant set referenced by this geometry, if any.

    Returns:
        str | None: The referenced variant set name, or ``None`` when this geometry
            references no set. Candidate names and their ordinals live in
            ``SceneModel.mesh_variant_sets``.

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
        Shape: The source shape type of the geom.

    Note:
        The high-level shape type determines the source geometric representation of the geom.
        Possible values include: Sphere, Cylinder, Capsule, Cuboid, InfinitePlane,
        HField, Mesh, and Plane. Each shape type has different parameters and
        may lower to different low-level runtime collider shapes.

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

### visual_only

```python
visual_only: bool
```

Whether this geom is visual-only and does not generate low-level colliders.

    Returns:
        bool: True if this geom does not participate in collision detection.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `get_active_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.bool_]` | Get the effective active flag for each data instance. |
| `get_angular_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world angular velocity of the geom. |
| `get_friction_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the friction override value from the scene data. |
| `get_linear_velocity` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world linear velocity of the geom. |
| `get_local_aabb` | `(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> Optional[numpy.typing.NDArray[numpy.float32]]` | Get the source geometry AABB in geom-local coordinates. |
| `get_mesh_variant_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.int64]` | Get the effective mesh variant for each data instance. |
| `get_pos_override` | `(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the effective local translation for each data instance. |
| `get_pose` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.float32]` | Get the world pose of the geom. |
| `get_quat_override` | `(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]` | Get the effective local rotation for each data instance. |
| `get_shape_override` | `(self, data: SceneData) -> numpy.typing.NDArray[numpy.int64]` | Get the effective runtime collision shape selection. |
| `get_world_aabb` | `(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> Optional[numpy.typing.NDArray[numpy.float32]]` | Get the source geometry AABB in world coordinates. |
| `set_active_override` | `(self, data: SceneData, active: Any) -> None` | Activate or deactivate this geom for every data instance. |
| `set_friction_override` | `(self, data: SceneData, friction: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Override the friction value of the geom. |
| `set_pose_override` | `(self, data: SceneData, pos: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32], quat: numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]) -> None` | Replace the local pose of this geom for every data instance. |
| `set_shape_override` | `(self, data: SceneData, shape: numpy.typing.NDArray[numpy.int64] \| Sequence[numpy.int64], size: Optional[numpy.typing.NDArray[numpy.float32] \| Sequence[numpy.float32]] = None, variant: Optional[numpy.typing.NDArray[numpy.int64] \| Sequence[numpy.int64]] = None) -> None` | Override the runtime collision geometry selection for every data instance. |

### get_active_override

```python
def get_active_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.bool_]
```

Get the effective active flag for each data instance.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[bool]: Whether the geom exists for each instance, with the same array shape
                as ``data``. An inactive geom produces no collision, ray hit, or rendering; its
                shape/size/pose overrides are kept and restored on re-enable.

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

### get_local_aabb

```python
def get_local_aabb(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> Optional[numpy.typing.NDArray[numpy.float32]]
```

Get the source geometry AABB in geom-local coordinates.

        Args:
            data: The scene data to query.

            out: Pre-allocated output array of shape
                ``(*data.shape, 2, 3)``. When provided, finite AABB results are written into this
                array and returned directly.

        Returns:
            Optional[NDArray[float]]: ``None`` when the source geom has no finite AABB, currently
                only for ``InfinitePlane``, or when the geom is inactive for the instance. Otherwise
        returns an array with shape         ``(*data.shape, 2, 3)`` where ``[..., 0, :]`` is min
        and ``[..., 1, :]`` is max.

        Note:
            Runtime size overrides in ``data``, when present, affect supported primitive bounds.

### get_mesh_variant_override

```python
def get_mesh_variant_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.int64]
```

Get the effective mesh variant for each data instance.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[int]: Set-local variant ordinal for each data instance, with the same array
                shape as ``data``. The ordinal indexes the candidate name list of the referenced
                set in ``SceneModel.mesh_variant_sets``. Primitive selections use the ``-1``
                sentinel.

### get_pos_override

```python
def get_pos_override(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective local translation for each data instance.

        Args:
            data: The scene data to query.
            out: Pre-allocated output array of shape
                ``(*data.shape, 3)``. When provided, results are written into this array and
                returned directly.

        Returns:
            NDArray[float]: The effective local translation, shape ``(*data.shape, 3)``.
                Falls back to the geom's authored position for instances without a pose
                override.

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

### get_quat_override

```python
def get_quat_override(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> numpy.typing.NDArray[numpy.float32]
```

Get the effective local rotation for each data instance.

        Args:
            data: The scene data to query.
            out: Pre-allocated output array of shape
                ``(*data.shape, 4)``. When provided, results are written into this array and
                returned directly.

        Returns:
            NDArray[float]: The effective local rotation quaternion in ``[i, j, k, w]`` order,
                shape ``(*data.shape, 4)``. Falls back to the geom's authored orientation for
                instances without a pose override.

### get_shape_override

```python
def get_shape_override(self, data: SceneData) -> numpy.typing.NDArray[numpy.int64]
```

Get the effective runtime collision shape selection.

        Args:
            data: The scene data to query.

        Returns:
            NDArray[int]: Effective shape for each data instance, with the same array shape as
                ``data``. Values are ``Shape`` ordinals and compare equal to the corresponding
                ``Shape`` members, e.g. ``geom.get_shape_override(data) == Shape.Mesh`` selects
                the mesh instances, and ``Shape.types()[value]`` decodes a member by ordinal.
                Mesh selections are reported as ``Shape.Mesh``.

### get_world_aabb

```python
def get_world_aabb(self, data: SceneData, out: Optional[numpy.typing.NDArray[numpy.float32]] = None) -> Optional[numpy.typing.NDArray[numpy.float32]]
```

Get the source geometry AABB in world coordinates.

        Args:
            data: The scene data to query.

            out: Pre-allocated output array of shape
                ``(*data.shape, 2, 3)``. When provided, finite AABB results are written into this
                array and returned directly.

        Returns:
            Optional[NDArray[float]]: ``None`` under the same conditions as
                `get_local_aabb`. Otherwise returns an array with shape
                ``(*data.shape, 2, 3)`` where ``[..., 0, :]`` is min and ``[..., 1, :]`` is max.

### set_active_override

```python
def set_active_override(self, data: SceneData, active: Any) -> None
```

Activate or deactivate this geom for every data instance.

        An inactive geom produces no collision, ray hit, or rendering — the per-instance
        "absent slot" state (e.g. a head part missing from some instances' asset variants).
        Unlike the shape selection, the active flag applies to every geom, including
        non-switchable ones (Plane, HField, mesh without a variant set). The shape, size,
        and pose overrides are kept and take effect again once the geom is re-enabled. The flag
        does not couple to mass properties; combine it with the link inertia overrides when a
        removed part should also change dynamics.

        Args:
            data: The scene data to modify.
            active: Per-instance active flag.
                - Scalar ``bool``: Single value applied to all instances.
                - Shape ``(*data.shape,)``: Per-instance values; the batch dimension must match
                  ``data`` exactly, single-value broadcasting is not accepted.

        Note:
            Raises ValueError when an array batch dimension does not match ``data``.

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

### set_pose_override

```python
def set_pose_override(self, data: SceneData, pos: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32], quat: numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]) -> None
```

Replace the local pose of this geom for every data instance.

        The pose is a replacement of the geom's authored local ``pos``/``quat`` relative to its
        parent link, applied to collision, raycast, and rendering. It is independent of the
        shape/size selections.

        Args:
            data: The scene data to modify.
            pos: Translation ``[x, y, z]``.
                - Shape ``(3,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 3)``: Per-batch values.
            quat: Rotation quaternion ``[i, j, k, w]``; normalized internally.
                - Shape ``(4,)``: Single value applied to all batches.
                - Shape ``(*data.shape, 4)``: Per-batch values.

        Note:
            Instances with a non-finite translation or a non-finite / zero-norm quaternion are
            silently ignored and keep their previous pose. Batch dimensions must match ``data``
            exactly (no single-value broadcasting of a mismatched length).

### set_shape_override

```python
def set_shape_override(self, data: SceneData, shape: numpy.typing.NDArray[numpy.int64] | Sequence[numpy.int64], size: Optional[numpy.typing.NDArray[numpy.float32] | Sequence[numpy.float32]] = None, variant: Optional[numpy.typing.NDArray[numpy.int64] | Sequence[numpy.int64]] = None) -> None
```

Override the runtime collision geometry selection for every data instance.

        This is the single setter for the geom-level selection: a primitive shape replaces any
        current selection, and ``Shape.Mesh`` selects a mesh variant of the referenced set
        (reported by ``SceneModel.mesh_variant_sets[geom.mesh_variant_set]``).

        Args:
            data: The scene data to modify.
            shape: One of Sphere, Cylinder, Capsule, Cuboid, Ellipsoid, or Mesh,
                encoded as integer ``Shape`` ordinals. Any integer dtype is accepted and
                converted to int64 by NumPy.
                - Shape ``(*data.shape,)``: One selection per data instance. The batch dimension
                  must match ``data`` exactly; single-value broadcasting is not accepted.
            size: Optional primitive size for the selected primitives.
                - Shape ``(*data.shape, 3)``: One row of 3 components per data instance. The batch
                  dimension must match ``data`` exactly; single-value broadcasting is not accepted.
                Each primitive reads only the components it requires; unused components are
                stored but ignored. When omitted, primitive selections are validated against and
                keep each instance's current effective size. Instances selecting ``Shape.Mesh``
                ignore ``size``.
            variant: Set-local mesh variant ordinal; ``-1`` ignores the
                instance. Required whenever ``shape`` contains ``Shape.Mesh`` and ignored
                otherwise. Any integer dtype is accepted and converted to int64 by NumPy.
                - Shape ``(*data.shape,)``: One variant ordinal per data instance. The batch
                  dimension must match ``data`` exactly; single-value broadcasting is not accepted.

        Note:
            Raises ValueError when an array batch dimension does not match ``data``, a shape
            is not a supported selection, a ``Shape.Mesh`` selection has no ``variant``
            argument or an out-of-range ordinal, or ``variant`` sets an ordinal on a non-mesh
            row. Array-shape errors are rejected before any instance is
            modified; the remaining conditions are validated inside the parallel apply pass,
            so instances applied before the error keep their new selection. An instance
            whose current or provided size is invalid for the selected primitive keeps its
            previous selection.
