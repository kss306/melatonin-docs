# Useful code snippets

### Get screen width

```lua
local function getScreenXY()
    local width, height = cheat.get_window_size()
    local x, y = width / 2, height / 2
    return x,y
end
```

***

### Melatonin colors

```lua
local melatonin_colors = {
    r = 159,
    g = 152,
    b = 222
}
```

***

### Get enemies

```lua
for i, player in ipairs(entity.get_players()) do
    if(entity.is_enemy(player)) then
    
    end
end
```

***

### Get hit enemy

```lua
local last_total_hits = -1
local enemy_ent = {}

local function on_paint()
    local curTime = globals.curtime()
    local total_hits = engine.get_total_hits()
    local temp_ent = {}
    for i, player in ipairs(entity.get_players()) do
        if(entity.is_enemy(player)) then
            local enemypawn = entity.get_player_pawn(player)
            local health = memory.read_integer(enemypawn + 0x324)
            local playername = entity.get_player_name(player)
            temp_ent[#temp_ent + 1] = { playername, health } 
            for i, enemy in ipairs(enemy_ent) do 
                if(health > enemy[2])then goto continue end
                if(enemy[1] == playername and enemy[2] ~= health and total_hits ~= last_total_hits) then
                    local action = "Hit"
                    if(health <= 0)then
                        action = "Killed"
                    end
                    Utility.log(string.format("%s %s for %d", action, playername, enemy[2]-health))
                end
                ::continue::     
            end
        end
    end
    enemy_ent = temp_ent    
end

cheat.set_callback("paint", on_paint)
```
