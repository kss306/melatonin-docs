# Quick Start

{% hint style="info" %}
melatonin allows users to create custom functions in lua and integrates them into the cheat
{% endhint %}

## Code editor

To write code efficiently, software developers use code editors instead of Windows Notepad. One of the most popular code editors is Visual Studio Code. It's a lightweight code editor that has the added benefit of being able to integrate custom user-made extensions.

Melatonin.win has an extension for Visual Studio Code to help developers access the API functions without typing them all out or looking into the documentation.

[Download Visual Studio Code](https://code.visualstudio.com/download)&#x20;

[Download Extension](https://marketplace.visualstudio.com/items?itemName=ef.melatoninlua)

## Script location

{% hint style="warning" %}
melatonin has a dedicated folder for the script to be placed in / created in
{% endhint %}

The script path is: `C:\Users\username\AppData\Roaming\Melatonin\scripts`

You can also press <mark style="color:blue;">**Win+R**</mark> and type <mark style="color:yellow;">`%appdata%`</mark> into the pop-up to quickly access the Roaming folder. Just scroll down to the <mark style="color:yellow;">`Melatonin\scripts`</mark> folder.&#x20;

Or, to make it really simple, just press <mark style="color:purple;">Open Folder</mark> in the Scripts tab inside Melatonin

## First script

#### This basic script will render a basic line ESP from the bottom of the screen to each enemy

First of all, we want a way to toggle the ESP in the cheat's UI. To do that, we will create a checkbox

{% code lineNumbers="true" fullWidth="false" %}
```lua
local enable = gui.new_checkbox("Enable")
```
{% endcode %}

Next, we need a way to draw on the screen. For this, we use a callback from Melatonin called <mark style="color:yellow;">`paint`</mark>. This callback is called every frame, so it’s perfect for this situation. To access this callback, we need the function <mark style="color:yellow;">`cheat.set_callback(cb, func)`</mark>

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()

end)
```
{% endcode %}

Inside the callback function, we will write code to find all enemy players and draw a line to their origin point. But first, we will check if we are still alive and if the checkbox is enabled. For that, we need to declare the local player

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
end)
```
{% endcode %}

The variable <mark style="color:yellow;">`lp`</mark> is now the local player. The function <mark style="color:yellow;">`engine.get_local_player()`</mark> is provided by the Melatonin API. Now, we will integrate the alive check and the checkbox check

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    
    if (entity.is_alive(lp) and gui.get(enable)) then
    
    end
end)
```
{% endcode %}

Okay, now that we know we are alive and the checkbox is ticked, we can get all enemy entities. We do this by looping through the list of players on the server and checking if they are enemies

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    
    if (entity.is_alive(lp) and gui.get(enable)) then
        for i, player in ipairs(entity.get_players()) do
            if(entity.is_enemy(player)) then
            
            end
        end

    end
end)
```
{% endcode %}

In the next step, we will get our monitor resolution and divide the width of the screen by 2. This will give us the coordinate for the center of the monitor

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    
    if (entity.is_alive(lp) and gui.get(enable)) then
        for i, player in ipairs(entity.get_players()) do
            if(entity.is_enemy(player)) then
                local sw,sh = cheat.get_window_size()
                local x,y = sw/2, sh

            end
        end

    end
end)
```
{% endcode %}

Now we have an <mark style="color:yellow;">`x`</mark> and a <mark style="color:yellow;">`y`</mark> coordinate for the line to start from. The next step is to get the player origin

{% code lineNumbers="true" %}
```lua
local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    
    if (entity.is_alive(lp) and gui.get(enable)) then
        for i, player in ipairs(entity.get_players()) do
            if(entity.is_enemy(player)) then
                local sw,sh = cheat.get_window_size()
                local x,y = sw/2, sh
                
                local enemy_x, enemy_y = utility.world_to_screen(entity.get_origin(player))
            end
        end

    end
end)
```
{% endcode %}

We use the function <mark style="color:yellow;">`utility.world_to_screen`</mark> to convert the 3-dimensional coordinates of the enemy to a point on our screen. Now we know where the enemy is and where to draw the line to

<pre class="language-lua" data-title="line_esp.lua" data-line-numbers><code class="lang-lua">local enable = gui.new_checkbox("Enable")

cheat.set_callback("paint", function()
    local lp = engine.get_local_player()
    
    if (entity.is_alive(lp) and gui.get(enable)) then
        for i, player in ipairs(entity.get_players()) do
            if(entity.is_enemy(player)) then
                local sw,sh = cheat.get_window_size()
                local x,y = sw/2, sh
                
                local enemy_x, enemy_y = utility.world_to_screen(entity.get_origin(player))
                
<strong>                render.line(x, y, enemy_x, enemy_y, 255, 255, 255, 255, 2)
</strong>            end
        end

    end
end)
</code></pre>

Done. We drew a line from the bottom center of our screen to the enemy’s position. I know, line ESP isn't very modern or cool, but the key takeaways from these steps are:

1. Create a <mark style="color:yellow;">`gui`</mark> element for the cheat UI
2. Create a callback function&#x20;
3. Check entity attributes, e.g., <mark style="color:yellow;">`is_alive`</mark> or <mark style="color:yellow;">`is_enemy`</mark>
4. Loop through the players on the server
5. Get the screen size
6. Use <mark style="color:yellow;">`world_to_screen`</mark>
7. Draw using the render functions

I hope you found this getting started section useful. If you have any questions about the docs or Lua coding in general, feel free to ask in the #lua channel in the Melatonin Discord

