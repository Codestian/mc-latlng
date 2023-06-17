# MC-LATLNG

An automation script (RPA) to create points from a list of LatLng coordinates in Minecraft, especially for the BuildTheEarth (BTE) project.

## Requirements

For Minecraft, ensure `/tpll` is enabled. No worldedit is necessary, just ensure you have permissions to execute `/setblock`.

For macOS, ensure you have the Automator app enabled. To setup, open Automator and select a file named `RPA` inside this repo's mac folder. In other platforms it will show up as `RPA.workflow` but mac shows it as only `RPA` with a preview image.

There is no Windows support yet, but you may need Power Automate which is only available for Windows 10 and above. 

## Why would I want to use this?

When building stuff in BTE, we often need to reference map providers. For example, if we want to build a curve, we would need to copy a few LatLng coordinates across the curve in the map, and join them together manually in game using commands such as //curve. However, copying and pasting the coordinates into the game takes a lot of time and effort. This tool aims to automate the pasting part. All you need to do is paste all your LatLng coordinates into a .txt file. Refer to the example.txt file for formatting.

## How does it work?

First, you need to select a .txt file containing the list of LatLng coordinates. Quickly focus to the Minecraft window and unpause the game. The program will then proceed to do the following steps after 2 seconds in a loop:

1. Type `/tpll LAT, LNG 12` and press enter. This teleports your player to the location, based on `LAT, LNG`. By default, it will be at 12.
2. Type `t` and press enter. This opens the chat prompt.
3. Type `/setblock ~ ~-1 ~ minecraft:gold_block` and press enter. This will set the block below the player. By default, it will be gold block.
4. Go back to step 1 and repeat with next row of LatLng coordinates.

Once all coordinates have been looped through, the program will press the `esc` key and pause the game. 