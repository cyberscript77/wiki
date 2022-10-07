# Troubleshooting

> This helps if you lost your way or something came up

# If you are stuck in tutorial
- Go to /Quest_mod/Json/datapack/default/event/ and **remove tutorial_help.json**
- Go to /quest_mod/data/ and **delete compiled_cache.lua**
- Reload mod
- Go to keystone, update mod and **reload cet after update**
- Go to keystone,update Main datapack if needed

**Note:** You should see the tutorial only if the save that you load doesn't have previous CyberScript data. Then it appears only one time.

# My mod is loaded but keystone doesn't show (aka REQUIREMENTS)

- Check if you have native setting mod : https://www.nexusmods.com/cyberpunk2077/mods/3518
- Also latest CET : https://www.nexusmods.com/cyberpunk2077/mods/107
- And finally : open shell command (Windows Key +R) , type **dotnet --info**, you should have at least.
- .NET Desktop Runtime 6.0.8 or higher https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-6.0.8-windows-x64-installer

**Note:** restart your computer after installing the above programs.

# Bugged quest

- Go into Mods menu , Under CyberScript Settings, Click on the reset CM quest, Clean the mess, Rebuild Datapack cache, Rebuild Datapack cache.
- Then back out the pause menu, then go back to the CyberScript Settings in Mods menu (So the UI shows that the datapacks got refreshed aka turned off)
- missions should now be Unbugged and can be selected again.

**IF SOLUTION FAILS.**

- Go to cyber_engine_tweaks/mods/quest_mod/data DELETE Compiled_datapack File .. Go to the SESSIONS folder, Delete all of them , You can keep latest on there since it's essentially your last save however you saved via manual or auto.