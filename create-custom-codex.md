# Create custom Codex Entry

> In this page, you will be able to follow an small tutorials about making your own codex entry in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described codex entry.**

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
<br>We will create .... codex entry!

# 💬 Create a codex entry

**📂 Setup the folder**

First : in your datapack folder, create a folder named "codex". It will contain every codex entry script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingcodex.json

Open it with your favorite text editor.

**💀 Write the codex skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about codex structure :

A codex is a text. :
- A tag : Cyberscript will know it by this.
- A title : the title of the codex in the list
- A description : the content of the codex
- locked : determine if the codex will be showed in the list or not  ?

Now let's make it in JSON :

```json

		{
			"tag":"amazingcodex",
			"title":"Hello There !",
			"description":"This is my \n custom codex entry !!! ",
			"locked":false


		}

```

Note that I use "\n", it means break line 😉 



# Test your interact and your codex !

Codex are called through an extra data on quest ([What are you talking about ?](create-custom-quest.md)) or directly in Codex journal menu if unlocked , under CyberScript Section.

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/datapack//myAmazingDatapack

the structure of the folder should be


```structure
📂myAmazingDatapack
├── 📃 desc.json
├── 📁 codex
|    └── 📃 amazingcodex.json
```

Select the datapack "myAmazingDatapack" in cycle interact ([What are you talking about ?](cet-key-binding.md))

then hit the key for use your interact. Dialog should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)