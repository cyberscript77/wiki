# Create custom Garage Entry

> In this page, you will be able to follow an small tutorials about making your own Garage entry in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described Garage entry.**

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
<br>We will create .... Garage entry!

# 💬 Create a Garage entry

**📂 Setup the folder**

First : in your mod folder, create a folder named "garage". It will contain every Garage entry script of your mod. Logic !

In this folder, create a JSON text file, like for example : amazingCar.json

Open it with your favorite text editor.

**💀 Write the Garage skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about codex structure :

A codex is a text. :
- A tag : Cyberscript will know it by this.
- A name : the name of the entry in the list
- A type :  Bike = 0,   Car = 1,
- tweak : the tweak of the vehicle that it should be in the list
- trigger 
- requirement
- action (when selected in the list)

Now let's make it in JSON :

```json

		{

			"name":"My Police Car",
			"tag":"amazingCar",
			"type":1,
			"tweak":"Vehicle.cs_savable_archer_hella_police_siren",
			"trigger":{
				"auto":{
					"name":"auto"
				}
			},
			"requirement":[["auto"]],
			"action":[
			
				{
					"name": "spawn_vehicule_v2",
					"tag": "police_car",
					"spawnlevel": 36,
					"appearance": "",
					"spawn_system": 3,
					"scriptlevel":0,
					"group": "",
					"create_group_if_not_exist": false,
					"source": "vehicle",
					"source_helper": "vehicle||faction||current_district_leader||current_subdistrict_leader||district_leader||subdistrict_leader||random||from_list||district_rival||subdistrict_rival||current_district_rival||current_subdistrict_rival",
					"source_tag": "Vehicle.cs_savable_archer_hella_police_siren",
					"source_gang": "faction_mox",
					"source_list": ["Vehicle.cs_savable_archer_hella_police_siren"],
					"source_tag_helper": "Vehicle.cs_savable_archer_hella_police_siren||faction_mox||district_westbrook||NorthOaks",
					"source_use_rival": false,
					"position": "relative_to_entity",		
					"position_helper": "at||relative_to_entity||node||player_look_at||poi||mappin||fasttravel||custom_place||custom_room",
					"position_change_helper": "Write 'current' in position_tag for get current node,mappin, fasttravel, custom_place or custom_room. \n For poi if you write 'current' in position_poi_district you will get the current district, \n if you write 'current in position_poi_subdistrict you will get the current subdistrict. \n also if you write 'random' in position_poi_subdistrict or position_poi_district, you will get an 'random' value",
					"position_range": 50,
					"position_lookatdistance":0,		
					"position_tag": "player",
					"position_tag_helper": "judy01||playerhouse01||playerhouse_bed||",
					"position_way": "behind",
					"position_way_helper": "normal||behind||forward",
					"position_poi_district": "",
					"position_poi_subdistrict": "",
					"position_poi_is_for_car": false,
					"position_poi_from_position": false,
					"position_poi_use_location_tag": false,		
					"position_poi_type": 1,
					"position_distance": 10,
					"position_house_way": "default",
					"position_house_way_helper": "default||enter||exit",
					"position_house_tag": "playerhouse01",	
					"position_node_usegameplay": false,
					"x": 0,
					"y": 0,
					"z": 0,
					"amount": 1,
					"isAV": false,
					"appears_from_behind": false,
					"wait_for_vehicle": false,
					"help": "This action will summon a Vehicle with several custom parameter ",
					"helper": "This action will summon Vehicle with several custom parameter ",
					"helperTitle": "Vehicle : Spawn a Vehicle"
				}
			
			]



}

```


# Test your garage entry !

garage are called through Vehicle Manager Popup !

Copy your whole mod folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/mod//myAmazingmod

the structure of the folder should be


```structure
📂myAmazingmod
├── 📃 desc.json
├── 📃 init.lua
├── 📁 libs
├── 📁 scripts
	├── 📁 garage
|    		└── 📃 amazingCar.json
```

Select the mod "myAmazingmod" in cycle interact ([What are you talking about ?](cycle-throught-interact.md))

then open Vehicle Manager Popup . It should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
