# Create an mods folder

> In this page, you will be able to follow small Tutorials about making your own mod in JSON and play it with Cyberscript.

**To start, you need:**
- 📄 Text editor : VS code, Notepad (hard but possible) or Notepad ++ (my favorite). Along with Notepad++ you need a Json Plugin for it as well.
- ✍️ Knowing fundamentals of JSON (read it, it's easy 😀 ) [here](https://www.w3schools.com/js/js_json_intro.asp)
- 💯 Read the fundamental about Cyberscript: [Scripting Basics](scripting-basics.md)
- ✔ an JSON validator website (for be sure that your json is not malformatted, because it will not compile if) [JSONlint](https://jsonlint.com/)
- 🧠 a Brain, that work not that bad :)
- 🥇 Cyberpunk Game with Cyberscript installed and working
- ⏲ Patience, you will discover a new thing. It require patience and trial and error before it works.
  
**Ok now I will assume you have it all. let's start !**<hr>

# 📁 Creating a mod folder

Cyberscript work with mod architecture. A mod is a folder that contains Organized scripts that are to be executed by CyberScript's Script Engine, via triggers.

It can be missions, dialogs, places and events...

It have also an file named desc.json (that the case for every mod) it contains the information for the mod about the mod.

So now :
- create an folder "bin". Inside this folder, create this path : "bin\x64\plugins\cyber_engine_tweaks\mods\"
- Create a folder named for example "myAmazingmod"
- In this folder at the root, create a file text named desc.json. OR just copy n' paste an existing one and change out it's values, as a starter.
the structure of the folder should be :


```structure
📁 bin
├── 📁 x64
     ├── 📁 plugins
          ├── 📁 cyber_engine_tweaks
              ├── 📁 mods
                   ├── 📁 myAmazingmod  
                       └── 📃 desc.json
```



  
Now we will fill this `desc.json`

Let's take a look

```json
{
  "name": "myAmazingmod",
  "desc": "Really, it blow you away !",
  "author": "donk7413",
  "file": "myAmazingmod.zip",
  "tag": "myAmazingmod",
  "version": "1.0.0",
  "flags":["cm_version:1.2.8", "compile", "beta"]
}
```

You can see many fields in it, let's describe it :

- name : name of your mod
- desc : description of your mod
- author : author of the mod
- file : name of the archive when it will be zipped, it should use the tag + ".zip"
- tag : the word identifier of the mod, the mod will recognize it by this field
- version : the version of the mod, should be formated X.X.X (Major.Medium.Minor)
- flags : the "requirements" and extra information about the mod. For this case, "cm_verson" means it should require at least cyberscript 1.2.8. List of possible flag [here](mod-flag.md)
- Compile is a flag that works with auto refresh. The way it works is if you were to change 1 thing in your mod while the game is open, Just simply pause and unpause for the change to be made.

All right, save it and close the file, we are done with the desc.json. Easy, right ?<br>
Now you can create your own content in !
