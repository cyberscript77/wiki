# Creating functions

> In this page, you will be able to follow a small tutorial about making your own function in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described function.**

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
<br>We will create .... Function !

# ⚙ Create a Function

**❓ Why using Function ?**

Using function will save you time. You want repeat an script part ? Call function and make reusable script.

**📂 Setup the folder**

First : in your mod folder, create a folder named "function". It will contain every function script of your mod. Logic !

In this folder, create a JSON text file, like for example : amazingFunction.json

Open it with your favorite text editor.

**💀 Write the function skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about function structure :

an function have several things :

- A name
- a tag
- a list of action

Now let's make it in JSON :

```json
{
    "name": "myamazingfunction",
    "tag": "myamazingfunction",
    "action": [ ]
}
```

This is the skeleton of our function. For resume what you see below : The choice is have name: "myamazingfunction",

Cyberscript know it as "myamazingfunction".

It have an action options list.

Lets fill it with one action :

```json
{
    "name": "myamazingfunction",
    "tag": "myamazingfunction",
    "action": [
		{
            "name":"notify",
            "value":"Hello world !"
        }
    ]
}
```

Here you have one action Notify that will display a game notification with text "Hello world !" That's all ! Easy, right ? fill the action list as you want.

functions are called through an action. do_function or do_random_function

so we need make an interact (or any other object that use actions) for use it.

you can follow this tutorial for make an interact : [How to make an custom Interact ?](create-custom-interact.md)

There is a small example that will work :

```json
{
	"name": "Test My Amazing function",
	"tag": "myamazinginteractfunction",
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
		"name": "do_function",
		"value": "myamazingfunction",
		"parallele": false
	},
	]
}
```

# Test your faction!

Copy your whole mod folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/myAmazingmod

the structure of the folder should be

📂myAmazingmod

```structure
├── 📃 desc.json
├── 📃 init.lua
├── 📁 libs
├── 📁 scripts
	├── 📁 function
	|    └── 📃 amazingFunction.json
	├── 📁 interact
	     └── 📃 myamazinginteractfunction.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript mod Manager and enable myAmazingmod

Select the mod "myAmazingmod " in cycle interact ([What are you talking about ?](cycle-throught-interact.md))!

then hit the key for use your interact. Function should execute !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
