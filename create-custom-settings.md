# Creating Custom settings

> In this page, you will be able to follow a small tutorial about making your own Custom Setting in JSON and play it with Cyberscript.

**It will be a long, but fully complete tutorial. At the end you will be able to use the described Subject of this tutorial.**

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
<br>We will create .... Custom Settings!

# ⚙ Create a Setting

**❓ Why using Setting ?**

Custom Settings  are here if you want let your users customize their experience with your datapack.

**📂 Setup the folder**

First : in your datapack folder, create a folder named "setting". It will contain every function script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingSetting.json

Open it with your favorite text editor.

**💀 Write the Setting skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about setting structure :

An setting have several things at least:

- a tag
- a type
- a category
- a category Libelle
- a label
- a description
- a list of action 

Now let's make it into a JSON :

```json
{
  "tag": "mysetting",
  "type": "sliderInt",
  "category": "MySetting",
  "categorylibelle":"My settinf for XXX",
  "label": "An test slider",
  "description": "For a test",
  "action":[]
} 
```

This is the skeleton of our setting. 

Now let's talk about the type

# Type

A Setting always has a  "type". Depending of that "type", you can do several things.

Let's dive !

# Button

An easy and simple button that will perform action.

Take a look : 

```json
{
  "tag": "mysetting",
  "type": "button",
  "category": "MySetting",
  "categorylibelle":"My setting for XXX",
  "label": "An test button",
  "buttonlabel": "test Me !",
  "textsize":45,
  "description": "For a test",
  "action":[
  {
    "name":"notify",
    "value":"hello !"
  }
  ]
} 
```

# Toggle

A toggle that will change an variable/key target to true/false. Action will be ran after the toggle.

Take a look : 

```json
{
  "tag": "mysetting",
  "type": "toggle",
  "category": "MySetting",
  "categorylibelle":"My setting for XXX",
  "label": "An test toggle",
  "description": "For a test",
  "defaultvalue":true,
  "variable":{
    "tag":"myvar",
    "key":"mykey"
  },
  "action":[
  {
    "name":"notify",
    "value":"hello !"
  }
  ]
}
```

**Note : "variable" should target an variable key combo who have a boolean(true/false) as value**

# Slider (number)

A slider that will change a variable/key target to desired value. Action will be ran after you Click n hold, slide, release Click.

- "min" : minimal possible value
- "max" : maximal possible value
- "step" : how much it increase by slide

**Note : "variable" should target an variable key combo who have an number (not decimal ) as value**

Take an look :

```json
{
  "tag": "mysetting",
  "type": "sliderInt",
  "category": "MySetting",
  "categorylibelle":"My setting for XXX",
  "label": "An test slider",
  "description": "For a test",
   "defaultvalue":50,
  "variable":{
    "tag":"myvar",
    "key":"mykey"
  },
  "min":0,
  "max":100,
  "step"1,
  "action":[
  {
    "name":"notify",
    "value":"hello !"
  }
  ]
}
```

# Slider (decimal)
Same than "sliderInt" but it can accept decimal value rounded as 0.00.

**Note : "variable" should target a variable key combo who have an number, or decimal, as value**

```json
{
  "tag": "mysetting",
  "type": "sliderFloat",
  "category": "MySetting",
  "categorylibelle":"My setting for XXX",
  "label": "An test slider",
  "description": "For a test",
   "defaultvalue":50.55,
  "variable":{
    "tag":"myvar",
    "key":"mykey"
  },
  "min":0,
  "max":100,
  "step"0.1,
  "action":[
  {
    "name":"notify",
    "value":"hello !"
  }
  ]
}
```

# Slider(text)

A slider that will change a variable/key target to desired index of a list.

So assume that we have a variable Mylist with key List that contains

```json 
["Option 1", "Option 2", "Option 3", "Option 4"]
```

if you choose "Option 3", it will store in target variable : 3 because it's the index 3 of the list.

Action will be ran after sliding it.

The possible options are taken from an exisitng variable and will be stored in a targeted variable.

**"defaultvalue" is the index of the selected element of that list.**

**Note : "variable" should target a variable key combo that has a list of texts as value**

Take a look : 

```json
{
  "tag": "mysetting",
  "type": "sliderText",
  "category": "MySetting",
  "categorylibelle":"My setting for XXX",
  "label": "An test slider",
  "description": "For a test",
  "variable":{
    "tag":"myvar",
    "key":"mykey"
  },
 "defaultvalue":1,
  "target":{
    "tag":"myvar2",
    "key":"mykey2"
  },
  "action":[
  {
    "name":"notify",
    "value":"hello !"
  }
  ]
}
```

# Test your setting!

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
└── 📁 setting
     └── 📃 amazingSetting.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack. Go back to  Mods , Cyberscript Custom Settings,  Refresh Cache, and enjoy !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
