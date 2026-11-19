# motrixsim.write.WriteSource

Module: [`motrixsim.write`](../modules/motrixsim.write.md)

A fixed-width physics data target used to compile a write plan.

    This is the common base of all concrete write sources: `ActuatorCtrls`, `BodyPosition`,
    `BodyRotation`, `BodyLinearVelocity`, `AddBodyLinearVelocity`, `BodyAngularVelocity`,
    `BodyJointPosition`,
    `BodyJointVelocity`, `JointQuaternion`, `JointAngularVelocity`, `ActuatorKpOverride`,
    `ActuatorDampingOverride`, `LinkMassOverride`,
    `LinkCenterOfMassOverride`, `GeomFrictionOverride`, `GeomSizeOverride`, `GeomPoseOverride`,
    `GeomActiveOverride`, and `GeomShapeOverride`. Construct the concrete sources
    directly; this base only types the values accepted by `SceneModel.compile_write`.

    Selectable sources take one `selection` argument that accepts entity names and indices
    alike: `None` selects all eligible entities (see each source), a list of names selects by
    name, and a list of indices or a one-dimensional NumPy integer ndarray selects by index.
    Unlike query sources, duplicates are rejected at compile time: a duplicated target would
    write the same underlying channel twice.
