# Create custom event

> In this page, you will be able to follow an small tutorials about making your own event in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described event.**

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

We assume here that you already [create an mod folder](create-an-mod-folder.md)
<br>Now let's go deeper! We will create .... Event !

# 🌍 Create a World Event

**📂 Setup the folder**

First : in your mod folder, create an folder named "event". It will contain every interact script of your mod. Logic !

In this folder, create a JSON text file, like for example : amazingEvent.json<br>

Open it with your favorite text editor.

**💀 Write the Event skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about event structure :

An event have several things :
- An name
- An tag
- a way

> There is several ways:
> - init : will fire the event if triggers and requirement are fullfilled at the initial load of a save file.
> - world : the event will be fire if triggers and requirement are fullfilled. Traditional way. (NOTE: World way is Constant as long as the trigger is fulfilled every second)
> - ambush = the event will be fire when ambush interval timer is triggered, players can setup the timer in mod setting. AKA custom Frequency event

- several triggers (what will unlock the interact)
- triggers requirement (in which order trigger need to be fullfilled to unlock the interact)
- an action list : some action you will perform when you hit the interact

Now let's make it in JSON :

```json
    {
		"name": "My Amazing Event",
		"tag": "myamazingevent",
		"way": "world",
		"trigger": {

		},
		"requirement": [
			[ ]
		],
		"action": [ ]
	}
```

This is the skeleton of our event. For resume what you see below : The event is named "My Amazing Event",

Cyberscript know it as "myamazingevent".

the type is "world".

Now let's fill some triggers and requirement.

```json
{
	"name": "My Amazing Event",
	"tag": "myamazingevent",
	"way": "world",
	"trigger": {
		"playerposition": {
	            "name": "entity_at_position",
	            "x": -1530,
	            "y": 986,
                "z": 23,
		        "range": 20,
		        "tag": "player"
           	}
		},
		"requirement": [
			[
				"playerposition"
			]
		],
		"action": [ ]
	}
```

For this example, we want that the event is unlocked when V is at location "x": -1530, "y": 986, "z": 23 and in radius of 20

So let's add a trigger definition named "playerposition" who uses the trigger "entity_at_position"

you can find all trigger definition [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/data/triggertemplate.json)

All right, we have setup a condition for getting the event!

Now let's talk about trigger action AKA what your script should do when it's unlocked.

For this example, we want a game notification display "Hey ! Something happens !"

We will fill the list of action

We will fill it with action. You can find every possible action [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/data/actiontemplate.json)

Lets fill our json and describe it

```json
{
		"name": "My Amazing Event",
		"tag": "myamazingevent",
		"way": "world",
		"trigger": {
			"playerposition": {
		             "name": "entity_at_position",
		             "x": -1530,
			         "y": 986,
         	         "z": 23,
		             "range": 20,
		             "tag": "player"
                }
		},
		"requirement": [
			[
				
				"playerposition"
			]
		],
		"action": [
		{
			"name":"notify",
			"value":"Hey ! Something happens !"
		}
		]
	}
```

Here we use the action notify that will display an in game notification and the value will be Hey ! Something happens !

# Test your event !

Copy your whole mod folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack/myAmazingmod

the structure of the folder should be

📂myAmazingmod

```structure
├── 📃 desc.json
└── 📁 event
    └── 📃 amazingEvent.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript mod Manager and enable myAmazingmod.

Go to location "x": -1530, "y": 986, "z": 23 and in radius of 20 and see it happens !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)