Minetest mission mod (missions)
======

Minetest mod for in-game mission creation
Adds blocks to create missions with rewards, timeout and penalties

* Github: [https://github.com/thomasrudin-mt/missions](https://github.com/thomasrudin-mt/missions)
* Forum Topic: [https://forum.minetest.net/viewtopic.php?f=9&t=20125](https://forum.minetest.net/viewtopic.php?f=9&t=20125)

Supported missions:
* Transport (to mission-chest)
* Craft
* Build
* Dig

# Install

* Unzip/Clone it to your worldmods folder

# Blocks

The blocks have no recipe because they should be used by a admin or creative-player.
The nature of the mission-reward could be abused for cheating if a survival-player could craft it.

## Mission-chest (missions:chest)

The mission chest acts as a target for transport-missions. The book in the right-click menu is used as a reference to it (placed in the transport block menu)

# Mission-types

## Transport (missions:transport)

A simple transport mission, in which blocks/items must be place in the target chest (displayed in hud, if started)
This block can be configured only by its owner:

* **Target**: The target mission-chest (book-reference)
* **Time**: Time for the mission in seconds
* **Reward**: Block/Items rewards if the mission is completed
* **Transport**: Blocks/items to transport/craft. All items must be placed in the **to**-chest for mission completion

XP mod fields (for xp_redo, if enabled)

* **XP-Reward** amount of xp to reward on completion
* **XP-Penalty** amount of xp to take away if the mission fails (timeout) must be positive

Buttons:

* **Save** Saves the configuration
* **Start** Starts the mission for the player

## Build

Build nodes

## Dig

Dig nodes/items

## Craft

Craft items

# Depends

* default
* [xp-redo](https://github.com/thomasrudin-mt/xp_redo)?

# Screenshots

## Mission-blocks (chest and mission-types)
![](screenshots/Minetest_2018-05-17-09-18-20.png?raw=true)
Note: **Android screenshot**

## Mission chest with book as reference
![](screenshots/Minetest_2018-05-17-09-18-38.png?raw=true)

## Example transport mission configuration
![](screenshots/Minetest_2018-05-28-10-12-59.png?raw=true)

## Running transport mission
![](screenshots/Minetest_2018-05-17-10-28-35.png?raw=true)

## Running dig-mission
![](screenshots/Minetest_2018-05-28-10-13-28.png?raw=true)

# Lua api

## misssions.start_mission(player, missionSpec)

```lua
missionSpec = {
	name = "Mission name",
	type = "transport", -- "build", "craft", "dig"
	time = 300, --seconds
	xp = { -- optional
		reward = 100,
		penalty = 50
	},
	reward = {
		"default:stone 50"
	},

	-- build, craft, dig, transport mission
	context = {
		list: {
			"default:stone 10"
		}
	},

	-- transport mission
	target = {
		x = 100,
		y = 200,
		z = 300,
		title = "Town chest"
	}
}
```

# Pull requests / bugs

I'm happy for any bug reports or pull requests (code and textures)

# TODO / Ideas

* Kill mission
* Goto mission
* Walk mission
* Display current missions in sfinv/unified inv
* Mission stats / export
* Persist missions across server-restart (player:set_attribute)
* HUD improvements
