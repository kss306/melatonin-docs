---
description: >-
  This page documents all the extra event callbacks the custom_callbacks.lua
  provides
---

# Custom Callbacks

## Implementing the script

```lua
local cc = require("custom_callbacks")
local events = cc.events

local function player_hurt(data)
    local player_hit = data[1]
    local player_damager = data[2]
    local dmg_taken = data[3]
    local hp_left = data[4]
    local body_part = data[5]
end

cc.set_callback(events.player_hurt, player_hurt)
```

***

## List of all events

1. [round\_start](custom-callbacks.md#round\_start)
2. [round\_end](custom-callbacks.md#round\_end)
3. [player\_hurt](custom-callbacks.md#player\_hurt)
4. [item\_purchase](custom-callbacks.md#item\_purchase)
5. [bomb\_beginplant](custom-callbacks.md#bomb\_beginplant)
6. [bomb\_abortplant](custom-callbacks.md#bomb\_abortplant)
7. [bomb\_planted](custom-callbacks.md#bomb\_planted)
8. [bomb\_exploded](custom-callbacks.md#bomb\_exploded)
9. [bomb\_dropped](custom-callbacks.md#bomb\_dropped)
10. [bomb\_pickup](custom-callbacks.md#bomb\_pickup)
11. [bomb\_begindefuse](custom-callbacks.md#bomb\_begindefuse)
12. [bomb\_abortdefuse](custom-callbacks.md#bomb\_abortdefuse)
13. [bomb\_defused](custom-callbacks.md#bomb\_defused)
14. [player\_connected](custom-callbacks.md#player\_connected)
15. [player\_disconnected](custom-callbacks.md#player\_disconnected)

***

{% hint style="warning" %}
The events return a optinal array of data to the callbacks. [See in the implementation](custom-callbacks.md#implementing-the-script)
{% endhint %}

### round\_start

| Data Type | Name          | Description                          |
| --------- | ------------- | ------------------------------------ |
| int       | round\_number | The number of the now starting round |

***

### round\_end

| Data Type | Name          | Description                    |
| --------- | ------------- | ------------------------------ |
| int       | round\_number | The number of the played round |

***

### player\_hurt

| Data Type | Name            | Description                               |
| --------- | --------------- | ----------------------------------------- |
| int       | player          | Index of the player that received damage  |
| int       | player\_damager | Index of the player that dealt the damage |
| int       | dmg\_taken      | The damage that the player took           |
| int       | hp\_left        | Health left                               |
| int       | body\_part      | Index of the hit body part                |

***

### item\_purchase

| Data Type | Name   | Description                                     |
| --------- | ------ | ----------------------------------------------- |
| int       | player | Index of the player that bought / sold the item |
| string    | item   | Name of the bought / sold item                  |
| int       | cost   | Amout of added / subtracted money               |

***

### bomb\_beginplant

| Data Type | Name        | Description                              |
| --------- | ----------- | ---------------------------------------- |
| int       | player      | Index of the player that is planting     |
| string    | bomb\_spot  | Name of the bomb spot                    |
| float     | planted\_in | Time in seconds when the bomb is planted |

***

### bomb\_abortplant

| Data Type | Name       | Description                               |
| --------- | ---------- | ----------------------------------------- |
| int       | player     | Index of the player that stopped planting |
| string    | bomb\_spot | Name of the bomb spot                     |

***

### bomb\_planted

| Data Type | Name        | Description                                       |
| --------- | ----------- | ------------------------------------------------- |
| int       | player      | Index of the player that planted                  |
| string    | bomb\_spot  | Name of the bomb spot                             |
| float     | bomb\_timer | Time in seconds when the bomb is going to explode |

***

### bomb\_exploded

| Data Type | Name       | Description                      |
| --------- | ---------- | -------------------------------- |
| int       | player     | Index of the player that planted |
| string    | bomb\_spot | Name of the bomb spot            |

***

### bomb\_dropped

| Data Type | Name   | Description                               |
| --------- | ------ | ----------------------------------------- |
| int       | player | Index of the player that dropped the bomb |
| int       | bomb   | Index of the bomb entity                  |

***

### bomb\_pickup

| Data Type | Name   | Description                                 |
| --------- | ------ | ------------------------------------------- |
| int       | player | Index of the player that picked up the bomb |

***

### bomb\_begindefuse

| Data Type | Name          | Description                               |
| --------- | ------------- | ----------------------------------------- |
| int       | player        | Index of the player that started defusing |
| string    | bomb\_spot    | Name of the bomb spot                     |
| float     | defuse\_timer | Time in seconds when the defuse is done   |
| bool      | has\_kit      | True / False if player has a defuse kit   |

***

### bomb\_abortdefuse

| Data Type | Name       | Description                               |
| --------- | ---------- | ----------------------------------------- |
| int       | player     | Index of the player that stopped defusing |
| string    | bomb\_spot | Name of the bomb spot                     |

***

### bomb\_defused

| Data Type | Name        | Description                                      |
| --------- | ----------- | ------------------------------------------------ |
| int       | player      | Index of the player that defused                 |
| string    | bomb\_spot  | Name of the bomb spot                            |
| float     | bomb\_timer | Time in seconds when the bomb should be exploded |

***

### player\_connected

| Data Type | Name   | Description                        |
| --------- | ------ | ---------------------------------- |
| int       | player | Index of the player that connected |

***

### player\_disconnected

| Data Type | Name   | Description                           |
| --------- | ------ | ------------------------------------- |
| int       | player | Index of the player that disconnected |
