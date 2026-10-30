# DD2-Auto-Heatstone
video game mod

A tiny quality-of-life [QOL] mod for Dragon’s Dogma 2: Dark Arisen [DD2] that automatically uses a Heatstone when the game detects the Cold/Chilled condition.
I made this because constantly opening the inventory just to use a Heatstone during Norgan whiteouts became annoying. This mod does one thing and one thing only:
Cold activates → automatically use one Heatstone.
Nothing more.

Features

Automatically uses one Heatstone when the Cold/Chilled status activates.
Uses the game’s normal native item-use function.
Only targets the legitimate Heatstone item.
Verifies at runtime that the target item is actually named
Heatstone
before using it.
Checks that you actually have a Heatstone in your inventory.
Uses a one-shot latch, so it cannot rapidly consume your entire Heatstone stack.
A new Heatstone can only be used after the previous Cold status has cleared and a new Cold episode begins.
Includes an additional cooldown as another safeguard.
Can be enabled or disabled at any time through the REFramework UI.
Extremely lightweight.
No hotkeys required.
No inventory-menu interaction required.

Why the latch matters

The mod does not behave like an autoclicker.
Once it uses one Heatstone, it becomes latched and refuses to use another while the same Cold condition remains active.
In other words:
One Cold episode = maximum one automatic Heatstone use.
The mod must first observe Cold clearing before it can arm itself for another future Cold episode.
This prevents accidental rapid consumption of multiple Heatstones.

Safety

The mod is intentionally narrow and conservative.
It does not:
Spawn items.
Add items.
Delete items directly.
Manually subtract inventory quantities.
Modify stamina.
Modify health.
Modify status values.
Modify pawns.
Modify equipment.
Modify quests.
Hook game functions.
Perform raw memory writes.
Directly edit save data.
The only gameplay-changing action performed by the script is the game’s normal native Use Item function.
Before that happens, the mod checks that the expected item ID resolves at runtime to the exact name:
Heatstone
If that verification fails, the mod does nothing.

Requirements

REFramework
Fluffy Mod Manager recommended for installation
Dragon’s Dogma 2: Dark Arisen

Installation

Install the archive through Fluffy Mod Manager and enable the mod.

Installation with Fluffy Mod Manager

Make sure REFramework for Dragon’s Dogma 2 is already installed and working.
Download the AutoHeatstone ZIP archive.
Do not extract the ZIP manually.
Open Fluffy Mod Manager and select Dragon’s Dogma 2.
Open the Mod List.
Add AutoHeatstone to Fluffy using either of these methods:
Drag-and-drop method: click and hold the downloaded AutoHeatstone ZIP file in Windows Explorer, drag it over the open Fluffy Mod Manager window, and release the mouse button. Fluffy should import the ZIP into its mod list automatically.
Add Mod(s) method: use Fluffy’s Add Mod(s) option, browse to the downloaded AutoHeatstone ZIP, select it, and confirm.
If AutoHeatstone does not immediately appear in the list, click Refresh Mod List.
Find AutoHeatstone in the mod list and enable it using the checkbox/switch next to the mod.
Launch Dragon’s Dogma 2.
Once in-game, press Insert to open the REFramework menu.
Expand:
Script Generated UI → AutoHeatstone v1.0
If the AutoHeatstone panel appears there, the mod has loaded correctly.
The installed Lua script should ultimately be located at:
Dragon's Dogma 2\reframework\autorun\AutoHeatstone.lua


Uninstalling?
Close the game, open Fluffy Mod Manager, and disable AutoHeatstone from the Mod List.
You can also temporarily disable the mod while the game is running by opening:
REFramework → Script Generated UI → AutoHeatstone v1.0
and unchecking Enabled.


For reframework users who don't use fluffy - 

Installation - 

The script/file/ dot lua file goes to:
reframework/autorun/AutoHeatstone.lua
Launch the game normally.

Uninstalling?
1. Close the game
2. remove that lua file. 
Done. 


In-Game Controls

Open REFramework and go to:
Script Generated UI → AutoHeatstone
There is an Enabled checkbox.
Unchecking it immediately disables automatic Heatstone use for the current session.
If you want the mod completely disabled across launches, disable it through Fluffy Mod Manager.

How It Works

The mod monitors the game’s Cold status through the player’s status-condition controller.
When Cold becomes active:
The mod confirms the target item is actually Heatstone.
It confirms that you possess at least one.
It waits for several consecutive Cold-state checks to avoid transient triggers.
It asks the game to use exactly one Heatstone.
It latches and refuses to use another until Cold has cleared.
No inventory spam and no repeated use loop.

Compatibility

Because this is a small REFramework Lua script with no game-file replacements, it should generally coexist well with other mods.
However, as with any REFramework mod, a future Dragon’s Dogma 2 or REFramework update could change internal game APIs.
If a major game or REFramework update releases, disabling the mod temporarily until compatibility is confirmed is recommended.

Credits

Thanks to the REFramework project for making lightweight runtime scripting possible.
Thanks also to the author of ItemBelt, Zephyr. ItemBelt’s current Dark Arisen implementation was extremely useful for confirming the correct Heatstone item data and the game’s native item-use path.
Thanks to jeremy bentham for inspiring me to make people happy! The image is of jeremy bentham.
GPT 5.6 (medium and high thinking mode).
