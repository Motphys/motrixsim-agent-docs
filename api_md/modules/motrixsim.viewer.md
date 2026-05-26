# motrixsim.viewer

## Functions

### launch

```python
def launch(model: Optional[SceneModel] = None, data: Optional[Any] = None, callback: Optional[Any] = None) -> None
```

Launch a managed viewer with optional model and data.
    
    This function provides a simplified interface similar to MuJoCo's managed viewer.
    It blocks until the viewer window is closed, automatically handling the physics
    simulation loop and rendering.
    
    Args:
        model: The scene model to simulate and visualize.
                                      If not provided, loads a default sample model.
        data: The scene data containing the initial state.
                                    If not provided, creates default data from the model.
        callback: A callback function called at each physics step.
