
# Create custom interface

> In this page, you will be able to follow an small tutorials about making your own interface in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described interface (UI).**

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
<br>We will create .... interface !

# 📱 Create a Interface

**📂 Setup the folder**

First : in your datapack folder, create a folder named "interfaces". It will contain every interfaces script of your datapack. Logic !

In this folder, create a JSON text file, like for example : myUI.json

Open it with your favorite text editor.

**💀 Write the interfaces skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about interface structure :

A dialog is an list of choice. a choice have several things :
- A Desc
- A speaker
- a Tag
- several triggers (what will unlock the choice) you can found the list here
- triggers requirement (in which order triggers need to be fulfilled to unlock the choice)
- an options list : some object that will perform when you choose it.

Now let's make it in JSON :

```json
{
	"title": "myUI",
	"tag": "myUI",
	"onload_action": [

  ...list of actions that will be performed when UI is loaded




	],
	"controls": 
  [
  ...list of the differents elements inside the UI
  ]
}
```

This is the skeleton of our interface. For resume what you see below : The interface is named "myUI",

Cyberscript know it as "myUI".

it have a empty on_load actions list.

it have a empty controls list.

Lets fill control list with 2 elements :

```json
{
	"title": "myUI",
	"tag": "myUI",
	"onload_action": [

 


	],
	"controls": 
	[
	  	{
			"type": "area",
			"tag": "rootarea",
			"rotation": 0,
			"anchor": 15,
			"fittocontent": true,

			"trigger": {
				"auto": {
					"name": "auto"
				}
			},
			"margin": {
				"left": 0,
				"top": 0
			},
			"size": {
				"width": 1000,
				"height": 1000
			},
			"scale": {
				"width": 1,
				"height": 1
			},
			"requirement": [
				[
					"auto"
				]
			]
		},



		{
			"type": "area",
			"tag": "container",
			"parent": "rootarea",
			"rotation": 0,
			"anchor": 15,
			"opacity": 1,
			"visible": true,
			"fittocontent": false,
			
			"trigger": {
				"auto": {
					"name": "auto"
				}
			},
			"margin": {
				"left": 0,
				"top": 0
			},
			"size": {
				"width": 1000,
				"height": 1000
			},
			"scale": {
				"width": 1,
				"height": 1
			},
			"requirement": [
				[
					"auto"
				]
			]
		},
  ]
}
```



Before getting into it, let's talk a little about UI process.

Your UI is an stack of layer that you put one over one.

Your base will be the lowest layer then you stack new element on it.

Cyberscript let you use interface in 3 ways possible for now : 

- Inside an popup windows like shard, the base will be the popup element hud, you don't need to take care of it.
- As HUD element, you will be able to stack on an particular hud element. It can be the whole HUD "frame", that is invisible or hook to an hud element like mini-map.
- As custom WebPage, the base will be the web browser page layout, who is invisible.

Why I told you this ? because depending the way you choose, you will apply your interface to different "bases".

For schema it : 

```



						
					   Text
					    |
Text				Image	   Area	
 |				  |         |
Button				Rectangle___		Text
 |				  |			  |
Background			Background		Circle
 |    				  |   			  |
Area				Area			Area
 |				  |             	  |          ....
___________________________________________________________________________________________________________________________________________________________
								 |
							    Your UI Base
								 |
							Hooked Game Base
						 (popup, exiiting hud element, webpage browser)
```



Now, back to work.


Here you have written two elements. They look like very similar but it's important to have theses one. It will be the personnal base of your UI.

let's look at the first one :


```

{
			"type": "area",
			"tag": "rootarea",
			"rotation": 0,
			"anchor": 15,
			"fittocontent": true,

			"trigger": {
				"auto": {
					"name": "auto"
				}
			},
			"margin": {
				"left": 0,
				"top": 0
			},
			"size": {
				"width": 1000,
				"height": 1000
			},
			"scale": {
				"width": 1,
				"height": 1
			},
			"requirement": [
				[
					"auto"
				]
			]
		},


```


- "type":  There are several type for element, we will describe them later. We choose area, means its an area, simple.
- "tag": the identity of this element in Cyberscript
- "rotation": You can rotate this element to an angle (like 180° or 360°) ([Do your math](https://en.wikipedia.org/wiki/Angle))
- "anchor": 15,
- "fittocontent": true,
- "trigger": 
- "auto": 
- "margin":
- "size": 
- "scale":
- "requirement":





Lets describe them

**Option 1**

Description is "Take the blue pills" Trigger is auto (automatically unlocked) requirement require only auto trigger it have an list of action that contains one action (you can find the list [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/actiontemplate.json)):

- a subtitle that will show "Morpheus : Make good dreams, Neo !"

**Option 2**

Description is "Take the red pills" Trigger is auto (automatically unlocked) requirement require only auto trigger it have a list of action that contains one action :

- a subtitle that will show "Morpheus : Welcome to the matrix, Neo !"

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

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
├── 📁 dialog
|    └── 📃 amazingChoice.json
└── 📁 interact
     └── 📃 amazingInteract.json
```

Select the datapack "myAmazingDatapack" in cycle interact ([What are you talking about ?](cet-key-binding.md))

then hit the key for use your interact. Dialog should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
