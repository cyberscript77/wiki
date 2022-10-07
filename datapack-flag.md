# Datapack Flag

- "amm" : check if the user have AMM Mod
- "amm_version:X.X.X" : check if the user have AMM Mod with version X.X.X or superior
- "amm_version_strict:X.X.X" : check if the user have AMM Mod with version X.X.X ONLY
- "cm_version:X.X.X" : check if the user have CyberScript version with version X.X.X or superior
- "cm_version_strict:X.X.X" : check if the user have CyberScript version with version X.X.X ONLY
- "datapack:my_datapack_tag" : check if the user have datapack by his tag
- "datapack_version:<span></span>my_datapack_tag:X.X.X" : check if the user have datapack by his tag and version X.X.X or superior
- "datapack_version_strict:<span></span>my_datapack_tag:X.X.X" : check if the user have datapack by his tag and version X.X.X ONLY
- "nsfw" : check if the Nudidty Censor Setting in game is enabled or not. If enabled, the condition is false, if disabled, the condition - is true.
- "compile" : force the compilation again for this datapack everytime that the user open pause menu. (Useful for debug or test an - datapack during dev, can affect game performance, disable it for publish it in stable)
- "beta":will bypass the "cm_version" or "cm_version_strict" if the user use an BETA version of CyberScript.