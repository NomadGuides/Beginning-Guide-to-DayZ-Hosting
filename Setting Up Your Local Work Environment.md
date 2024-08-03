```markdown
# How-To Create A Vanilla DayZ SA Server

## Requirements

To create your own DayZ SA Server on Windows (VM or dedicated server), you should be able to:

- Navigate a Windows directory structure.
- Open ports on the Windows firewall.
- Open/forward ports on your router (if hosted locally).
- Create and run a batch (.BAT) file.
- Find and edit various configuration files (mostly XML and JSON).

If you’ve rented a server from a GSP, this guide might not be necessary but will provide useful background. I recommend reading [How-To Add Mods To A DayZ SA Server](#) and [How-To Customize A DayZ SA Server](#).

DayZ SA is self-contained and doesn’t require an external database, unlike A2:DayZMod.

## Super Quick Non-Installation

1. **Download DayZ Server** from Steam -> Library -> Tools
   - You don’t need a second copy of DayZ or a separate Steam account to run a server.
   - DayZ Server Experimental is a separate download.

2. **Edit `serverDZ.cfg`** located at `C:\Program Files (x86)\Steam\steamapps\common\DayZServer\serverDZ.cfg`
   - Change the `hostname` variable to your server name. It can be a maximum of 63 characters.
   ```cfg
   hostname="MyServerName";
   ```

3. **Set Launch Options** for DayZ Server:
   - Right-click on DayZ Server -> Properties.
   - In the General tab, add the following in Launch Options:
     ```
     -config=serverDZ.cfg -profiles=profile
     ```
   - Press OK, then Close.

4. **Configure Firewall and Router:**
   - Add INBOUND rules to the Windows firewall and forward the following default ports if needed:
     - 2302, 27016 (both UDP only).

5. **Create and Run a Batch File:**
   - Create a file named `start_dayzserver.bat` with the following content:
     ```bat
     @echo off
     :start
     ::Server name [!EDIT THIS!]
     set serverName=EXAMPLE NAME
     ::Server files location [DEFAULT !EDIT AS NEEDED!]
     set serverDirectory="C:\Program Files (x86)\Steam\steamapps\common\DayZServer"
     ::Server Port [DEFAULT]
     set serverPort=2302
     ::Server config [DEFAULT. hostname= in serverDZ.cfg is what shows in the steam server browser. !EDIT AS NEEDED!.]
     set serverConfig=serverDZ.cfg
     ::Server profile location. logfiles are written here and mods are configured here [DEFAULT]
     set serverProfile=profile
     ::Logical CPU cores to use (Equal or less than available)
     set serverCPU=4
     ::modlist should be of the form "-mod=@mod1;@mod2;@mod3;"
     set modList="-mod="
     ::Sets title for terminal (DONT edit)
     title %serverName% batch
     ::DayZServer location (DONT edit)
     cd /D "%serverDirectory%"
     :: makes the profile directory if it doesn't already exist
     if not exist "%serverProfile%" ( 
     mkdir %serverProfile% > nul
     ) 
     echo (%time%) %serverName% started.
     ::Launch parameters (edit end: -config=|-port=|-profiles=|-doLogs|-adminLog|-netLog|-freezeCheck|-filePatching|-BEpath=|-cpuCount=)
     start "DayZ Server" /min DayZServer_x64.exe -config=%serverConfig% -port=%serverPort% -profiles=%serverProfile% -BEpath=battleye %modList% -cpuCount=%serverCPU% -dologs -adminlog -netlog -freezecheck

     ::Time in seconds before kill server process (14400 = 4 hours)
     timeout 14400
     taskkill /im DayZServer_x64.exe /F
     ::Time in seconds to wait before..
     timeout 10
     ::Go back to the top and repeat the whole cycle again
     goto start
     ```

## Full Installation

1. **Download DayZ Server** from Steam -> Library -> Tools
   - By default, the files will be in `C:\Program Files (x86)\Steam\steamapps\common\DayZServer`.
   - Copy this directory to another location to avoid auto-updates from Steam overwriting your changes. For simplicity, use `C:\dayzserver\` and refer to it as `<server_root>`.

2. **Configure Server Parameters** by editing `<server_root>\serverDZ.cfg`:
   - Change the `hostname` variable to your server name (max 63 characters).
     ```cfg
     hostname="MyServerName";
     ```
   - Set a password if desired:
     ```cfg
     password="MyServerPassword";
     ```
   - Set `steamQueryPort` if needed (usually not necessary):
     ```cfg
     steamQueryPort=27016; // default
     ```

3. **Configure RCON Access**:
   - Edit or create `<server_root>\battleye\BEServer_x64.cfg`:
     ```cfg
     RConPort 2322
     ```
   - Avoid using gameport+2,3,4.

4. **Set Game Port** on the command line using `-port=<game_port>`. Default is 2302:
   ```
   -port=2302
   ```

5. **Configure Firewall and Router:**
   - Add INBOUND rules to the Windows firewall and forward the gameport and steamqueryport (UDP) as needed (default: 2302 & 27016).
   
6. **Run the Server** via command line or batch (.BAT) file:
   - Example command line:
     ```bat
     "C:\Windows\System32\cmd.exe " /C start "DayZSA" C:\dayzserver\DayZServer_x64.exe "-config=C:\dayzserver\serverDZ.cfg" -port=2302 "-profiles=C:\dayzserver\profile" "-BEPath=C:\dayzserver\battleye" -dologs -adminlog
     ```

## Using BEC for START/STOP/RESTART and Messages [In Process of Writing This Section]

- **BattlEye Extended Controls (BEC)** provides basic admin controls and messaging. Note that there is no restart command for the server; BEC can stop the server at a specified time or schedule. 
  - [Download BEC](#)
  - Edit `<server_root>\BattlEye\BEServer_x64.cfg` and set `RconPort`:
    ```cfg
    RconPort 2322
    ```
  - Put BEC files in `<server_root>\BEC`.
  - Edit `<server_root>\BEC\Config\Config.cfg`:
    - Set IP to your server’s public IP.
    - Set Port to your game port (default 2302).
    - Set `BePath` to where BattlEye is located (default `<server_root>\Battleye`).

## Starting a Server with Mods

1. **Add Mods** by following [How-To Add Mods To A DayZ SA Server](#).
2. **Run the Server** with mods via command line or batch (.BAT) file, replacing `@mod1;@mod2;@mod3;` with your mods:
   ```bat
   "C:\Windows\System32\cmd.exe " /C start "DayZSA" C:\dayzserver\DayZServer_x64.exe "-config=C:\dayzserver\serverDZ.cfg" -port=2302 "-profiles=C:\dayzserver\profile" "-mod=@mod1;@mod2;@mod3;" "-BEPath=C:\dayzserver\battleye" -dologs -adminlog
   ```

## Supporting DayZSALauncher

- **Add Your Server** to DayZSALauncher by visiting [DayZSALauncher Server Check](https://dayzsalauncher.com/#/servercheck). Use your server’s IP and SteamQueryPort (27016).

## START/STOP/RESTART

- **Automatic Restart:** There’s no built-in restart command for DayZ. Use a script or app that starts the server, monitors the process, and restarts it if necessary. You may also need a tool to shut down the server at regular intervals.
  - **BEC** has messaging and shutdown options.
  - **CF Tools** is a complete management app.
  - Custom `.BAT` files for managing the server can be used if you understand scripting.

## Troubleshooting

- **XAPOFX1_5.dll is Missing:**
  - Download and install DirectX.

- **Server Not Accessible or Not Showing Up:**
  - Ensure INBOUND firewall rules and port forwarding are configured. Check `DayZServer_x64<date-time>.RPT` for port information.

- **Server Not Showing Up on DayZSALauncher:**
  - Add your server to the DayZSALauncher list at [DayZSALauncher Server Check](https://dayzsalauncher.com/#/servercheck).

- **Cannot Connect with RCON-Based Tools:**


  - Ensure `RconPort` is set in `<server_root>\battleye\BEServer_x64.cfg`.

- **No Loot or Infected Spawning:**
  - Check XML file typos or configuration issues. Validate XML and JSON files using:
    - [XML Validation](https://www.xmlvalidation.com/)
    - [JSON Lint](https://jsonlint.com/)

- **Server Crashing or Other Errors:**
  - Review server and mod log files for errors. Validate syntax using:
    - [XML Validation](https://www.xmlvalidation.com/)
    - [JSON Lint](https://jsonlint.com/)
```
