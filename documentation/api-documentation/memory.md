# Memory

### Get module

Returns a address of the module and the size of the module

```lua
memory.get_module(string: module_name)
```

***

### Find signature

Returns a address in memory

```lua
memory.find_signature(int: start, int size, dynamic: signature, pattern: mask)
```

***

### Read byte

Returns 0 or 1

```lua
memory.read_byte(address)
```

***

### Read float

Returns a float

```lua
memory.read_float(address)
```

***

### Read integer

Returns a integer

```lua
memory.read_integer(address)
```

***

### Read string

Returns a string

```lua
memory.read_string(address, int: size)
```

***

### Read pointer

Returns a address in memory

***

```lua
memory.read_pointer(address)
```

***

### Read vector

Returns x, y, z

```lua
memory.read_vector(address)
```

***

### Get pawn from handle

Returns entity address

```lua
memory.get_pawn_from_handle(address)
```
