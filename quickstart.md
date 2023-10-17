# Quick start

> This page covers the installation on windows, linux and steam deck.

<span style="color:#00FA9A; font-weight:bold;">⚠️ We support Vortex mod manager</span>.

## Requirements

- [Native settings mod](https://www.nexusmods.com/cyberpunk2077/mods/3518).
- [Cyber Engine tweaks (CET)](https://www.nexusmods.com/cyberpunk2077/mods/107).
- [Codeware](https://www.nexusmods.com/cyberpunk2077/mods/7780).
- [CyberScript Core Animation Archive](https://www.nexusmods.com/cyberpunk2077/mods/7691).
- [Redmod](https://www.youtube.com/watch?v=NVKVuzIW5WY&t=190s).

?> **Read their guide to install the requirements** and make sure you have the latest or updated version of these requirements.

## Download

To experience the mod, you have to download it first 🤩. Fortunately downloading CyberScript is common for all operating systems (i.e Windows, Linux, Steam Deck). But since, I have windows in my hand, I will demostrate using windows 🎀

There are two ways to download.

- Through Nexus platform
- Our Github repository

?> **Download from any one of the link**<br><br>▶️ Link to download from our Nexus page https://www.nexusmods.com/cyberpunk2077/mods/6475<br>▶️ Link to download from our github repository https://github.com/cyberscript77/release<br>🥺 Don't know how to download from github ? [Follow this guide](download-from-github.md)


After downloading our **CyberScript Core**, time to experience it 😋. Choose your operating system and follow the guide.

## Installation

?> Right now, CyberScript can be installed in three operating systems, **Windows 10 or 11**, **Linux or Steam Deck.** Follow the guides carefully to avoid rewriting some other files. <br><br>**Starting the Installation assuming, you have already downloaded the mod file.**

I'm using  : 

> How to install CyberScript on Windows 10, 11. 

- Open the [Downloaded ZIP from here](https://www.nexusmods.com/Core/Libs/Common/Widgets/DownloadPopUp?id=52734&game_id=3333)) using any software you like (ex. [7Zip](https://www.7-zip.org/), [WinRAR](https://www.win-rar.com/))
- It contains a folder called `bin`.
- Copy or Extract the `bin` folder to your Cyberpunk 2077 game installed folder.

# Linux and Steam Deck

In order to install our mod in Linux or Steam Deck, follow this [guide](installation-linux.md)


## Playing with CyberScript
You can get any mods that using cyberscript by looking in *requirements* -> *mods requiring this
file*
section on the Nexus webpage.
CyberScript alone will do nothing since it's a framework !

Mods powered by Cyberscript can only work in cyberscript framework.

When enabling any mods, whether it be in bunches or one at a time, ALWAYS GO TO CyberScript settings to `REFRESH MODS CACHE`.

# Enable a Cyberscript Powered Mod

1- Go to Pause Menu <br/>
2 - Go to "Mods"  <br/>
3 - Go to "Cyberscript Mods Manager" Tabs  <br/>
4 - Enable the mods you need/want  <br/>
5 - Go to "Cyberscript settings" Tabs and hit "REFRESH MODS CACHE" at the bottom.
6 - Close Pause Menu


Often, mods using cyberscript got interacts, [learn here how to use them](cycle-throught-interact.md)



?> If you have any problem in installation look into [Troubleshooting](troubleshooting.md) or post it on Discord.


## Redmod troubleshooting
If you get issue like AV don't show, no sound, no entity spawn or something like this, it's because
Vortex Redmod don't deploy cyberscript mods yet.

Go to (game root folder)/r6/cache/modded/mods.json and put all cyberscript based mod to
**"enabled":true**

Then

- go to your game root folder
- go to tools - > redmod -> bin 
- create a txt file named *start.bat*
- edit it with notepad
- copy this 
> redMod.exe deploy<br/> pause

- save the file and run it

⚠️ You may have to enable mods from *mods.json* and run *start.bat* everytime that you add a new redmod mod from vortex ⚠️