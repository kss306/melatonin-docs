# Text on player bone

**This code example will showcase how to render text on any bone from any player**

First of all we need to create a callback of the paint event and a gui checkbox for toggling the render process via the cheat gui

<pre class="language-lua"><code class="lang-lua"><strong>local enable = gui.new_checkbox("Enable")
</strong>
local function on_paint()
    -- called every frame
end

cheat.set_callback("paint", on_paint)
</code></pre>

***

Now we will add a reference to the local player and check if it's alive and if the checkbox is checked

<pre class="language-lua"><code class="lang-lua"><strong>local enable = gui.new_checkbox("Enable")
</strong>
local function on_paint()
    -- called every frame
    local lp = engine.get_local_player()
    if(gui.get(enable) and entity.is_alive(lp)) then
        -- checkbox is toggled and local player is alive
        
    end
end

cheat.set_callback("paint", on_paint)
</code></pre>

***

We will now loop through all the player entities

<pre class="language-lua"><code class="lang-lua"><strong>local enable = gui.new_checkbox("Enable")
</strong>
local function on_paint()
    -- called every frame
    local lp = engine.get_local_player()
    if(gui.get(enable) and entity.is_alive(lp)) then
        -- checkbox is toggled and local player is alive
        for i, player in ipairs(entity.get_players()) do
            -- the entity is now stored in the variable player
        end
    end
end

cheat.set_callback("paint", on_paint)
</code></pre>

***

Now that we got the entity reference, we can get their bone position and store the position of the bone as a 2D coordinate on screen. We will use the Head bone which has the ID 6. Check out all the other bone ID's here [#bone-id-list](../api-documentation/extra-infos.md#bone-id-list "mention")

<pre class="language-lua"><code class="lang-lua"><strong>local enable = gui.new_checkbox("Enable")
</strong>
local function on_paint()
    -- called every frame
    local lp = engine.get_local_player()
    if(gui.get(enable) and entity.is_alive(lp)) then
        -- checkbox is toggled and local player is alive
        for i, player in ipairs(entity.get_players()) do
            -- the entity is now stored in the variable player
            local bone_x, bone_y = utility.world_to_screen(entity.bone_position(player, 6))
            
        end
    end
end

cheat.set_callback("paint", on_paint)
</code></pre>

***

We can now use those x and y values to draw text in their position

<pre class="language-lua"><code class="lang-lua"><strong>local enable = gui.new_checkbox("Enable")
</strong>
local function on_paint()
    -- called every frame
    local lp = engine.get_local_player()
    if(gui.get(enable) and entity.is_alive(lp)) then
        -- checkbox is toggled and local player is alive
        for i, player in ipairs(entity.get_players()) do
            -- the entity is now stored in the variable player
            local bone_x, bone_y = utility.world_to_screen(entity.bone_position(player, 6))
            render.text(bone_x, bone_y, 255, 255, 255, 255, 0, true, "Player")
        end
    end
end

cheat.set_callback("paint", on_paint)
</code></pre>
