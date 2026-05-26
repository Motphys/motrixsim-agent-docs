# motrixsim.render.RenderSettings

Module: [`motrixsim.render`](../modules/motrixsim.render.md)

The global render settings for render app.

## Properties

| Name | Type | Description |
|------|------|-------------|
| `enable_oit` | `bool` | Whether to enable OIT(Order Independent Transparency) effect. |
| `enable_shadow` | `bool` | Whether to render shadows for lights. |
| `enable_ssao` | `bool` | Whether to enable SSAO(Screen Space Ambient Occlusion) effect. |
| `enable_ssgi` | `bool` | Whether to enable SSGI(Screen Space Global Illumination) effect. |
| `share_lights_between_envs` | `bool` | Whether to share lights between multiple simulation worlds, for performance optimization. |
| `simplify_render_mesh` | `bool` | Wether to simplify render mesh when loading the model. |

### enable_oit

```python
enable_oit: bool
```

Whether to enable OIT(Order Independent Transparency) effect.

### enable_shadow

```python
enable_shadow: bool
```

Whether to render shadows for lights.

### enable_ssao

```python
enable_ssao: bool
```

Whether to enable SSAO(Screen Space Ambient Occlusion) effect.

### enable_ssgi

```python
enable_ssgi: bool
```

Whether to enable SSGI(Screen Space Global Illumination) effect.

### share_lights_between_envs

```python
share_lights_between_envs: bool
```

Whether to share lights between multiple simulation worlds, for performance optimization.
    If false, each simulation world will have its own set of lights, which may cost more
    rendering resources, or out of memory crash depends on the number of simulation worlds and
    scene complexity.

### simplify_render_mesh

```python
simplify_render_mesh: bool
```

Wether to simplify render mesh when loading the model.

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `__new__` | `(cls, simplify_render_mesh: bool, enable_shadow: bool, enable_ssao: bool, enable_oit: bool, share_lights_between_envs: bool, enable_ssgi: bool = False) -> RenderSettings` |  |
| `performance` | `() -> RenderSettings` | Get a render settings with high performance. |
| `quality` | `() -> RenderSettings` | Get a render settings with high quality. |

### __new__

```python
def __new__(cls, simplify_render_mesh: bool, enable_shadow: bool, enable_ssao: bool, enable_oit: bool, share_lights_between_envs: bool, enable_ssgi: bool = False) -> RenderSettings
```

### performance

```python
def performance() -> RenderSettings
```

Get a render settings with high performance.

### quality

```python
def quality() -> RenderSettings
```

Get a render settings with high quality.
