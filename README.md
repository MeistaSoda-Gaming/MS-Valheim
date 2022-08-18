# MS-Valheim
This repository serves the purpose of sharing the world files of Valheim with each other, so that we can play without having to rely on someone hosting the server.
Follow the steps below to make sure, that everything works out.

If you have any questions, contact ***MeistaSoda#5695*** or head to his [server](https://discord.gg/gGdvjUm3QJ) on Discord.


## SERVER FILES SHARING

### Step 1 - BACKUP
Make sure to create a backup of the world file before overwriting the file in your folder.
It is no problem to create a folder within the world saves or just outside that folder, to save a backup of all world files.

You should be able to find the server files in `C:\Users\[YOUR USER]\AppData\LocalLow\IronGate\Valheim\worlds_local`
*Hint: open the __AppData__ folder with __%appdata%__ in the command prompt aka cmd.*

### Step 2 - COPY FILES
Copy all files from the folder that is named after the world you want to play in. Simply paste them in the **worlds_local** folder.

### Step 3 - PLAY & ENJOY
You should be able to find the local world in your game now. Make sure that it remains a local save file ingame as well, to avoid issues.
Make sure you inform your fellow Vikings whenever you start playing from those files and when you are done, so that you don't end up playing at the same time without sharing the progress. In that case you would have to sacrifice one of the two progresses in order to save the file.

### Step 4 - SAVE PROGRESS
After playing on the world, you should shut down the game and head to the folder that holds the saved world files. Copy them into the repository and commit the changes to github.


## DEDICATED SERVER
Besides using the inbuilt hosting feature, which allows simple access and coop-gameplay, there is also another option of hosting a server, without having to be ingame and have your character online.
This is a simple tutorial on how to set up a [dedicated server](https://www.pcgamer.com/valheim-multiplayer-dedicated-server/).

### Step 1 - Valheim Dedicated Server Tool
![Steam - Valheim Dedicated Server Tool](https://cdn.mos.cms.futurecdn.net/tdzUVjWHK8xv7aZQ5enKFR-1200-80.jpg)

Open up **Steam** and toggle the ***Tools*** option in the steam library search and look for Valheim. You should be able to find `Valheim Dedicated Server` - install it.
Once the installation is complete, head to its installing folder *(f.e. `C:\Program Files (x86)\Steam\steamapps\common\Valheim Dedicated Server`)* and look for `start_headless.server`.
Make a backup-copy of it *(can be in the same folder)*, rename it and open it.

> When the game updates it will wipe the `start_headless.server` file clean, so make sure you have a backup of that file.

This is what you should be able to see, when opening the file:
```
@echo off
set SteamAppId=892970

echo "Starting server PRESS CTRL-C to exit"

REM Tip: Make a local copy of this script to avoid it being overwritten by steam.
REM NOTE: Minimum password length is 5 characters & Password cant be in the server name.
REM NOTE: You need to make sure the ports 2456-2458 is being forwarded to your server through your local router & firewall.
valheim_server -nographics -batchmode -name "My server" -port 2456 -world "Dedicated" -password "secret"
```

Edit the last line to your custom needs:
* -name "My server" --> Name the server by replacing __My server__
* -world "Dedicated" --> Choose the world name of your created world
* -password "secret" --> Change the password for people to join. IT HAS to BE DIFFERENT to the server name
* -public 1 --> Add this to the last line to make the server publically (1) or private(0) visible in the community server list (ingame).

Here is the example of the ***Tutoria Server***
```
@echo off
set SteamAppId=892970

echo "Starting server PRESS CTRL-C to exit"

REM Tip: Make a local copy of this script to avoid it being overwritten by steam.
REM NOTE: Minimum password length is 5 characters & Password cant be in the server name.
REM NOTE: You need to make sure the ports 2456-2458 is being forwarded to your server through your local router & firewall.
valheim_server -nographics -batchmode -name "Masters of Soda" -port 2456 -world "Tutoria" -password "heavysoda" -public 1
```

Save your progress and it and close the editor.

### Step 2 - Port Forwarding
In order for the dedicated server to work, you have open the ports. For that, go to your ***ROUTER SOFTWARE*** and open the **ports 2456-2458 TCP/UDP** The Host Port should be 2456.

If there's a firewall on the server PC, you'll have to open those ports on the firewall as well.
1. Open the **Windows Defender Firewall with Advanced Security**
2. Head to the `Inbound Rules`
3. Create a `New Rule...`
4. Choose ***Port***
5. Set the *Specific local ports:* as *2456-2458* for both ***TCP*** and ***UDP*** *(requires you to create a new rule twice)*
6. ***Allow the connection***
7. Tick all options
8. Name it and press the **Finish**-Button
9. Repeat steps 2-8 with the `Outbound Rules`

### Step 3 - Starting the Dedicated Server
Double click on the batch file that you renamed from "start_headless.server". The server should now start.

If the server is set to `-public 1`, the server should be visible in the *Community Server* list (sometimes takes between 10-15 Minutes to update the list).
If the server is set to `-public 0`, your fellow vikings will have to join through the *Steam Server Browser* `Steam --> View --> Servers` on the Steam Client in the Favourites tab by pressing "Add A Server".
In both cases it is also possible to join through the host IP. The IP address for your server is your server PC's external IP with the affix `:2457` on the end for the correct port.

*Example:* 192.168.1.4:2457

### Step 4 - HAVE FUN