---
description: Calculate an entities velocity and return it as an integer
---

# Get velocity

```lua
local function calcVelo(ent)
    local velocity = math.floor(entity.get_velocity(ent)+0.1)
    return velocity
end

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    local velocity = calcVelo(lp)
    utility.log(velocity)
end)
```
