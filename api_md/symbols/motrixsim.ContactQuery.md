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
| `is_colliding` | `(self, geom_pairs: Any) -> numpy.typing.NDArray[numpy.bool_]` | Given a list of geometry pairs, check if they are colliding. |

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
