# motrixsim.ui

## Classes

- [`ButtonState`](../symbols/motrixsim.ui.ButtonState.md)
- [`CameraRef`](../symbols/motrixsim.ui.CameraRef.md) - A blueprint-local Camera source resolved by the RenderApp that owns the blueprint.
- [`CheckboxGroupState`](../symbols/motrixsim.ui.CheckboxGroupState.md)
- [`CheckboxState`](../symbols/motrixsim.ui.CheckboxState.md)
- [`Frame`](../symbols/motrixsim.ui.Frame.md) - A stable location whose custom UI child fragment can be rebuilt at runtime.
- [`Image`](../symbols/motrixsim.ui.Image.md) - A mutable Image presentation embedded in a declaration or used as a standalone Viewer leaf.
- [`RadioGroupState`](../symbols/motrixsim.ui.RadioGroupState.md)
- [`SelectState`](../symbols/motrixsim.ui.SelectState.md)
- [`TextInputState`](../symbols/motrixsim.ui.TextInputState.md)
- [`ToggleGroupState`](../symbols/motrixsim.ui.ToggleGroupState.md)
- [`View`](../symbols/motrixsim.ui.View.md) - A View declaration usable as a Viewer blueprint leaf.
- [`ViewerBlueprint`](../symbols/motrixsim.ui.ViewerBlueprint.md) - A layout composed from Views and other layout containers.
- [`_Container`](../symbols/motrixsim.ui._Container.md) - Context manager returned by `Column()`, `Row()`, and `Section()`.

## Functions

### Button

```python
def Button(label: str, *, on_click: Optional[Any] = None) -> ButtonState
```

Add a button to the active declaration container.

### Checkbox

```python
def Checkbox(label: str, *, value: bool = False, on_change: Optional[Any] = None) -> CheckboxState
```

Add an instance-local checkbox to the active declaration container.

### CheckboxGroup

```python
def CheckboxGroup(label: str, options: Sequence[str], *, value: Optional[Sequence[str]] = None, columns: Optional[int] = None, on_change: Optional[Any] = None) -> CheckboxGroupState
```

Add an independently selectable checkbox group to the active declaration container.

### Column

```python
def Column() -> _Container
```

Start a vertical UI container.

### Contacts

```python
def Contacts(*, title: Optional[str] = None) -> View
```

Create the Contacts View.
    Only supported by ``viewer.launch``.

### Favorites

```python
def Favorites(*, title: Optional[str] = None) -> View
```

Create the Favorites View.
    Only supported by ``viewer.launch``.

### Files

```python
def Files(*, title: Optional[str] = None) -> View
```

Create the Files View.
    Only supported by ``viewer.launch``.

### Horizontal

```python
def Horizontal(children: Any, *, shares: Optional[Sequence[float]] = None) -> ViewerBlueprint
```

Create a horizontal split. Direct View children are automatically tab-wrapped.

    Note:
        ``shares`` contains one positive finite relative weight per child, in child order.
        Weights need not sum to one. Omit it or pass ``None`` to divide the available space equally.
        A wrong length or an invalid weight raises ``ValueError``.

### Inspector

```python
def Inspector(*, title: Optional[str] = None) -> View
```

Create the Inspector View.
    Only supported by ``viewer.launch``.

### Log

```python
def Log(*, title: Optional[str] = None) -> View
```

Create the Log View.

### Options

```python
def Options(*, title: Optional[str] = None) -> View
```

Create the Options View.

### Properties

```python
def Properties(*, title: Optional[str] = None) -> View
```

Create the Properties View.
    Only supported by ``viewer.launch``.

### RadioGroup

```python
def RadioGroup(label: str, options: Sequence[str], *, value: Optional[str] = None, direction: str = 'vertical', on_change: Optional[Any] = None) -> RadioGroupState
```

Add a strict single-selection radio group to the active declaration container.

### Row

```python
def Row() -> _Container
```

Start a horizontal UI container.

### SceneTree

```python
def SceneTree(*, title: Optional[str] = None) -> View
```

Create the SceneTree View.
    Only supported by ``viewer.launch``.

### ScrollArea

```python
def ScrollArea(*, max_height: float) -> _Container
```

Start a vertically scrollable UI region with a bounded height.

### Section

```python
def Section(title: str) -> _Container
```

Start a visually separated functional section.

### Select

```python
def Select(label: str, options: Sequence[str], *, value: Optional[str] = None, on_change: Optional[Any] = None) -> SelectState
```

Add an instance-local select to the active declaration container.

### Tabs

```python
def Tabs(children: Any) -> ViewerBlueprint
```

Create an explicit tab group for multiple Views.

### Text

```python
def Text(value: str) -> None
```

Add immutable text to the active declaration container.

### TextInput

```python
def TextInput(label: str, *, value: str = '', on_change: Optional[Any] = None, on_submit: Optional[Any] = None) -> TextInputState
```

Add an instance-local single-line text input to the active declaration container.

    `on_submit`, when provided, receives the current value after the focused input handles Enter.

### ToggleGroup

```python
def ToggleGroup(label: str, options: Sequence[str], *, value: Optional[Sequence[str]] = None, columns: Optional[int] = None, on_change: Optional[Any] = None) -> ToggleGroupState
```

Add an independently selectable button group to the active declaration container.

### Vertical

```python
def Vertical(children: Any, *, shares: Optional[Sequence[float]] = None) -> ViewerBlueprint
```

Create a vertical split. Direct View children are automatically tab-wrapped.

    Note:
        ``shares`` contains one positive finite relative weight per child, in child order.
        Weights need not sum to one. Omit it or pass ``None`` to divide the available space equally.
        A wrong length or an invalid weight raises ``ValueError``.

### Viewport

```python
def Viewport(*, camera: Optional[Any] = None, title: Optional[str] = None, toolbar: bool = True) -> View
```

Create a Viewport, optionally bound to a blueprint-local Camera reference.

    Note:
        `toolbar` only sets the initial Toolbar visibility. Use the owning Tabs menu for runtime
        changes.
