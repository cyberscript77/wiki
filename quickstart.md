# Quick start

> This page covers the installation on windows, linux and steam deck.

<span style="color:#00FA9A; font-weight:bold;">⚠️ We support Vortex mod manager</span>.

## 0 - Requirements

- [Native settings mod](https://www.nexusmods.com/cyberpunk2077/mods/3518).
- [Cyber Engine tweaks (CET)](https://www.nexusmods.com/cyberpunk2077/mods/107).
- [Codeware](https://www.nexusmods.com/cyberpunk2077/mods/7780).
- [CyberScript Core Animation Archive](https://www.nexusmods.com/cyberpunk2077/mods/7691).
- [Redmod](https://www.youtube.com/watch?v=NVKVuzIW5WY&t=190s).

?> **Read their guide to install the requirements** and make sure you have the latest or updated version of these requirements.

## 1 - Download

To experience the mod, you have to download it first 🤩. Fortunately downloading CyberScript is common for all operating systems (i.e Windows, Linux, Steam Deck). But since, I have windows in my hand, I will demostrate using windows 🎀

There are two ways to download.

- Through Nexus platform
- Our Github repository

?> **Download from any one of the link**<br><br>▶️ Link to download from our Nexus page https://www.nexusmods.com/cyberpunk2077/mods/6475<br>▶️ Link to download from our github repository https://github.com/cyberscript77/release<br>🥺 Don't know how to download from github ? [Follow this guide](download-from-github.md)


After downloading our **CyberScript Core**, time to experience it 😋. Choose your operating system and follow the guide.

## 2 - Installation

?> Right now, CyberScript can be installed in three operating systems, **Windows 10 or 11**, **Linux or Steam Deck.** Follow the guides carefully to avoid rewriting some other files. <br><br>**Starting the Installation assuming, you have already downloaded the mod file.**

I'm using  : 

> How to install CyberScript on Windows 10, 11. 

- Open the [Downloaded ZIP from here](https://www.nexusmods.com/Core/Libs/Common/Widgets/DownloadPopUp?id=52734&game_id=3333)) using any software you like (ex. [7Zip](https://www.7-zip.org/), [WinRAR](https://www.win-rar.com/))
- It contains a folder called `bin`.
- Copy or Extract the `bin` folder to your Cyberpunk 2077 game installed folder.

### Linux and Steam Deck

In order to install our mod in Linux or Steam Deck, follow this [guide](installation-linux.md)


## 3 - Playing with CyberScript
You can get any mods that using cyberscript by looking in *requirements* -> *mods requiring this
file*
section on the Nexus webpage.
CyberScript alone will do nothing since it's a framework !

Mods powered by Cyberscript can only work in cyberscript framework.

## 4 - Enable a Cyberscript Powered Mod

1- Go to Pause Menu <br/>
2 - Go to "Mods"  <br/>
3 - Go to "Cyberscript Mods Manager" Tabs  <br/>
4 - Enable the mods you need/want  <br/>
6 - Close Pause Menu


## 5 -Cycle throught Interact

Since we can't display so much interact in same time, you need to select which one you want use from the mod that contains it.

Depending on if you play with a controller or keyboard, you need to keybind some key in order to switch between using keyboard or controller.

First one, Cycle Custom Intereact is very important, to bind it, open Mods setting and go to Cyberscript binding:

![alt 1](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/pause.png)

![alt 1](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/keybindtab.png)

![alt 1](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/keybind.png)

Hotkeys Amount means how many hotkeys you need to hit for trigger the menu (aka combo)

Hold the key means that the key need to be holded

This key will allow you to go through current selected Mods's interacts if the Mods has any within it's folder.

![alt 2](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/2.jpg)

Use the interact "Select active Interactions Group" to open the menu and select the current active Mods

![alt 3](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/3.jpg)

then use Cycle Custom Interact key to choose the interact you want to use. 

![alt 4](./assets/images/cet-key-binding/../gettings-started/cet-key-binding/4.jpg)

?> If you have any problem in installation look into [Troubleshooting](troubleshooting.md) or post it on Discord.


## 6 - Redmod troubleshooting
If you get issue like AV don't show, no sound, no entity spawn or something like this, it's because
Vortex Redmod don't deploy cyberscript mods yet.



This issue is independant of cyberscript, usually, it's vortex deployment issue, for summarize it try to convert mods and filter the deployement , but here you can get a guide to resolve it :

### - Go to Vortex > Settings > V2077 Settings > Uncheck "Automatically convert old-style 'archive' mods to Redmods on install" and re-install your mods

- Try to remove
(game root folder)/r6/cache/modded folder


- Relaunch game through RedLauncher with mod enabled (small gear near Play button)


