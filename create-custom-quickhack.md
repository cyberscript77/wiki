# Create custom quickhack

> In this page, you will be able to follow a small tutorial about making your own quickhack in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to play the described quickhack.**

**To start, you need:**
- 📄 Text editor : VS code, Notepad (hard but possible) or Notepad ++ (my favorite). Along with Notepad++ you need a Json Plugin for it as well.
- ✍️ Knowing fundamentals of JSON (read it, it's easy 😀 ) [here](https://www.w3schools.com/js/js_json_intro.asp)
- 💯 Read the fundamental about Cyberscript: [Scripting Basics](scripting-basics.md)
- ✔ an JSON validator website (for be sure that your json is not malformatted, because it will not compile if) [JSONlint](https://jsonlint.com/)
- 🧠 a Brain, that work not that bad :)
- 🥇 Cyberpunk Game with Cyberscript installed and working
- ⏲ Patience, you will discover a new thing. It require patience and trial and error before it works.

**Ok now I will assume you have it all. let's start !**<hr>

# 📁 Introduction

We assume here that you already [create an datapack folder](create-an-datapack-folder.md)
<br>Now let's go deeper! We will create .... quickhack !

# ⏏ Create an quickhack

**📂 Setup the folder**

First : in your datapack folder, create an folder named "quickhack". It will contain every quickhack script of your datapack. Logic !<br>
In this folder, create a JSON text file, like for example : myquickhack.json

Open it with your text editor of choice. <br>

**💀 Write the quickhack skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.
Let's talk about quickhack structure :

An quickhack script has several things :
- A name
- A tag
- A display
- several triggers (what will unlock the interact)
- triggers requirement (in which order trigger need to be fulfilled to unlock the interact)
- an action list : some action you will perform when you hit the interact key

Now let's make it into a JSON :

```json
{
	"tag": "myquickhack",
	"icon": "UIIcon.quickhack_icebreaker",
	"title": "My Hack",
	"titlealternative": "",
	"description": "My amazing hack",
	"trigger": {
		"auto": {
			"name": "auto"
		}

	},
	"requirement": [
		["auto"]
	],
	"inactiveReason": "My inactive reasons",
	"unlocktrigger": {
		"auto": {
			"name": "auto"
		}

	},
	"unlockrequirement": [
		["auto"]
	],
	"actiontype": 5,
	"cost": 3,
	"uploadtime": 2,
	"duration": 10,
	"icelevelvisible": true,
	"iceLevel": 13,
	"quality": 1,
	"isinstant": false,
	"cooldown": 0,
	"networkbreached": true,
	"action": [{
		"name": "notify",
		"value": "Haxiing...."
	}]
}
```


# Test your quickhack !

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/


so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
└── 📁 quickhack
    └── 📃 myquickhack.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack. MAKE SURE to have Auto refresh on!

Then go to see Rogue, open your journal and look under the "Available " section. You will see your interact !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)