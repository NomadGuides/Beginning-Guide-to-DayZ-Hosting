```markdown
# How-To Add Mods To A DayZ SA Server

This guide assumes that you’ve read [Setting Up Your Local Work Environment](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/Setting%20Up%20Your%20Local%20Work%20Environment).

## Definitions

- `<server_root>`: The base directory for all your server files. Typically this is where `DayZServer_x64.exe`, `serverDZ.cfg`, the `mpmissions` directory and other files/directories are located.
- `<server_profile>`: A subdirectory of `<server_root>` that contains the main DayZ log file (`DayZServer_x64*.RPT`) and is specified on the command line as `-profiles`.

## Finding/Downloading/Installing Mods

1. Browse the Steam Workshop for DayZ to find interesting mods for your server. Subscribe to the ones that you want.
2. Alternatively, you can use STEAMCMD to download mods, but you’ll still need the `publishedid`. [todo: write up a short STEAMCMD tutorial]
3. Locating mods on your local PC:
    - If you want to find mods by ID: Copy the `<publishedid>` of the mod. The URL shows `id=<publishedid>` when you are viewing the mod. For example, the URL for the Trader Mod is `https://steamcommunity.com/sharedfiles/filedetails/?id=1590841260`, so the `<publishedid>` is `1590841260`.
    - If you want to find mods by Name: By default, mods are located via the shortcuts in `C:\Program Files (x86)\Steam\steamapps\common\DayZ`.
4. Grab all the files from either `C:\Program Files (x86)\Steam\steamapps\workshop\content\22100\<publishedid>` (by ID) or `C:\Program Files (x86)\Steam\steamapps\common\DayZ\!Workshop\@<ModName>` (by name).
5. Place those files in the server root in a directory like `@<modname>` where `<modname>` is the name from the workshop or the name from `meta.cpp`. For example, `<server_root>\@Trader`.
6. Find the mod's key file (`*.bikey`) and copy it to `<server_root>\keys`.

## Running the Server

Run the server via this command (replacing `@mod1;@mod2;@mod3;` with your mods):

```bash
"C:\Windows\System32\cmd.exe" /C start "DayZSA" C:\dayzserver\DayZServer_x64.exe -config=C:\dayzserver\serverDZ.cfg -port=2302 -profiles=C:\dayzserver\profile "-mod=@mod1;@mod2;@mod3;" -BEPath=C:\dayzserver\battleye -dologs -adminlog
```

## Configuring Mods

For a complete discussion of the XML config files, read [How-To Customize A DayZ SA Server](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/How-To%20Customize%20A%20DayZ%20SA%20Server) and [DayZ SA Server Mission Files](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/DayZ%20SA%20Server%20Mission%20Files).

Mods should include the following XML config files:

- `types.xml` (loot table) if new items are added
- `cfgspawnabletypes.xml` (attachments + cargo) for items and vehicles
- `events.xml` (dynamic events) if spawning things like vehicles
- `cfgeventspawns.xml` (event coordinates) for event locations

## Troubleshooting

- Is the mod loaded on the server?
- Does the mod name on the command line (`"-mod=@mod1;"`) match the directory name of the mod in the `<server_root>` folder?
- Did you copy the key (`*.bikey`) from the mod into the `<server_root>\keys` directory?
- Did you add any necessary XML config files required by the mod?
- Did you add any necessary mod-specific configuration files?
- No loot or infected are spawning? Most likely a typo in an XML file. Use these tools to validate your XML files:
    - [XML Validation](https://www.xmlvalidation.com/)
    - [DayZ Skyn1](https://dayz.skyn1.se/)
    - [DayZ Types Pro](http://dayztypes.pro/)
- Is the mod loaded on the client? Did you use the in-game browser and join with the necessary mods automatically? Did you use DayZ Launcher and have it join with the necessary mods automatically?
```

Feel free to adjust any specific details or add additional information as needed.
