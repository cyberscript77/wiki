# Create custom shard

> In this page, you will be able to follow an small tutorials about making your own shard in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described shard.**

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
<br>We will create .... Shard!

# 💬 Create a shard

**📂 Setup the folder**

First : in your datapack folder, create a folder named "shard". It will contain every shard script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingshard.json

Open it with your favorite text editor.

**💀 Write the shard skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about shard structure :

A shard is a text. :
- A tag : Cyberscript will know it by this.
- A title : the title of the shard in the list
- A description : the content of the shard
- Crypted :  determine if the shard is scrypted or not ? (WIP)
- New : determine if the shard will be tagged as new or not ?
- locked : determine if the shard will be showed in lsit or not  ?

Now let's make it in JSON :

```json

	{
		"tag": "myAmazingShard",
		"title": "My amazing Shard",
		"description": "Cyberscript is amazing \n How I lived before know it ?",
		"crypted": false,
		"new": true,
		"locked": false
	 
	}

```

Note that i use "\n", it means break line !



# Make an interact that will call your phone dialog in an sms popup !

Shard are called through an action or directly in shard journal menu if unlocked , under CyberScript Section.


## CyberScript Core 1.0.8+
you can follow this tutorial to make an interact : [How to make an custom Interact ?](create-custom-interact.md)

There is a small example that will work :

```json
{
	"name": "Test My Amazing Shard",
	"tag": "myamazinginteractshard",
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
            "name": "open_shard",
            "tag": "myAmazingShard"
        }, ]
}
```


You will have a shard popup that will open ! 

# Test your interact and your shard !

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack//myAmazingDatapack

the structure of the folder should be


```structure
📂myAmazingDatapack
├── 📃 desc.json
├── 📁 shard
|    └── 📃 myAmazingShard.json
└── 📁 interact
     └── 📃 myamazinginteractphonedialog.json
```

Select the datapack "myAmazingDatapack" in cycle interact ([What are you talking about ?](cet-key-binding.md))

then hit the key for use your interact. Dialog should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)