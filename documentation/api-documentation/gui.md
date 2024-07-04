# Gui

### New checkbox

Returns a reference for gui.get and gui.set

```lua
gui.new_checkbox(string: name)
```

***

### New slider

Returns a reference for gui.get and gui.set

```lua
gui.new_slider(string: name, int: min, int: max)
```

***

### New hotkey

Returns a reference for gui.get and gui.set

```lua
gui.new_hotkey(string: name, int: key)
```

***

### Get

Returns the state of a gui elemet e.g., checkbox bool, slider current int, etc.

```lua
gui.get(int: gui_id)
```

***

### Set

Set the value of a gui element

```lua
gui.set(int: gui_id, var: value)
```
