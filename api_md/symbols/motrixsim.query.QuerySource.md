# motrixsim.query.QuerySource

Module: [`motrixsim.query`](../modules/motrixsim.query.md)

A fixed-width physics data source used to compile a query plan.

    This is the common base of all concrete query sources: `DofPosition`, `DofVelocity`,
    `BodyDofPosition`, `BodyDofVelocity`, `ActuatorControls`, `LinkPosition`, `LinkRotation`,
    `LinkLinearVelocity`, `LinkAngularVelocity`, `SensorValues`, `LinkNetContactForces`,
    `GeomPosition`, `GeomRotation`, `GeomLinearVelocity`, and `GeomAngularVelocity`. Construct
    the concrete sources directly; this base only types the values accepted by
    `SceneModel.compile_query`.

    Selectable sources take one `selection` argument that accepts entity names and indices
    alike: `None` selects all entities in model order, a list of names selects by name, and a
    list of indices or a one-dimensional NumPy integer ndarray selects by index. Lists preserve
    their order, may contain duplicates, and must not mix names and indices; names are resolved
    to model indices at compile time. `BodyDofPosition` and `BodyDofVelocity` have no "all"
    selection and require one.
