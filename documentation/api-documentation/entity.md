# Entity

### Get players

Returns an array of player entity indices

```lua
entity.get_players()
```

***

### Get weapons

Returns an array of weapons on the ground entity indices

```lua
entity.get_weapons()
```

***

### Get projectiles

Returns an array of thrown grenade entity indices

```lua
entity.get_projectiles()
```

***

### Get origin

Returns x, y, z world coordinates of the entities origin

```lua
entity.get_origin(int: entity_index)
```

***

### Get mins

Returns x, y, z minimum coordinates of the entities bounds

```lua
entity.get_mins(int: entity_index)
```

***

### Get maxs

Returns x, y, z maximum coordinates of the entities bounds

```lua
entity.get_mins(int: entity_index)
```

***

### Get player name

Returns the player name

```lua
entity.get_player_name(int: entity_index)
```

***

### Get bounding box

Returns x1, y1, x2, y2 from all corners of the boundig box

```lua
entity.get_bounding_box(int: entity_index)
```

***

### Is alive

Returns true if entity is alive

```lua
entity.is_alive(int: entity_index)
```

***

### Is enemy

Returns true if entity is hostile

```lua
entity.is_enemy(int: entity_index)
```

***

### Is immune

Returns true if player is immune to damage

```lua
entity.is_immune(int: entity_index)
```

***

### Bone position

RReturns x, y, z world coordinates of the entities bone

```lua
entity.bone_position(int: entity_index, int: bone_id)
```

[#bone-id-list](extra-infos.md#bone-id-list "mention")

***

### Get address

Returns a players address in memory

```lua
entity.get_address(int: entity_index)
```

***

### Get player pawn

Returns a players pawn address in memory

```lua
entity.get_player_pawn(int: entity_index)
```

***

### Get player controller

Returns a players controller address in memory

```lua
entity.get_player_controller(int: entity_index)
```

***

### Get player weapon

Returns the definition index of the players weapon

```lua
entity.get_player_controller(int: entity_index)
```

***

### Get velocity

Returns players velocity

```lua
entity.get_velocity(int: entity_index)
```

***

### Get health

Returns players health

```lua
entity.get_health(int: entity_index)
```

{% hint style="danger" %}
This function seems to be broken right now. A workaround code can be found below
{% endhint %}

<pre class="language-lua"><code class="lang-lua">--Get health from offset 0x324
local entity_pawn = entity.get_player_pawn(int: entity_index)
<strong>local entity_health = memory.read_integer(entity_pawn + 0x324)
</strong></code></pre>
