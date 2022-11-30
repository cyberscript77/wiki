# Create custom interact

> In this page, you will be able to follow a small tutorial about making your own interact in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to play the described interact.**

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
<br>Now let's go deeper! We will create .... Interact !

# ⏏ Create an Interact

**📂 Setup the folder**

First : in your datapack folder, create an folder named "interact". It will contain every interact script of your datapack. Logic !<br>
In this folder, create a JSON text file, like for example : amazingInteract.json

Open it with your text editor of choice. <br>

**💀 Write the interact skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.
Let's talk about interact structure :

An interact script has several things :
- A name
- A tag
- A display
- a icon, you can find the list of icon  [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/data/ChoiceIcons.json)
- several triggers (what will unlock the interact)
- triggers requirement (in which order trigger need to be fulfilled to unlock the interact)
- an action list : some action you will perform when you hit the interact key

Now let's make it into a JSON :

```json
{
	"name": "My Amazing Interact",
	"tag": "myamazinginteract",
	"display": "event_interact",
	"icon":"EngineeringIcon",
	"type": "interact",
	"sorttag": "none",
	"trigger": {
		
	},
	"requirement": [
		[ ]
	],
	"action": [ ]
}
```

This is the skeleton of our interact. For resume what you see bellow : The interact is named "My Amazing Interact",

Cyberscript know her as "myamazinginteract".

it display as "event_interact" , traditionnal interact way.

You can have several interact display type :

- event_interact , traditionnal way.
- place or place_main, will be available in Cyberscript custom place
- phone_service, like an contact phone in phone.

the type is "interact". You have two type :

- interact : traditionnal interact
- hint : hint interact, at the bottom right of the screen

if you choose "hint", you need add some field to your json :

- "hold" : true/false, need hold the interact for fire it.
- "key" : "QuickMelee", which key will fire the interact. it can be 'CameraAim', 'QuickMelee', 'DeviceAttack'

Now let's fill some triggers and requirement.

For this example, we want that the interact is always unlocked

So let's add a trigger "auto"

you can find all trigger definition [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/triggertemplate.json)

let's add it to our interact as "mytrigger" and add it in requirement too :

```json
{
	"name": "My Amazing Interact",
	"tag": "myamazinginteract",
	"display": "event_interact",
	"type": "interact",
	"sorttag": "none",
	"trigger": {
		"mytrigger":{
		"name": "auto"
	        }
	},
	"requirement": [
		[
		"mytrigger"
		]
	],
	"action": [ ]
}
```

All right, we have setup a condition for getting the interact!

Now let's talk about trigger action AKA what your script should to when player hit the interact key.

For this example, we want a game notification display "Hello world"

We will fill the list of action

We will fill it with action. You can find every possible action [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/actiontemplate.json)

lets make fill our json and describe it

```json
{
	"name": "My Amazing Interact",
	"tag": "myamazinginteract",
	"display": "event_interact",
	"type": "interact",
	"sorttag": "none",
	"trigger": {
		"mytrigger":{
		"name": "auto"
	    }
	},
	"requirement": [
		[
		"mytrigger"
		]
	],
	"action": [
	    {
           "name":"notify",
           "value":"Hello World !"
        }
	]
}
```

Here we use the action notify that will display an in-game notification and the value will be Hello World !<hr>

# Test your interact !

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/


so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
└── 📁 interact
    └── 📃 amazingInteract.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack. MAKE SURE to have Auto refresh on!

Then go to see Rogue, open your journal and look under the "Available " section. You will see your interact !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)