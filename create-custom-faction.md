# Create custom Faction

In this page, you will be able to follow a small tutorial about making your own interact in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described faction.**

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
<br>We will create .... Factions !

# 🛡 Create a Faction

**📂 Setup the folder**

First : in your datapack folder, create a folder named "dialog". It will contain every dialog script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingFixer.json

Open it with your favorite text editor.

**💀 Write the Faction skeleton**

Now we have an blank page. But don't worry, we will fill it step by step.

Let's talk about Faction structure :

an Faction have several things :

- A Name : The name of your Faction
- A Tag : the tag of your Faction . Cyberscript will know it by this way.
- a DistrictTag : it need to be bounded to an district tag by default. you can find the list here (it can change with the gang wars  system)
- a Logo (optionnal, leave it to "" if you don't know) : In game logo name.
- A list of Rivals Tag : you will determine every rival faction by default (it can change with the gang wars system)
- A list of SpawnableNPC TweakID : all character model that can be in this faction. Useful when you use spawn_npc action that have  faction as source
- A list of AttitudeGroup : Will be useful for check for any looked entity that have this attitude group then you will be able to change the attitude toward another group or another entity (like player) you can find the list in quest_mod/data/db/attitudegroup. Use name field
- A list of SpawnableVehicule TweakID : all vehicle model that can be in this faction. Useful when you use spawn_vehicle action that have faction as source. you can find the list here
- A VIP object list. You can define some VIP of this faction. They will be available as spawn option if your affinity with this faction - is higher or equal to the VIP score.

You can find every character [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/CharacterTable.xlsx?raw=true). Use the Name Names (for example use Judy, no Character.Judy).

A VIP object look like this

```json
{
	"name": "Nix",
	"score": 0
},
```

Now let's make it in JSON :

```json
{
	"Name": "My Amazing Faction",
	"Tag": "myamazingfaction",
	"DistrictTag": "district_watson",
	"Logo": "logo_netwatch",
	"Rivals": [
		"faction_arasaka",
		"faction_kangtao",
		"faction_militech",
		"faction_maelstrom"
	],
	"SpawnableNPC": [
		"Character.afterlife_merc_fast_melee_m_hard",
		"Character.afterlife_merc_fast_melee_w_hard",
		"Character.afterlife_merc_generic_medium_range_m_hard",
		"Character.afterlife_merc_generic_medium_range_w_hard",
		"Character.afterlife_merc_netrunner_m_hard",
		"Character.afterlife_merc_netrunner_w_hard",
		"Character.afterlife_merc_strong_short_range_m_hard",
		"Character.afterlife_merc_strong_short_range_w_hard",
		"Character.afterlife_netrunner_netrunner2_yukimura_ma_rare",
		"Character.afterlife_netrunner_netrunner2_yukimura_wa_rare",
		"Character.afterlife_rare_fmelee3_katana_ma_elite",
		"Character.afterlife_rare_fmelee3_katana_wa_elite",
		"Character.afterlife_rare_fmelee3_mantis_ma_elite",
		"Character.afterlife_rare_fmelee3_mantis_wa_elite",
		"Character.afterlife_rare_franged2_ajax_ma_rare",
		"Character.afterlife_rare_franged2_ajax_wa_rare",
		"Character.afterlife_rare_franged2_overture_wa_rare",
		"Character.afterlife_rare_franged2_saratoga_ma_rare",
		"Character.afterlife_rare_franged2_saratoga_wa_rare",
		"Character.afterlife_rare_gunner3_hmg_mb_elite",
		"Character.afterlife_rare_sniper3_ashura_ma_elite"
	],
	"AttitudeGroup": [
		"rogue"
	],	
	"SpawnableVehicule": [
		"Vehicle.rogue_bike",	
		"Vehicle.rogue_car",
		"Vehicle.sq024_claire_truck",
		 "Vehicle.v_sport2_mizutani_shion", 
		 "Vehicle.v_sport2_quadra_type66", 
		 "Vehicle.v_sportbike2_arch",
		 "Vehicle.v_sportbike1_yaiba_kusanagi"
	],
	"VIP": [
		{
			"name": "Nix",
			"score": 0
		},
		{
			"name": "Nancy",
			"score": 20
		},
		{
			"name": "Henry",
			"score": 10
		},
		{
			"name": "Kerry",
			"score": 30
		}
	]
}
```

This is the skeleton of our faction. For resume what you see below : The faction is named "My Amazing Faction",

Cyberscript know it as "myamazingfaction".

it's related to watson

the logo is the netwatch logo

rivals are Cyberscript faction arasaka, kangtao, militech and maelstrom.

there is an list of many spawnable npc, vehicle and vip.

And that's all you need !

# Test your faction!

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be

📂myAmazingDatapack

```structure
├── 📃 desc.json
└── 📁 faction
     └── 📃 amazingFaction.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack

You will also see it on worldmap under faction icon !

You can now use it as faction for fixer's gig creation [Fixer tutorial](create-custom-fixer.md)

fill the field "faction" tag by myamazingfaction tag !

It can also take part of the Cyberscript Gang Wars system and be called in every possible action that involve your faction !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)