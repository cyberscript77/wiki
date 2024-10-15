Custom NPC (ent file) with specific animation

# Preface

<span style="font-weight:bold;">A big big thanks to <span style="color:rgb(211, 61, 61)">Vitium,</span> <span style="color:rgb(115, 92, 255)">MaximiliumM</span> and the <span style="color:rgb(185, 94, 4)">AMM community</span> for help me to make it !</span>

👩Check [AMM mod](https://www.nexusmods.com/cyberpunk2077/mods/790) !**

📡Check their [discord](https://discord.com/invite/amm) !

# Starting

In this page, you will be able to follow a small tutorial about making your your custom NPC (ent file) with specific animation and use it with CyberScript.

For now this is not RedMod, when i will know how to use it with RedMod, I will update this page.

**It will be a long, but fully complete tutorial. At the end you will be able to use the described Subject of this tutorial.**

**To start, you need:**

- 💯 Read the fundamental about Cyberscript: [Scripting](scripting-basics.md)
- 🐺 [WolvenKit](https://github.com/WolvenKit/WolvenKit-nightly-releases/releases) 
- 🧠 a Brain, that work not that bad :)
- 🥇 Cyberpunk Game with Cyberscript installed and working
- ⏲ Patience, you will discover a new thing. It requires trial and error before it works.

Ok now I will assume you have it all. let's start !

# 📁 Introduction

We assume here that you already [create an mod folder](create-an-mod-folder.md)

Now let's go deeper !

<br>We will create .... an NPC with special Pose !

# ⚙ Create a NPC

**🐺Create an Wkit project**

- Create an project with wkit, follow the instruction ! In this exmaple we will name it myamazingwork.
- ‼‼‼ GO TO EDIT > PROJECT SETTING AND UNCHECK "IS REDMOD?"

**📂 Setup the folder**

First : in your mod folder, create a folder named "archive". It will contain every .archive file of your mod. Logic !

**👩Found the NPC you want customize !**

Let's take Judy, because it's our beloved one !

- In Wkit, go to asset browser, go to base\quest\secondary_character\judy.ent and double click on it, it will import in in your project.
- Go to Project Browser, right click on judy.ent and click on "Open in File Explorer"
- It will open you an windows explorer, where you can see your judy.ent
- Because we dont't want override the game judy, let's rename our file judy_sit.ent
- Now we need to make an custom path to our judy. 

Actually, you have : 

```
📁 archive
└── 📁 base
    └── 📁 quest
        └── 📁secondary_character
            └── 📄judy.ent
```

Manage yourself to have this (remove other useless folder under archive/base):

```json
📁 archive
└── 📁 base
    └── 📁 myamazingwork
        └── 📁ent
            └── 📄judy_sit.ent
```

This will be the new custom path of your ENT file. So with CyberScript, you can call it by "base\myamazingwork\ent\judy_sit.ent"

Ok we have place our Judy, let's move !

**👋 Choose an animation**

- In Wkit, go to asset browser, and in the search bar, write "average_female" and use filter on "Kind" for take only .anims file.
- You will see an lot of possible animation. Let's explain the name

Usually name of animations are written like this

npctype _ gender _ size _  action _ environnement _ position _ angle _ bodypart _ bodyenvrionnement _ number

For example

generic_female_average__sit_couch_lean180_2h_guitar__no_pick_ponpon__01

This means, animation of an generic average female who are sit on an couch, leaning at 180 degree, with 2 hands on guitar playing ponpon shit.

Some abbreviations:

```
rh = right hand 
lh = left hand
1h = one hand
2h = 2 hands
rf = right foot
lf = left foot
1f = one foot
2f = 2 foot
rl = right leg
ll = left leg
1l = one leg
2l = 2 leg
```

also the degree:

```
0 = forward
180 = backward
90 = right
270 = left
```

so lean180 = leaning backward

Understood ? Now let's choose 

generic_female_average__sit_couch_lean180_2h_guitar__no_pick_ponpon__01

because we love to see Judy playing guitar !

**🔗 Bound the animation to the entity**

Double click on it and it will be added to your project !

So you should have 

```json
📁 archive
└── 📁 base
    ├── 📁 myamazingwork
    │   └── 📁ent
    │       └── 📄judy_sit.ent
    └── 📁 animations
        └── 📁npc
            └── 📁generic_characters
                └── 📁female_average
                    └── 📁interactive_scene
                        └── 📄generic_female_average__sit_couch_lean180_2h_guitar__no_pick_ponpon__01.anims
```

Manage yourselft to have (remove other useless folder under archive/base):

```
📁 archive
└── 📁 base
    └── 📁 myamazingwork
        ├── 📁ent
        │   └── 📄judy_sit.ent
        └── 📁anims
            └── 📄sit_guitar.anims
```

So now we have our animation and our npc, let's combine them !

First double-click on sit_guitar.anims

Wkit will open the file property

Go to

```json
🔽animAnimSet
└── 🔽animations
    └── 🔽0
        └── 🔽animation
            └── 🔽name
```

Then replace

sit_couch_lean180_2h_guitar__no_pick_ponpon__01__play__02

by

idle_stand

Save your file and close the properties.

Now double-click on judy_sit.ent

Wkit will open the file property

Go to

```
🔽entEntityTemplate
└── 🔽components
    └── 🔽1 - Character Entity Animation Setup
        └── 🔽animations
            └── 🔽gameplay
                └── 🔽0
                    └── 🔽animSet
                        └── DepotPath
```

Then replace the current value by

base\myamazingwork\anims\sit_guitar.anims

**📦 Pack & Install !**

Go on the top of Wkit and click on Pack & Install

It should pack your project into an .archive file and copy it to  (GOG or steam game folder)/Cyberpunk 2077/archive/pc/mods/myamazingwork.archive

**We are done !**

# ⏯ Test your stuff !

We need make an interact (or any other object that use actions) for use it.

you can follow this tutorial for make an interact : [How to make an custom Interact ?](create-custom-interact.md)

There is a small example that will work :

```json
{
	"name": "Test My Amazing Judy",
	"tag": "myamazinginteractfunction",
	"display": "event_interact",
	"type": "interact",
	"sorttag": "none",
	"trigger": {
		"mytrigger":
		{
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
		"name": "spawn_npc",
		"tag": "judy",
		"spawnlevel": 42,
		"use_police_prevention_system": false,
		"group": "",
		"appearance": "none",
		"create_group_if_not_exist": false,
		"source": "npc",
		"useEntpath": true,
		"source_tag": "base\\myamazingwork\\ent\\judy_sit.ent",
		"source_list": [],
		"source_use_vip": false,
		"source_use_rival": false,
		"position": "relative_to_entity",
		"position_tag": "player",
		"position_way": "normal",
		"position_poi_district": "",
		"position_poi_subdistrict": "",
		"position_poi_is_for_car": false,
		"position_poi_from_position": false,
		"position_poi_use_location_tag": false,
		"position_poi_range": 0,
		"position_poi_type": 0,
		"position_distance": 5,
		"x": 0,
		"y": 0,
		"z": 0,
		"amount": 1
	},
	]
}
```


<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
