# NavBot-Helper-DoDS
Config file of key binds to help with NavBot with Day of Defeat: Source https://github.com/caxanga334/NavBot


# NavBot Helper Keybinds Table

| Key                 | Action                                | Description                                                                                                              |
|--------------|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| F1                  | Edit Connections                      | Cycle connection edit modes: Connect / Disconnect. Right Click: Mark nav area. Left Click: Connect/Disconnect.          |
| F2                  | Edit Area                             | Cycle area edit types: Create, Delete, Splice, Split, Merge, Chop. Right Click: Select/start area. Left Click: Perform action. |
| F3                  | Area Attributes                       | Cycle area attribute types: Transient, Avoid, Crouch, Stop, No Allies, No Axis, Bombs to Open, Requires Prone, Remove All. Right Click: Mark area. Left Click: Apply attribute. |
| F4                  | Ladder Editing                        | Cycle ladder editing modes: Auto, Manual, Flip. Right Click / Left Click: Ladder actions.                               |
| F5                  | Build / Test Nav Paths                | Cycle path-finding test modes: All, My Team, Allied, Axis. Right Click: Mark destination. Left Click: Start path test. |
| F6                  | Adjust Area Height                    | Cycle through area height options: 1 / 10 / 100 / On Ground. Left / Right Click: Select area. Mouse Wheel: Raise / Lower height. |
| F7                  | Set Selection Mode                    | Cycle selection editing modes: Look to Add, Drag to Add. Right Click: Begin selection. Left Click: End selection.       |
| F9                  | Mark Walkable Areas                   | Toggle marking walkable areas. Left / Right Click: Mark walkable area or delete all walkable marks.                     | 
| F10                 | Seed Walkable Spots                   | Seeds walkable spots for initial nav mesh generation.                                                                    |
| F11                 | Generate Incremental Nav Mesh         | Run incremental nav mesh generation after seeding walkable spots.                                                        |
| Keypad /            | Toggle Waypoint Edit                  | Toggle waypoint editing mode on/off.                                                                                     |
| Keypad *            | Toggle NavMesh Edit                   | Toggle full nav mesh editing mode on/off.                                                                                |
| Keypad Up Arrow     | Waypoint Radius Cycle                 | Cycle waypoint radius: 0 → 16 → 32.                                                                                     |
| Keypad 5            | Waypoint Team Cycle                   | Cycle waypoint team: Allied → Axis → Unassigned.                                                                        |
| Keypad Down Arrow   | Waypoint Control Point Index Cycle    | Cycle waypoint control points: View Index → 1 → 2 → 3 → 4 → 5 → 6                                                   |
| Keypad Right Arrow  | Waypoint Attribute Cycle              | Cycle waypoint attributes: MG Nest → Rifle Grenade → Prone → Point Owners Only → Point Attackers Only. Left Click: Apply attribute. |
| Keypad PLUS         | Add Waypoint                          | Adds a waypoint.                                                                                 |
| Keypad MINUS        | Delete Waypoint                       | Deletes the nearest waypoint.                                                                                            |
| Keypad ENTER        | Nav Analyze                           | Resets mouse binds, kicks all bots, sets quota to zero, compresses nav IDs, analyzes nav mesh, and prints confirmation. |
| Insert              | Show Spawn Points                     | Displays spawn points (doesn’t include teleport-only spawns on some maps).                                             |
| Page Up             | Toggle NoClip                         | Enable / Disable noclip mode.                                                                                            |
| Page Down           | Toggle Gravity                        | Toggle gravity between low (200) and normal (800).                                                                      |
| Home                | Toggle Friendly Fire                  | Toggle friendly fire on/off.                                                                                             |
| Delete              | Cycle Bot Quota                       | Cycle bot quota between preset quantities: 2 → 4 → 8 → 12 → 14.                                                        |
| End                 | Remove All Bots                       | Kick all bots and reset bot quota to zero.                                                                               |



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

# Fix Errors
## Degenerate Navigation Area
Error Example:<br>
``L 12/31/2025 - 22:28:56: [NavBot] Degenerate Navigation Area #1320 at setpos 1962.5 975 704.031``<br>
Fix with:<br>
``sm_nav_add_to_selected_set_by_id 1320``<br>
``nav_delete_marked``
