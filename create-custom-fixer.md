# Create custom fixer

> In this page, you will be able to follow an small tutorials about making your own fixer in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described fixer.**

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
<br>We will create .... Fixer !

# 👨🏻‍💻 Create a Fixer

**📂 Setup the folder**

First : in your datapack folder, create a folder named "dialog". It will contain every dialog script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingFixer.json

Open it with your favorite text editor.

**💀 Write the interact skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about fixer structure :

An Fixer have several things:
- An Name : The name of your fixer
- An Tag : the tag of your fixer. Cyberscript will know it by this way.
- a Faction : an custom faction tag. You can leave it to "" if you don't need it
- A LOC_X : X coordinate in the world
- A LOC_Y : Y coordinate in the world
- A LOC_Z : Z coordinate in the world
- a range : an spawn range when you are at Fixer's location for make it spawn/despawn
- A exist field (true/false) : Does this Fixer Exist in the game's story missions and has a set location ?(Wakako, Rita, Regina, Rogue  etc.) ?
- A npcexist field (true/false) : Does this Fixer Exist already as a Side NPC and No set location? (River, Meredith, Judy, Etc.)
- a NPCId field : TweakId of the character, you can found an list here
- several triggers (what will unlock the fixer)
- triggers requirement (in which order trigger need to be fullfilled to unlock the fixer)
- an spawn action list : some action you will perform when fixer spawn
- an despawn action list : some action you will perform when fixer despawn

Now let's make it in JSON :

```json
{
	"Name":"My Amazing Fixer",
	"LOC_X":-1530,
	"LOC_Y":986,
	"LOC_Z":86,
	"range":5,
	"Faction":"",
	"Tag": "myamazingfixer",
	"exist":false,
	"npcexist":false,
	"NPCId":"Character.Afterlife_Barman",
	"trigger": { },
	"requirement":
        [
          [ ]
        ],
	"spawn_action": [ ],
	"despawn_action": [ ]
}
```

This is the skeleton of our fixer. For resume what you see bellow : The fixer is named "My Amazing Fixer",

Cyberscript know it as "myamazingfixer".

it will spawn when player in in range of 5 at the location "x":-1530,"y":986,"z":86.

it is not related to any custom faction.

it doesn't exist in the world as fixer

it doesn't exist in the world as side npc

Model will be Character.Afterlife_Barman

Now let's fill some triggers and requirement.

```json
{
	"Name":"My Amazing Fixer",
	"LOC_X":-1530,
	"LOC_Y":986,
	"LOC_Z":86,
	"range":5,
	"Faction":"",
	"Tag": "myamazingfixer",
	"exist":false,
	"npcexist":false,
	"NPCId":"Character.Afterlife_Barman",
	"trigger":
        {
		"always_enable":{
			"name":"auto"
		}
	},
	"requirement":
        [
          [
             "always_enable"
          ]
        ],
	"spawn_action": [ ],
	"despawn_action": [ ]
}
```

For this example, we want that the fixer is always unlocked

So let's add an trigger definition named "always_enable" who use the trigger "auto"

you can found all trigger definition [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/triggertemplate.json)

All right, we have setup an condition for getting the event!

Now let's talk about spawn action AKA what your script should to when it's spawn.

For this example, we want that he said "Hi V ! want take an job ?"

We will fill the list of spawn_action

We will fill it with action.

You can find every possible action [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/actiontemplate.json)

lets make fill our json and describe it

```json
{
	"Name":"My Amazing Fixer",
	"LOC_X":-1530,
	"LOC_Y":986,
	"LOC_Z":86,
	"range":5,
	"Faction":"",
	"Tag": "myamazingfixer",
	"exist":false,
	"npcexist":false,
	"NPCId":"Character.Afterlife_Barman",
	"trigger":
        {
		"always_enable":{
			"name":"auto"
		}
	},
	"requirement":
        [
          [
             "always_enable"
          ]
        ],
	"spawn_action":
	[	
		{
			"name": "subtitle",
			"title": "Hi V ! want take an job ?",
			"type": 1,
			"target": "player",
			"speaker": "My Amazing Fixer",
			"duration": 3,
			"helper": "This action will fire an random subtitle, it act live wait for second",
			"helperTitle": "Dialog : run random subtitle"
		}
	],
	"despawn_action": [ ]
}
```

we use "subtitle".

- title : it will display an subtitle with the text described in "title" field.
- Type 1 means Regular (you can check every possible type [here](https://nativedb.red4ext.com/scnDialogLineType)
- target : player means the entity who the subtitle will be affected is the player
- speaker is the speaker. It's an text. In our case we write Rogue. So it will display "My Amazing Fixer : Hi V ! want take an job ?". You can put banana or anything. It's just an text that indicate who speak.
- persistent : false means that the subtitle doesn't stay forever displayed.
- duration : means in second how much time it will be displayed if not persistent.in our case 3 second.

Now let's talk about despawn action AKA what your script should to when it's despawn.

For this example, we want that he said "See ya V !"

We will fill the list of despawn_action

We will fill it with action.

You can find every possible action [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/actiontemplate.json)

lets make fill our json and describe it

```json
{
	"Name":"My Amazing Fixer",
	"LOC_X":-1530,
	"LOC_Y":986,
	"LOC_Z":86,
	"range":5,
	"Faction":"",
	"Tag": "myamazingfixer",
	"exist":false,
	"npcexist":false,
	"NPCId":"Character.Afterlife_Barman",
	"trigger":
        {
		"always_enable":{
			"name":"auto"
		}
	},
	"requirement":
        [
          [
             "always_enable"
          ]
        ],
	"spawn_action":
	[	
		{
			"name": "subtitle",
			"title": "Hi V ! want take an job ?",
			"type": 1,
			"target": "player",
			"speaker": "My Amazing Fixer",
			"duration": 3,
			"helper": "This action will fire an random subtitle, it act live wait for second",
			"helperTitle": "Dialog : run random subtitle"
		}
	],
	"despawn_action":
    [
        {
			"name": "subtitle",
			"title": "See ya V !",
			"type": 1,
			"target": "player",
			"speaker": "My Amazing Fixer",
			"duration": 3,
			"helper": "This action will fire an random subtitle, it act live wait for second",
			"helperTitle": "Dialog : run random subtitle"
		}
    ]
}
```

we use "subtitle".

- tle : it will display an subtitle with the text described in "title" field.
- pe 1 means Regular (you can check every possible type here
- rget : player means the entity who the subtitle will be affected is the player
- eaker is the speaker. It's an text. In our case we write Rogue. So it will display "My Amazing Fixer : See ya V !".You can put banana anything. It's just an text that indicate who speak.
- rsistent : false means that the subtitle doesn't stay forever displayed.
- ration : means in second how much time it will be displayed if not persistent.in our case 3 second.

# Test your fixer!

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
├── 📁 fixer
     └── 📃 amazingFixer.json
```

Then load your game. Load an save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack

Go to location "x": -1530, "y": 986, "z": 23 and in radius of 20 and see it happens !

You will also see it on worldmap under fixer icon !

You can now use it as fixer for quest tutorial [Quest tutorial](create-custom-quest.md)

replace fixer_rogue tag by myamazingfixer tag !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)