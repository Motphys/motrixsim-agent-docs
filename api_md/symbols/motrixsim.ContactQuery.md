# motrixsim.ContactQuery

Module: [`motrixsim`](../modules/motrixsim.md)

## Properties

| Name | Type | Description |
|------|------|-------------|
| `num_contacts` | `numpy.typing.NDArray[numpy.uint32]` | The number of contacts in the world. |

### num_contacts

```python
num_contacts: numpy.typing.NDArray[numpy.uint32]
```

The number of contacts in the world.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `contacting_geoms` | `(self, geom: Any) -> numpy.typing.NDArray[numpy.uint32]` | Get the geoms currently contacting a geom. |
| `is_colliding` | `(self, geom_pairs: Any) -> numpy.typing.NDArray[numpy.bool_]` | Given a list of geometry pairs, check if they are colliding. |

### contacting_geoms

```python
def contacting_geoms(self, geom: Any) -> numpy.typing.NDArray[numpy.uint32]
```

Get the geoms currently contacting a geom.

        Args:
           geom: Geom object, index or name.

        Returns:
            NDArray[uint32]: Unique high-level geom indices contacting ``geom`` in the current
            step, sorted in ascending order.

### is_colliding

```python
def is_colliding(self, geom_pairs: Any) -> numpy.typing.NDArray[numpy.bool_]
```

Given a list of geometry pairs, check if they are colliding.

        Args:
           geom_pairs: Pairs of geometry
                indices to check for collision. Shape = (N, 2) where N is the number of pairs.
            
        Returns:
            NDArray[bool]: Array of booleans indicating whether each pair is colliding.
