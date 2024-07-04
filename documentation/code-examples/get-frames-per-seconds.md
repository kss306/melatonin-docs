---
description: Calculate the framerate and return it as an integer
---

# Get frames per seconds

```lua
local global_frame, global_seconds = globals.framecount(), globals.realtime()

local function calcFPS()
    local new_sec = globals.realtime()
    if(new_sec < global_seconds + 1) then return end
    global_seconds = new_sec

    local fps = math.floor(globals.framecount() - global_frame)
    global_frame = globals.framecount()
    return fps
end

cheat.set_callback("paint", function()
    local fps = clacFPS()
    utility.log(fps)
end)
```
