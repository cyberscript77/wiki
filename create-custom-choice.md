# Create custom choice

> In this page, you will be able to follow an small tutorials about making your own choice in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described choice.**

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
<br>We will create .... Choice!

# 💬 Create a Choice

**📂 Setup the folder**

First : in your mod folder, create a folder named "choice". It will contain every choice script of your mod. Logic !

In this folder, create a JSON text file, like for example : amazingChoice.json

Open it with your favorite text editor.

**💀 Write the interact skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about choice structure :

A choice is an list of choice. a choice have several things :
- A Desc
- A speaker
- a Tag
- several triggers (what will unlock the choice) you can found the list here
- triggers requirement (in which order triggers need to be fulfilled to unlock the choice)
- an options list : some object that will perform when you choose it.

Now let's make it in JSON :

```json
[
	{
        "Desc": "Time to make a choice, choomba !",
        "speaker": {
            "value": "Morpheus",
            "way": "speak"
        },
        "Tag": "my_amazing_choice",
        "trigger": {},
        "requirement": [],
        "options": [ ]
    }
]
```

This is the skeleton of our choice. For resume what you see below : The choice is have a text : "Time to make a choice, choomba !",

Cyberscript know it as "my_amazing_choice".

it doesn't have a trigger

it doesnt have a requirement

it have a empty options list.

Lets fill it with two choices :

```json
[
	{
        "Desc": "Time to make a choice, choomba !",
        "speaker": {
            "value": "Morpheus",
            "way": "speak"
        },
        "Tag": "my_amazing_choice",
        "trigger": {},
        "requirement": [],
        "options": [
			{
                "Description": "Take the blue pills",
"icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Make good dreams, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]]
            }, 
            {
                "Description": "Take the red pills",
                 "icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Welcome to the matrix, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]]
            }
        ]
    }
]
```

Here you have two options.

Lets describe them

**Option 1**

Description is "Take the blue pills" Trigger is auto (automatically unlocked) requirement require only auto trigger it have an list of action that contains one action (you can find the list [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/data/actiontemplate.json)):

Icon is : FlatheadIcon, you can find the list of icon  [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/data/ChoiceIcons.json)

- a subtitle that will show "Morpheus : Make good dreams, Neo !"

**Option 2**

Description is "Take the red pills" Trigger is auto (automatically unlocked) requirement require only auto trigger it have a list of action that contains one action :

- a subtitle that will show "Morpheus : Welcome to the matrix, Neo !"

# Optionnal Fields

## Icon 
```json
[
	{
        "Desc": "Time to make a choice, choomba !",
        "speaker": {
            "value": "Morpheus",
            "way": "speak"
        },
        "Tag": "my_amazing_choice",
        "trigger": {},
        "requirement": [],
        "options": [
			{
                "Description": "Take the blue pills",
"icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Make good dreams, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]]
            }, 
            {
                "Description": "Take the red pills",
                 "icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Welcome to the matrix, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]]
            }
        ]
    }
]
```
- icon (for options), you can find the list of icon  [here](https://raw.githubusercontent.com/cyberscript77/release/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/data/ChoiceIcons.json)


## Style 

```json
[
	{
        "Desc": "Time to make a choice, choomba !",
        "speaker": {
            "value": "Morpheus",
            "way": "speak"
        },
        "Tag": "my_amazing_choice",
        "trigger": {},
        "requirement": [],
        "options": [
			{
                "Description": "Take the blue pills",
"icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Make good dreams, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]],
				"style":{
					"color":{
						"red":255,
						"green":0,
						"blue":0
					
					}
				
				},
            }, 
            {
                "Description": "Take the red pills",
                 "icon":"FlatheadIcon",
                "action": [
					{
						"name": "subtitle",
						"title": "Welcome to the matrix, Neo !",
						"type": 1,
						"target": "player",
						"speaker": "Morpheus",
						"duration": 2,
						"helper": "This action will fire an random subtitle, it act live wait for second",
						"helperTitle": "Dialog : run random subtitle"
					}
                ],
                "trigger": {
                    "auto": {
                        "name": "auto"
                    }
                },
                "requirement": [["auto"]]
            }
        ]
    }
]
```


You can add style to your interact.
- color : color of the text when unselect or color of the background when select




# Make an interact that will call your dialog !

dialog are called through an action.

so we need make an interact to show it.

you can follow this tutorial to make an interact : How to make an custom Interact ?

There is a small example that will work :

```json
{
	"name": "Test My Amazing dialog",
	"tag": "myamazinginteractdialog",
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
        "name":"dialog",
        "dialog": "my_amazing_choice",
    }]
}
```

# Test your interact and your dialog !

Copy your whole mod folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/myAmazingmod

the structure of the folder should be

📂myAmazingmod

```structure
├── 📃 desc.json
├── 📃 init.lua
├── 📁 libs
├── 📁 scripts
	├── 📁 choice
	|    └── 📃 amazingChoice.json
	└── 📁 interact
		 └── 📃 amazingInteract.json
```

Select the mod "myAmazingmod" in cycle interact ([What are you talking about ?](cycle-throught-interact.md))

then hit the key for use your interact. Dialog should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
