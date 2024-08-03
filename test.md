Here’s the guide formatted in Markdown for your GitHub repository:

```markdown
# How-To Create A Vanilla DayZ SA Server

If you’re going to create your own DayZ SA Server on Windows (VM or dedicated server), you should be able to:

- Find your way around a Windows directory structure.
- Open ports on the Windows firewall.
- Open/forward ports on your router (if hosted locally).
- Create/run a simple batch (`.BAT`) file.
- Find and edit various configuration files (mostly XML and JSON), when making configuration changes.

I suggest reading [How-To Add Mods To A DayZ SA Server](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/How-To%20Add%20Mods%20To%20A%20DayZ%20SA%20Server) and [How-To Customize A DayZ SA Server](https://github.com/Sk3tch725/Beginning-Guide-to-DayZ-Hosting/blob/main/How-To%20Customize%20A%20DayZ%20SA%20Server).

One nice thing about DayZ SA (I’ll just call it DayZ from now on) is that setting up a server is very easy. DayZ is self-contained and doesn’t require installation of an external database (unlike A2:DayZMod).

## Super Quick Non-Installation

1. **Download DayZ Server from Steam:**
   - Go to `Library` -> `Tools`.
   - Bohemia does not require you to own a second copy of DayZ nor create another Steam account to run a server.
   - Note that DayZ Server Experimental is a separate download and can be installed similarly.

2. **Edit Configuration File:**
   - Navigate to `C:\Program Files (x86)\Steam\steamapps\common\DayZServer\serverDZ.cfg` (default location).
   - Change the `hostname` variable to the name of your server. This is the name that shows up in the server browser. It can be a maximum of 63 characters long.
     ```cfg
     hostname="MyServerName";
     ```

3. **Set Launch Options in Steam:**
   - Right-click on DayZ Server -> `Properties`.
   - In the `General` tab, in `Launch Options`, add:
     ```
     -config=serverDZ.cfg -profiles=profile
     ```
   - Press `OK`, then `Close`.

4. **Open Ports:**
   - If you want to log in to this server from another PC or outside your network, add INBOUND rules to the Windows firewall and, if needed, to the router to open and forward the following default ports:
     - 2302, 27016 (both UDP only).

5. **Run the Server:**
   - Right-click on DayZ Server -> `Launch`.
   - Alternatively, you can create a file called `start_dayzserver.bat`, paste the following block into it, edit as necessary, and then double-click on it to run.

   ```batch
   @echo off
   :start
   :: Server name [!EDIT THIS!]
   set serverName=EXAMPLE NAME
   :: Server files location [DEFAULT !EDIT AS NEEDED!]
   set serverDirectory="C:\Program Files (x86)\Steam\steamapps\common\DayZServer"
   :: Server Port [DEFAULT]
   set serverPort=2302
   :: Server config [DEFAULT. hostname= in serverDZ.cfg is what shows in the steam server browser. !EDIT AS NEEDED!.]
   set serverConfig=serverDZ.cfg
   :: Server profile location. Logfiles are written here and mods are configured here [DEFAULT]
   set serverProfile=profile
   :: Logical CPU cores to use (Equal or less than available)
   set serverCPU=4
   :: modlist should be of the form "-mod=@mod1;@mod2;@mod3;"
   set modList="-mod="
   :: Sets title for terminal (DON'T edit)
   title %serverName% batch
   :: DayZServer location (DON'T edit)
   cd /D "%serverDirectory%"
   :: Makes the profile directory if it doesn't already exist
   if not exist "%serverProfile%" ( 
   mkdir %serverProfile% > nul
   ) 
   echo (%time%) %serverName% started.
   :: Launch parameters (edit end: -config=|-port=|-profiles=|-doLogs|-adminLog|-netLog|-freezeCheck|-filePatching|-BEpath=|-cpuCount=)
   start "DayZ Server" /min DayZServer_x64.exe -config=%serverConfig% -port=%serverPort% -profiles=%serverProfile% -BEpath=battleye %modList% -cpuCount=%serverCPU% -dologs -adminlog -netlog -freezecheck
   :: Time in seconds before kill server process (14400 = 4 hours)
   timeout 14400
   taskkill /im DayZServer_x64.exe /F
   :: Time in seconds to wait before..
   timeout 10
   :: Go back to the top and repeat the whole cycle again
   goto start
   ```

## Full Installation

1. **Download DayZ Server from Steam:**
   - Go to `Library` -> `Tools`.
   - Note that DayZ Server Experimental is a separate download and can be installed similarly.
   - By default, the files will be in `C:\Program Files (x86)\Steam\steamapps\common\DayZServer`.
   - Copy this directory to another location. Why? Because Steam will auto-update for the next release in the original location and overwrite any changes you have made. For simplicity, this documentation will use `C:\dayzserver\` and call it `<server_root>`.

2. **Set Server Configuration Parameters:**
   - Edit `<server_root>\serverDZ.cfg`.
   - Change the `hostname` variable to the name of your server. This is the name that shows up in the server browser. It can be a maximum of 63 characters long.
     ```cfg
     hostname="MyServerName";
     ```
   - Set a password if desired:
     ```cfg
     password="MyServerPassword";
     ```
   - Set `steamQueryPort` ONLY if needed due to a port conflict (usually not needed):
     ```cfg
     steamQueryPort=27016; // default
     ```

3. **Set Up RCON Access:**
   - For tools such as BEC, BattleMetrics, Dart, CF, etc., add the RCON port by editing or creating `<server_root>\battleye\BEServer_x64.cfg`.
     - Note: The filename may have extra characters appended if you’ve already run the server.
     - Any unused port can be used, but avoid game port +2, +3, +4. Put the following text in that file:
       ```cfg
       RConPort 2322
       ```

4. **Set Game Port on the Command Line:**
   - Use `-port=<game_port>`. 2302 is the default.
     ```batch
     -port=2302
     ```

5. **Open Ports:**
   - Add INBOUND rules to the Windows firewall to allow `gameport` and `steamqueryport` (UDP). They are at 2302 & 27016 by default unless you’ve changed them.
   - If you are hosting locally, you’ll most likely need to forward the same ports in your router to the host PC.

6. **Run the Server:**
   - Use this command line or a batch (`.BAT`) file:
     ```batch
     "C:\Windows\System32\cmd.exe" /C start "DayZSA" C:\dayzserver\DayZServer_x64.exe -config=C:\dayzserver\serverDZ.cfg -port=2302 -profiles=C:\dayzserver\profile -BEPath=C:\dayzserver\battleye -dologs -adminlog
     ```
   - Command line parameters documentation: [DayZ Server Configuration](https://community.bistudio.com/wiki/DayZ:Server_Configuration).

   **Note:** The `-mod`, `-profiles`, and `-config` command line parameters are wrapped in double quotes. These are required if any of the directory names have spaces or special characters.
```

Feel free to adjust any details or add additional instructions based on your needs!
