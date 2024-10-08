# How-To Modify Your DayZ SA Server

If you’re going to modify your DayZ SA server, you should be able to:

- Find your way around a Windows directory structure.
- Find/edit various configuration files (mostly XML & JSON).

I’ll assume that you’ve either read [Setting Up Your Local Work Environment](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/Setting%20Up%20Your%20Local%20Work%20Environment).

Without coding or creating a STEAM Workshop mod (PC-only), a number of features of DayZ can be modified such as:

- The Central Loot Economy (CLE)/loot table.
- Items, spawn amounts, locations, and rarity.
- Dynamic events like vehicles, infected, animals, heli crashes, and contaminated areas.
- Hit direction indicator.
- Base building conditions and damage.
- Map additions (easier with a PC, but can be loaded on console).
- Lighting, stamina, and more!

## Definitions

- `<server_root>`: The base directory for all your server files. Typically this is where `DayZServer_x64.exe`, `serverDZ.cfg`, the `mpmissions` directory, and other files/directories are located.
  - On a GSP, `<server_root>` is most likely the root directory where you log in via FTP or some control panel file manager.
- `<server_profile>`: A subdirectory of `<server_root>` that contains the main DayZ log file (`DayZServer_x64*.RPT`) and is specified on the command line as `-profiles`.
- `<server_mission>`: A subdirectory under `<server_root>` that contains the mission files for the particular map you are using.
  - For example, the map name for Chernarus is “chernarusplus” and Livonia is “enoch”.
  - `<server_mission>` is located in `<server_root>\mpmissions\dayzOffline.<mapname>`.

## XML Config Files

The most typical files to edit when tweaking your server or adding mods are:

- `types.xml` (loot table).
- `cfgspawnabletypes.xml` (attachments + cargo) for items, vehicles, and infected.
- `events.xml` (dynamic events) for spawning vehicles, infected, crashes, and more.
- `cfgeventspawns.xml` (event coordinates) for events.

Previously, you needed to edit the vanilla files directly. This method still works but is more prone to typos and makes debugging much harder.

The new method involves creating a subdirectory of `<server_mission>` and including your changes in `cfgeconomycore.xml`. Refer to the BI wiki page for more details: [DayZ: Central Economy mission files modding](https://community.bistudio.com/wiki/DayZ:Central_Economy_mission_files_modding).

1. Create the directory `<server_mission>\custom`.
2. Edit `cfgeconomycore.xml` and add your changes before the closing tag (`</economycore>`) like this:

    ```xml
    <ce folder="custom">
       <file name="types_custom.xml" type="types" />
       <file name="cfgspawnabletypes_custom.xml" type="spawnabletypes" />
       <file name="events_custom.xml" type="events" />
       <file name="globals_custom.xml" type="globals" />
    </ce>
    ```

    - For each of the changes you want to make to a vanilla setting, copy the original into your custom file and make the changes. Although the documentation suggests you don’t need to include all the attributes, it’s safer to do so.
    - Each of the files MUST be a syntactically correct, well-formed XML file with open and close tags. Refer to the original files to see the format.
    - If you are adding config files from mods, change “custom” above to be the mod name and make multiple entries. This way you have a single file per purpose, per mod. When a mod changes and adds new items, your changes are limited to those files.
    - Unfortunately, this method does not include all the files you might modify, such as `cfgeventspawns.xml`, `cfgrandompresets.xml`, `cfgeventgroups.xml`, `cfgeffectarea.json`, `cfggameplay.json`, `env\*_territory.xml`, and other files, so you’ll have to edit them directly and merge changes for each release.

For a longer explanation of the XML & JSON configuration files, read [DayZ SA Server Mission Files](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/DayZ%20SA%20Server%20Mission%20Files).

## Popular Loot Table (`types.xml`) Changes

- Increase the value of `<nominal>` (basically max) to have more of an item spawned at once. Caution: there is a balance and max items the server can handle.
- Change the `in_hoarder` attribute of the `<flags>` tag to `0` so that item max doesn’t count buried/stashed items (this attribute is not used much anymore in the vanilla server configs).
- Reduce the `<lifetime>` value of the item named “UndergroundStash” to make buried crates/chests/bags despawn quicker.
- To affect heli crash loot, change the `deloot` (dynamic event) attribute of the `<flags>` tag (`1`=spawns at heli crashes and convoys).
- Change or add a `<usage>` tag (Military, Police, Hunting, Village, Farm, Industrial, Medic, Town, Coast, Firefighter, School, Office, Prison, ContaminatedArea, SeasonalEvent, Unique).
- Change or add to a `<value>` tag (Tier1, Tier2, Tier3, Tier4).

## Popular Dynamic Events (`events.xml`) Changes

- Increase the number of Military Convoys or Helicopter crashes by increasing the `<nominal>` value in the event named “StaticMilitaryConvoy” or “StaticHeliCrash”, respectively.

## Hidden or Unused Game Assets

Some people have noticed that there are assets in the game files that don’t currently spawn. The reason is that most of the items aren’t functionally complete.

You can find some working items in `types.xml` already with nominal set to `0` such as the color variants of weapons and axes or seasonal event items. There are also 145 books that used to be readable but probably aren’t due to copyright or other reasons. However, you can still add them for players to collect.

- [Books `types.xml` entries](https://pastebin.com/s2DAYmX8) you can add to your server.
- [List of class names of other unused items](https://pastebin.com/RwyxD7Nx), some that spawn and some that are problematic.

There are items noted that spawn and can be generally held in your hands, thrown, used as melee weapons, or even eaten. You’ll have to create full `types.xml` entries for these if you want to use them.

**Warning:** The weapons marked as non-functional are, not surprisingly, NON-FUNCTIONAL. Use any of these NON-FUNCTIONAL items at your own risk! Some of these items will crash your server or get stuck in your hands (e.g., RPG, chainsaw, bows, M249).

## Troubleshooting

- **No loot or infected are spawning:**
  - Most likely a typo in an XML file. Check your syntax and/or diff against the vanilla files.
    - [DZSA Tools](https://dzsa.tools/) – for `types.xml`.
    - [DayZ Types Pro](http://dayztypes.pro/) – for `types.xml` (offline).
    - [XML Validation](https://www.xmlvalidation.com/) – for any XML file (syntax only).
  - The vanilla files can be downloaded from Steam or from [here](https://github.com/BohemiaInteractive/DayZ-Central-Economy).
