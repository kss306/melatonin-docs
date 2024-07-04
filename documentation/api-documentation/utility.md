# Utility

### Log

Logs a message into the console

```lua
utility.log(string: message)
```

***

### Random int

Returns a random integer between the min and the max

```lua
utility.random_int(int: min, int: max)
```

***

### Random float

Returns a random float between the min and the max

```lua
utility.random_float(float: min, float: max)
```

***

### World to screen

Returns 2D coordinates from a 3D point in space

```lua
utility.world_to_screen(int: x, int: y, int: z)
```

***

### Key state

Returns true if key is pressed

```lua
utility.key_state(int: key_id)
```

***

### Get delta time

Returns time elapsed since last frame, in seconds for the overlay

```lua
utility.get_delta_time()
```

***
