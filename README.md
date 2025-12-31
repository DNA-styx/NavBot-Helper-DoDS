# NavBot-Helper-DoDS
Config file of key binds to help with NavBot with Day of Defeat: Source https://github.com/caxanga334/NavBot


# NavBot Helper Keybinds Table


| Key         | Action                                | Description                                                                                                              |
|-------------|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| F1          | Edit Connections                    | Key Press: Connect, Disconnect. Right Click: Select area. Left Click: Perform Action                                          |
| F2          | Edit Area                           | Key Press: Create, Delete, Split, Splice, Merge. Right Click: Select area. Left Click: Perform Action.          |
| F3          | Area Attributes                     | Key Press: Cycle area attribute types. Right Click: Select area. Left Click: Apply attribute                                           |
| F4          | Add Ladders                         | Key Press: Auto, manual create, flip. Right Click: Select Area                                     |
| F5          | Test Nav Paths                      | Cycle path-finding test modes. Right Click: Select final area. Left Click: start test from current location              |
| F6          | Adjust Area Height					| Cycle through area height changes (Options: 1/10/100/fix to ground) (Left/Right Click: Select Area, Mouse Wheel: raise/lower)   |
| F9          | Mark Walkable Areas					| Enable marking walkable areas with mouse buttons (Left/Right click: Mark Walkable)                                             | 
| F10         | Seed Walkable Spots 				| Seed walkable spots for initial nav mesh generation                                                                             |
| F11         | Generate Incremental Nav Mesh       | Run after Seed walkable spots and marking walkable areas                                                                       |
| Insert      | Show Spawn Points                   | Useful for finding spawn points. Doesn't include spawn point teleports used on some maps                                        |
| Page Up     | Toggle NoClip                       | Toggle noclip mode on/off                                                                                                      |
| Page Down        | Toggle Gravity                      | Toggle gravity between low (200) and normal (800)                                                                              |
| Home        | Toggle Friendly Fire                | Toggle friendly fire on/off                                                                                                    |
| Delete      | Cycle Bot Quota                     | Cycle bot quota between preset quantities                                                                                      |
| End         | Remove All Bots                     | Kicks all bots and set bot quota to zero. Do this before editing                                                              |
| Keypad ENTER    | Run Nav Analyze                     | Kicks all bots, set bot quota to zero, saves the nav file and restarts the map                                                 |


# New map process
- Copy .cfg file to \dod\cfg
- Load map
- Load keybinds by typing `exec navbot-helper-dods.cfg`
- Press "Page Up" to enable god mode
- Press "F10" to Seed Walkable spots
- Press "F11" to Generate Nav Mesh
- Press Enter to Save Nav Mesh
- Fly around map and look for walkable areas not covered with nav mesh if you find any
  - Press "F9" to enable Mark as Walkable. Left click to place marker
  - Press "F11" to generate the nav mesh
  - If these new areas are on top of already existing ones, use sm_nav_delete_overlapping_from_selected_set to remove them
  - Press "Enter" to save
  - Repeat process until all walkable areas have nav mesh
- Press "Insert" to show spawn points and make sure they have nav mesh
- Add ladders (to be added)
- Look for disconnected nav mesh and join them with "F1"
- Look for and remove nav mesh from non walkable areas (e.g tops of buildings, places you don't want the bots going)

# Misc useful commands
- `sm_nav_snap_to_grid 1`
- `sm_navbot_tool_bots_go_to` makes bots come to your location
- `sm_navbot_debug_blind` bots can't see each other
- `sm_nav_merge_ladders <bottom ladder ID> <top ladder ID>` merge/join ladders that are close to each other
