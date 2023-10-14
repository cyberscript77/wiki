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

# Prior to Cyberscript Core 2.0, please download animation archive as well (available on Nexus too,
under optional files). Extract it in Cyberpunk game folder(like every Redmod archive mods)


After downloading our **CyberScript Core**, time to experience it 😋. Choose your operating system and follow the guide.

I'm using 
- [Windows 10, 11](installation.md)
- [Linux Os or Steam Deck](installation-linux.md)

## Playing with CyberScript
You can get any mods that using cyberscript by looking in *requirements* -> *mods requiring this
file*
section on the Nexus webpage



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