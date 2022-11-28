# Create custom Quest

> In this page, you will be able to follow small Tutorials about making your own Quest in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to play the described mission.**

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
<br>Now let's go deeper! We will create .... Quest !

# ⚔ Create a Quest

**📂 Setup the folder**

First, in your datapack folder, create an folder named "mission". It will contain every missions script of your datapack. Logic !<br>
In this folder, create a JSON text file (like for example : amazingMission.json), **open it with your text editor of choice.**<br>

# 💀 Write the quest skeleton
Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about mission structure

A mission/quest has several things :

- An "title"
- an "Content description"
- an "recommanded Level"
- an "questtype" : you can find the definition [here](https://nativedb.red4ext.com/gameJournalQuestType)
- an "district" : you can find the definition [here](https://nativedb.red4ext.com/gamedataDistrict)
- is "recurrent" or not
- several triggers (what will unlock the quest)
- triggers requirement (in which order trigger need to be fullfilled to unlock the quest)
- an Unlock action list : somes action you will perform when it unlock the quest (prior to Cyberscript 1.3.0+)
- an Trigger action list : somes action you will perform when you take the quest
- an objectives list : an quest have several objective, that can be optionnal or not, locked or not. we will talk about it later in this page.
- an end action list : some action you will perform when you finish the quest
- an failure action list : some action you will perform when you fail the quest

**Now let's make it into a JSON :**

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "unlock_action": [ ],
    "trigger_condition": { },
    "trigger_condition_requirement": [
        []
    ],
    "trigger_action": [ ],
	"objectives": [ ],
    "end_action": [ ],
    "failure_action": [ ]
}
```

This is the skeleton of our quest. what you see below : The quest is named "Amazing Mission", its described as "It's an really amazing quest that will change even the reality of the world !". Cyberscript know her as "amazingMission". It's for an recommanded player level of 10. It's an Main Quest (0) that happen in JapanTown (62).

Now let's fill some triggers and requirement.

For this example, we want the quest can be unlocked when you see Rogue as Fixer in the Afterlife.

So let's add a trigger "fixer"

you can found all trigger definitions [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/triggertemplate.json)

**The trigger for fixer is :**
```json
{
	"name": "npc",
	"way": "fixer",
	"value": "fixer_rogue",
	"way_help": "phone||speak||fixer",
	"value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
	"helper": "This trigger will be triggered when you talk with a specific NPC",
	"helperTitle": "NPC : who is talking"
}
```

let's add it to our mission as myfixer trigger and add it in requirement too :

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "trigger_condition": {
            "myfixer": {
                "name": "npc",
                "way": "fixer",
                "value": "fixer_rogue",
                "way_help": "phone||speak||fixer",
                "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
                "helper": "This trigger will be triggered when you talk with a specific NPC",
                "helperTitle": "NPC : who is talking"
            }
    },
    "trigger_condition_requirement": [
        [
           "myfixer"
        ]
    ],
    "unlock_action": [ ],
    "trigger_action": [ ],
    "objectives": [ ],
    "end_action": [ ],
    "failure_action": [ ]
}
```

All right, we have setup an condition for getting the mission !

Now let's talk about trigger action AKA what your script should to when player take and track the mission.

For this example, we want that Rogue say "Some bonks attack the afterlife, show them some respect" then V will answer an random answer then we show to the player where he need to go.

This setup the mission.

We will fill the list of trigger_action

We will fill it with action. You can find every possible action [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/actiontemplate.json)

lets fill our json and describe every action

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "trigger_condition": {
            "myfixer": {
                "name": "npc",
                "way": "fixer",
                "value": "fixer_rogue",
                "way_help": "phone||speak||fixer",
                "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
                "helper": "This trigger will be triggered when you talk with a specific NPC",
                "helperTitle": "NPC : who is talking"
            }
    },
    "trigger_condition_requirement": [
        [
           "myfixer"
        ]
    ],
    "unlock_action": [ ],
    "trigger_action": [
        {
            "name": "subtitle",
            "title": "Some bonks attack the afterlife, show them some respect !",
            "type": 1,
            "target": "player",
            "speaker": "Rogue",
            "persistent": false,
            "duration": 3
        }, 
	{
            "name": "random_subtitle",
            "title": [
                "On it. ",
                "Consider it done.",
                "On my way",
                "Gotcha.",
                "They will pay for it",
                "I will not let them survive",
                "It will be an carnage"
            ],
            "type": 1,
            "target": "player",
            "speaker": "V",
            "duration": 3,
            "helper": "This action will fire an random subtitle, it act live wait for second",
            "helperTitle": "Dialog : run random subtitle"
        }, 
	{
            "name": "set_mappin",
            "tag": "mymappintag",
            "typemap": "CustomPositionVariant",
            "wall": true,
            "active": true,
            "mapgroup": "",
            "title": "test_mission",
            "desc": "test_mission",
            "position": "at",
            "position_range": 0,
            "position_lookatdistance": 0,
            "position_tag": "",
            "position_way": "normal",
            "position_poi_district": "",
            "position_poi_subdistrict": "",
            "position_poi_is_for_car": false,
            "position_poi_from_position": false,
            "position_poi_use_location_tag": false,
            "position_poi_type": 1,
            "position_distance": 0,
            "position_house_way": "default",
            "position_house_tag": "",
            "position_node_usegameplay": false,
             "x": -1530,
             "y": 986,
             "z": 23
        }
    ],
    "objectives": [ ],
    "end_action": [ ],
    "failure_action": [ ]
}
```

First one is "subtitle".

- title : it will display an subtitle with the text described in "title" field.
- Type 1 means Regular (you can check every possible type [here](https://nativedb.red4ext.com/scnDialogLineType)
- target : player means the entity who the subtitle will be affected is the player
- speaker is the speaker. It's an text. In our case we write Rogue. So it will display "Rogue : Some bonks attack the afterlife, show them some respect !".You can put banana or anything. It's just an text that indicate who speak. -persistent : false means that the subtitle doesn't stay forever displayed. -duration : means in second how much time it will be displayed if not persistent.

Then we will make the answer of V. We want much varieties so V will be able answer an random subtitle from an list. we use the action "random_subtitle"

- title : it will display an random text in the list. It's an list of text so you have ["textA","textB"...]
- Type 1 means Regular (you can check every possible type [here](https://nativedb.red4ext.com/scnDialogLineType)
- target : player means the entity who the subtitle will be affected is the player
- speaker is the speaker. It's a text. In our case we write V. So it will display "V: [random text]". You can put banana or anything. It's just an text that indicate who speak. -persistent : false means that the subtitle doesn't stay forever displayed. -duration : means in second how much time it will be displayed if not persistent.

Finally we want set an map pin to indicate to the player where he need to go to start the first objective. We use the action : set_mappin. it's an complex at look but easy action. let's take an look :

- "tag", the tag of the mappin for let cyberscript engine know who is it.
- "typemap", the type of icon of the mappin. in our case we want it as custom white mappin. you can find all possibilities [here](https://nativedb.red4ext.com/gamedataMappinVariant)
- "wall" : this mapin can be seen through wall.
- "active" : this mappin is tracked
- "mapgroup" : you can bound several mappin in an group. In our case, we doesn't need it now
- "title" : the title of the mappin when you hover it on map
- "desc" : the description of the mappin when you hover it on map -"position" : we use "at" means we want set an mappin at defined location XYZ You don't need to take care of

```json
      "position_range": 0,
      "position_lookatdistance": 0,
      "position_tag": "",
      "position_way": "normal",
      "position_poi_district": "",
      "position_poi_subdistrict": "",
      "position_poi_is_for_car": false,
      "position_poi_from_position": false,
      "position_poi_use_location_tag": false,
      "position_poi_type": 1,
      "position_distance": 0,
      "position_house_way": "default",
      "position_house_tag": "",
      "position_node_usegameplay": false,
```
It's unused when we use "at"

- X,Y,Z : coordinate of the location you want target.

All right. now we have setup the thing. let's talk about objectives. ^

# ✅ Setting up the objectives

An quest have one or several objective. For finish the mission, you need complete every non optional objectives. Usually, an finished objective will unlock an new one. For our example :

**1️⃣ Objective 1 : We want that, when V reach the mappin we setup before, it unlock the objective number 2.**

let's fill our JSON and describe it after.

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "trigger_condition": {
            "myfixer": {
                "name": "npc",
                "way": "fixer",
                "value": "fixer_rogue",
                "way_help": "phone||speak||fixer",
                "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
                "helper": "This trigger will be triggered when you talk with a specific NPC",
                "helperTitle": "NPC : who is talking"
      }
    },
    "trigger_condition_requirement": [
        [
           "myfixer"
        ]
    ],
    "unlock_action": [ ],
    "trigger_action": [
        {
            "name": "subtitle",
            "title": "Some bonks attack the afterlife, show them some respect !",
            "type": 1,
            "target": "player",
            "speaker": "Rogue",
            "persistent": false,
            "duration": 3
        }, 
	{
            "name": "random_subtitle",
            "title": [
                "On it. ",
                "Consider it done.",
                "On my way",
                "Gotcha.",
                "They will pay for it",
                "I will not let them survive",
                "It will be an carnage"
            ],
            "type": 1,
            "target": "player",
            "speaker": "V",
            "duration": 3,
            "helper": "This action will fire an random subtitle, it act live wait for second",
            "helperTitle": "Dialog : run random subtitle"
        }, 
	{
            "name": "set_mappin",
            "tag": "amazingmission_mappin_01",
            "typemap": "CustomPositionVariant",
            "wall": true,
            "active": true,
            "mapgroup": "",
            "title": "Amazing Mission",
            "desc": "Go at this place and see what's happen",
            "position": "at",
            "position_range": 0,
            "position_lookatdistance": 0,
            "position_tag": "",
            "position_way": "normal",
            "position_poi_district": "",
            "position_poi_subdistrict": "",
            "position_poi_is_for_car": false,
            "position_poi_from_position": false,
            "position_poi_use_location_tag": false,
            "position_poi_type": 1,
            "position_distance": 0,
            "position_house_way": "default",
            "position_house_tag": "",
            "position_node_usegameplay": false,
             "x": -1530,
             "y": 986,
             "z": 23
        }
    ],
    "objectives": [
          {
            "title": "Go to the point",
            "tag": "amazingMission_01",
            "state": 2,
			"unlock":[],
			"extra":
			{
				"mappin":"amazingmission_mappin_01"
			
			},
            "isoptionnal": false,
            "trigger": {
                "playeratposition": {
                    "name": "entity_is_at_mappin_position",
                    "tag": "amazingmission_mappin_01",
                    "entity": "player",
                    "range": 5
                }
            },
            "requirement": [
                [
                    "playeratposition"
                ]
            ],
            "action": [
                {
                    "name": "notify",
                    "value": "You are at the good place !"
                }
            ],
            "failaction": [ ],
            "resume_action": [ ]
        }, 
    ],
    "end_action": [ ],
    "failure_action": [ ]
}
```

Sooo... it add some texts, right ? But don't be scared, we are good !

**Let's see in detail:**

- "title" : the title of the objective
- "tag" : the tag of the objective (cyberscript engine will know it as ) 
- "state" : the default state of the objective, you can found all definition [here](https://nativedb.red4ext.com/gameJournalEntryState)
- "unlock": list of tag of the objectives who will be unlocked when the objective is completed
- "extra": extra data that will be showed at the right side of the quest in the journal

**Extra**

it can be : 
- "mappin": tag of an exisiting mappin, when you click on it, it will open the map at the mappin coordinates.
Example:
```json
"extra":
{
	"mappin":"amazingmission_mappin_01"
},

```
- "data": A native game codex entry, you can find the list [here](https://github.com/cyberscript77/release/blob/main/bin/x64/plugins/cyber_engine_tweaks/mods/cyberscript/data/codex.json)

in our case, we can add for example Rogue:
```json
"extra":
{
	"data":
		[
			{
				"type":"gameJournalCodexEntry",
				"value":"codex/characters/quests/rogue"
			}
		]
},

```

- "custom" : a custom codex entry tag, when you click on it, it will open the custom codex entry by his tag.
```json
"extra":
{
	"custom":
		[
			{
				"tag":"myamazingcodexentry"
			}
		]
},

```



We put our at state 2 means Active (so you can track it by default, normal, it's the first one 😉)

- "isoptionnal" : false, this objective is not optionnal and need to be fullfilled for finish the mission.
- several triggers (what will finish the objective)
- triggers requirement (in which order trigger need to be fullfilled to finish the objective)
- an action list : somes action you will perform when you finish the objective.
- an failaction list : somes action you will perform when you fail the objective.
- an resume_action list : somes action you will perform when you re-track the objective.

Let's define trigger and requirement.

We want that the objective is finished when :
- V reach the mappin tagged amazingmission_mappin_01

so we put an trigger

```json
 "playeratposition": {
                    "name": "entity_is_at_mappin_position",
                    "tag": "amazingmission_mappin_01",
                    "entity": "player",
                    "range": 5
                }
```

You can translate it by it will be fullfilled when player arrived at mappin amazingmission_mappin_01 in an range of 5 from amazingmission_mappin_01 location.



we setup the requirement.


When the requirements are fullfilled according to triggers, Cyberscript will perform the "action" list.

After theses actions finished to run, the objective amazingMission_01 will have the state 3(Succeeded)

then we set in "unlock" list the objective(s) that will be unlocked when trigger is fullfilled according to requirement :

```json
"unlock":["amazingMission_02"] 
```

"amazingMission_02" is the tag of our next objective , let's talk about it !

**2️⃣ Objective 2 : We want that spawn an group of Maelstrom bonks that will run to V with an hostile attitude and shout a battle cry.**

let's fill our JSON and describe it after.

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",

    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,

    "recurrent": true,
    "trigger_condition": {

        "myfixer": {
            "name": "npc",
            "way": "fixer",
            "value": "fixer_rogue",
            "way_help": "phone||speak||fixer",
            "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
            "helper": "This trigger will be triggered when you talk with a specific NPC",
            "helperTitle": "NPC : who is talking"

          }
    },
        "trigger_condition_requirement": [
            [
                "myfixer"
            ]
        ],
        "unlock_action": [ ],
        "trigger_action": [
            {
                "name": "subtitle",
                "title": "Some bonks attack the afterlife, show them some respect !",
                "type": 1,
                "target": "player",
                "speaker": "Rogue",
                "persistent": false,
                "duration": 3
            }, {
                "name": "random_subtitle",
                "title": [
                    "On it. ",
                    "Consider it done.",
                    "On my way",
                    "Gotcha.",
                    "They will pay for it",
                    "I will not let them survive",
                    "It will be an carnage"
                ],
                "type": 1,
                "target": "player",
                "speaker": "V",
                "duration": 3,
                "helper": "This action will fire an random subtitle, it act live wait for second",
                "helperTitle": "Dialog : run random subtitle"
            }, {
                "name": "set_mappin",
                "tag": "amazingmission_mappin_01",
                "typemap": "CustomPositionVariant",
                "wall": true,
                "active": true,
                "mapgroup": "",
                "title": "Amazing Mission",
                "desc": "Go at this place and see what's happen",
                "position": "at",
                "position_range": 0,
                "position_lookatdistance": 0,
                "position_tag": "",
                "position_way": "normal",
                "position_poi_district": "",
                "position_poi_subdistrict": "",
                "position_poi_is_for_car": false,
                "position_poi_from_position": false,
                "position_poi_use_location_tag": false,
                "position_poi_type": 1,
                "position_distance": 0,
                "position_house_way": "default",
                "position_house_tag": "",
                "position_node_usegameplay": false,
                "x": -1530,
                "y": 986,
                "z": 23
            }
        ],
        "objectives": [{
                "title": "Go to the point",
                "tag": "amazingMission_01",
                "state": 2,
                "isoptionnal": false,
				"unlock":["amazingMission_02"],
                "trigger": {
                    "playeratposition": {
                        "name": "entity_is_at_mappin_position",
                        "tag": "amazingmission_mappin_01",
                        "entity": "player",
                        "range": 5
                    }
                },
                "requirement": [
                    [
                        "playeratposition"
                    ]
                ],
                "action": [   
				{
                    "name": "notify",
                    "value": "You are at the good place !"
                }
                ],
                "failaction": [ ],
                "resume_action": [ ]
            }, {
                "title": "Kill the enemies",
                "tag": "amazingMission_02",
                "state": 1,
				"unlock":["amazingMission_03"],
                "isoptionnal": false,
                "trigger": {
                    "trigger": {
                        "name": "auto"
                    }
                },
                "requirement": [
                    [
                        "trigger"
                    ]
                ],
                "action": [
	            {
                        "name": "create_group",
                        "tag": "amazingMission_02_npc_group"
                    }, 
					{
                        "name": "spawn_npc",
                        "tag": "amazingMission_02_npc",
                        "spawnlevel": 42,
                        "use_police_prevention_system": true,
                        "group": "amazingMission_02_npc_group",
                        "appearance": "none",
                        "create_group_if_not_exist": false,
                        "source": "npc",
                        "source_tag": "Character.cpz_maelstrom_grunt2_ranged2_ajax_wa",
                        "source_list": [],
                        "source_use_vip": false,
                        "source_use_rival": false,
						"position": "relative_to_entity",
                        "position_tag": "player",
                        "position_way": "behind",
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
                        "amount": 3
                    },
					{
                        "name": "wait_second",
                        "value": 3
                    },
                    {
                        "name": "move_group_at_entity_relative_position",
                        "entity": "player",
                        "x": -3,
                        "y": -3,
                        "z": 0,
                        "move": "Sprint",
                        "tag": "amazingMission_02_npc_group"
                    },
                    {
                        "name": "new_map_point_to_group",
                        "group": "amazingMission_02_npc_group",
                        "typemap": "EffectShootVariant",
                        "wall": true,
                        "active": false,
                        "mapgroup": "amazingMission_02_npc_group_mappin"
                    },
					{
                        "name": "attitude_group_against_entity",
                        "entity": "player",
                        "tag": "amazingMission_02_npc_group",
                        "attitude": "hostile"
                    }, 
					{
                        "name": "play_group_voice",
                        "tag": "amazingMission_02_npc_group",
                        "voice": "battlecry_curse"
                    }, 
					{
                        "name": "wait_second",
                        "value": 3
                    } 
					
                ],
                "failaction": [ ],
                "resume_action": [ ]
            },
        ],
        "end_action": [ ],
        "failure_action": [ ]
    }
```

Another bunch of text, but don't worry, as always, let's look at slowly !

We set a new objective, similar to the first one. But we change the default state as Inactive (1) so it will not be visible and is locked. For the trigger, we set a trigger "auto". that's mean we don't need any particular trigger and it will be fullfilled automatically. we set the requirment. now let's talk about the actions list.

What we will do :

- action "create_group" : set a group for group spawned enemies together. It's easier to manipulate. the group need to be set before that we spawn the npcs because after we will say "spawn in that group".
- "spawn_npc" : here we are. it will be your new best friend because you will use often this action ;)

let's describe it :

- tag : the tag of npc for let's cyberscript engine know it.
- spawnlevel : don't care, but any number, it's more for engine.
- use_police_prevention_system : we will use the prevention system for spawn them. there are several way to spawn an npc. This one is the classic one.
- group : remember "spawn in that group" ? so we put our group tag here .
- appearance : useful if you want to setup an specific appearance (like naked judy 🐷) but in our case, we don't need.
- create_group_if_not_exist :false, don't care about it. But with this, you don't need to use create_group action before, it will create an group automatically.
- source : npc. there is several source but npc means we will indicate to the mod directly what model of npc we want spawn.
- source_tag : we set the model name (TweakID) of the one that we want : Character.cpz_maelstrom_grunt2_ranged2_ajax_wa. you can found all possible model [here](https://github.com/donk7413/cybermod_release_repository/blob/main/quest_mod/data/db/CharacterTable.xlsx?raw=true)

**don't care about :**

```json
    "source_list": [],
    "source_use_vip": false,
    "source_use_rival": false,        
    "position_poi_district": "",
    "position_poi_subdistrict": "",
    "position_poi_is_for_car": false,
    "position_poi_from_position": false,
    "position_poi_use_location_tag": false,
    "position_poi_range": 0,
    "position_poi_type": 0,
    "x": 0,
    "y": 0,
    "z": 0,
```

it's unused in our case.

- position : relative_to_entity, means we will spawn it at an relative position of an entity
- position_tag : we want that entity is the player
- position_way : and we want it spawn behind the player
- position_distance : at 5m behind the player ;)
- amount : we want it spawn 3 bonks, so we put 3. Logic again :)

Now we want it wait 3 second, to give time to the game to spawn correctly the entities (it's an failsafe action, because the game act weird with spawn sometimes...)

so we use action : wait_second with value at 3

then we will move theses bonks to player relative position at X -3 and Y -3. We want they sprint. so we use action

```json
{
    "name": "move_group_at_entity_relative_position",
    "entity": "player",
    "x": -3,
    "y": -3,
    "z": 0,
    "move": "Sprint",
    "tag": "amazingMission_02_npc_group"
}
```

tag is the group of our entities.

We also want that there is a mappin over the head of every entity. to show to the player who are the bonks.

we use the action :

```json
{
    "name": "new_map_point_to_group",
    "group": "amazingMission_02_npc_group",
    "typemap": "EffectShootVariant",
    "wall": true,
    "active": false,
    "mapgroup": "amazingMission_02_npc_group_mappin"
},
```

it will create for each bonks a mappin that will be seen through wall, type EffectShootVariant and grouped into amazingMission_02_npc_group_mappin (for easy manipulation)

then we want that theses bonks become hostile to V so we use

```json
{
    "name": "attitude_group_against_entity",
    "entity": "player",
    "tag": "amazingMission_02_npc_group",
    "attitude": "hostile"
}, 
```

it will set the attitude as Hostile for every entity in amazingMission_02_npc_group group toward the player(V)

after this, we want them to shout a battle cry, so we put action :

```json
{
    "name": "play_group_voice",
    "tag": "amazingMission_02_npc_group",
    "voice": "battlecry_curse"
}, 
```

voice is an game voice name reference. you can found them all [here](possible-voices.md)

Now we want it wait 3 second again, to give time to them to comes to you. so we use action : wait_second with value at 3

then we set in "unlock" objective 3 (tag "amazingMission_03")

```json
"unlock":["amazingMission_03"] 
```


All right ! Now we will go to the last objective !

**3️⃣ Objective 3 : Kill them all !**

Easy but hard. We want that the objective is finished when V have killed all of the bonks ! It will set the end of the mission.

let's fill our JSON :

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "trigger_condition": {
        "myfixer": {
            "name": "npc",
            "way": "fixer",
            "value": "fixer_rogue",
            "way_help": "phone||speak||fixer",
            "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
            "helper": "This trigger will be triggered when you talk with a specific NPC",
            "helperTitle": "NPC : who is talking"

          }
        },
        "trigger_condition_requirement": [
            [
                "myfixer"
            ]
        ],
        "unlock_action": [ ],
        "trigger_action": [
            {
                "name": "subtitle",
                "title": "Some bonks attack the afterlife, show them some respect !",
                "type": 1,
                "target": "player",
                "speaker": "Rogue",
                "persistent": false,
                "duration": 3
            }, {
                "name": "random_subtitle",
                "title": [
                    "On it. ",
                    "Consider it done.",
                    "On my way",
                    "Gotcha.",
                    "They will pay for it",
                    "I will not let them survive",
                    "It will be an carnage"
                ],
                "type": 1,
                "target": "player",
                "speaker": "V",
                "duration": 3,
                "helper": "This action will fire an random subtitle, it act live wait for second",
                "helperTitle": "Dialog : run random subtitle"
            }, {
                "name": "set_mappin",
                "tag": "amazingmission_mappin_01",
                "typemap": "CustomPositionVariant",
                "wall": true,
                "active": true,
                "mapgroup": "",
                "title": "Amazing Mission",
                "desc": "Go at this place and see what's happen",
                "position": "at",
                "position_range": 0,
                "position_lookatdistance": 0,
                "position_tag": "",
                "position_way": "normal",
                "position_poi_district": "",
                "position_poi_subdistrict": "",
                "position_poi_is_for_car": false,
                "position_poi_from_position": false,
                "position_poi_use_location_tag": false,
                "position_poi_type": 1,
                "position_distance": 0,
                "position_house_way": "default",
                "position_house_tag": "",
                "position_node_usegameplay": false,
                "x": -1530,
                "y": 986,
                "z": 23
            }
        ],
        "objectives": [{
                "title": "Go to the point",
                "tag": "amazingMission_01",
				"unlock":["amazingMission_02"],
                "state": 2,
                "isoptionnal": false,
                "trigger": {
                    "playeratposition": {
                        "name": "entity_is_at_mappin_position",
                        "tag": "amazingmission_mappin_01",
                        "entity": "player",
                        "range": 5
                    }
                },
                "requirement": [
                    [
                        "playeratposition"
                    ]
                ],
                "action": [
				   {
                    "name": "notify",
                    "value": "You are at the good place !"
                }
                ],
                "failaction": [ ],
                "resume_action": [ ]
            }, {
                "title": "Fight the enemies",
                "tag": "amazingMission_02",
				"unlock":["amazingMission_03"],
                "state": 1,
                "isoptionnal": false,
                "trigger": {
                    "trigger": {
                        "name": "auto"
                    }
                },
                "requirement": [
                    [
                        "trigger"
                    ]
                ],
                "action": [
	                {
                        "name": "create_group",
                        "tag": "amazingMission_02_npc_group"
                    }, 
					{
                        "name": "spawn_npc",
                        "tag": "amazingMission_02_npc",
                        "spawnlevel": 42,
                        "use_police_prevention_system": true,
                        "group": "amazingMission_02_npc_group",
                        "appearance": "none",
                        "create_group_if_not_exist": false,
                        "source": "npc",
                        "source_tag": "Character.cpz_maelstrom_grunt2_ranged2_ajax_wa",
                        "source_list": [],
                        "source_use_vip": false,
                        "source_use_rival": false,
						"position": "relative_to_entity",
                        "position_tag": "player",
                        "position_way": "behind",
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
                        "amount": 3
                    },
					{
                        "name": "wait_second",
                        "value": 3
                    },
                    {
                        "name": "move_group_at_entity_relative_position",
                        "entity": "player",
                        "x": -3,
                        "y": -3,
                        "z": 0,
                        "move": "Sprint",
                        "tag": "amazingMission_02_npc_group"
                    },
                    {
                        "name": "new_map_point_to_group",
                        "group": "amazingMission_02_npc_group",
                        "typemap": "EffectShootVariant",
                        "wall": true,
                        "active": false,
                        "mapgroup": "amazingMission_02_npc_group_mappin"
                    },
					{
                        "name": "attitude_group_against_entity",
                        "entity": "player",
                        "tag": "amazingMission_02_npc_group",
                        "attitude": "hostile"
                    }, 
					{
                        "name": "play_group_voice",
                        "tag": "amazingMission_02_npc_group",
                        "voice": "battlecry_curse"
                    }, 
					{
                        "name": "wait_second",
                        "value": 3
                    }
                ],
                "failaction": [],
                "resume_action": []
            },
            {
            "title": "Kill them all !",
            "tag": "amazingMission_03",
            "state": 1,
			"unlock":[],
            "isoptionnal": false,
            "trigger": {
                "trigger": {
                    "name": "killed_group",
                    "tag": "amazingMission_02_npc_group"
                }
            },
            "requirement": [
                [
                    "trigger"
                ]
            ],
            "action": [ ],
            "failaction": [ ],
            "resume_action": [ ]
        }
        ],
        "end_action": [ ],
        "failure_action": [ ]
    }
```

Very easy objective. it will finish automatically when you have killed all of the entities in the group amazingMission_02_npc_group.

No need any action. The end of the mission will be in the "end_action" list of the mission. It's just here for say "Hey I kill them all, it's done !"

# 🏁 Finish the mission

When all of the non optionnal objectives are fullfilled, the mission will be finished and will execute actions in "end_action" list. In our case we want :

- wait 2 second (let the pressure cooldown ^^)
- delete the mappin.
- delete the corpses and associated mappins.
- delete the group of npcs
- send a phone notification from Rogues that tell you, "You are so cool, V !"
- reward you an random amount of money between 1000 and 2000

let's fill our JSON, we are close to the END !!!! I consider that now you know enough to read what happens in the script. Study is the key !

```json
{
    "title": "Amazing Mission",
    "content": "It's an really amazing quest that will change even the reality of the world !",
    "tag": "amazingMission",
    "recommandedlevel": 10,
    "questtype": 0,
    "district": 62,
    "recurrent": true,
    "trigger_condition": {
        "myfixer": {
            "name": "npc",
            "way": "fixer",
            "value": "fixer_rogue",
            "way_help": "phone||speak||fixer",
            "value_help": "use value (write the Name) for phone or Speak or value (write a tag text) for fixer",
            "helper": "This trigger will be triggered when you talk with a specific NPC",
            "helperTitle": "NPC : who is talking"
         }
    },
        "trigger_condition_requirement": [
            [
                "myfixer"
            ]
        ],
        "unlock_action": [ ],
        "trigger_action": [
            {
                "name": "subtitle",
                "title": "Some bonks attack the afterlife, show them some respect !",
                "type": 1,
                "target": "player",
                "speaker": "Rogue",
                "persistent": false,
                "duration": 3
            }, {
                "name": "random_subtitle",
                "title": [
                    "On it. ",
                    "Consider it done.",
                    "On my way",
                    "Gotcha.",
                    "They will pay for it",
                    "I will not let them survive",
                    "It will be an carnage"
                ],
                "type": 1,
                "target": "player",
                "speaker": "V",
                "duration": 3,
                "helper": "This action will fire an random subtitle, it act live wait for second",
                "helperTitle": "Dialog : run random subtitle"
            }, {
                "name": "set_mappin",
                "tag": "amazingmission_mappin_01",
                "typemap": "CustomPositionVariant",
                "wall": true,
                "active": true,
                "mapgroup": "",
                "title": "Amazing Mission",
                "desc": "Go at this place and see what's happen",
                "position": "at",
                "position_range": 0,
                "position_lookatdistance": 0,
                "position_tag": "",
                "position_way": "normal",
                "position_poi_district": "",
                "position_poi_subdistrict": "",
                "position_poi_is_for_car": false,
                "position_poi_from_position": false,
                "position_poi_use_location_tag": false,
                "position_poi_type": 1,
                "position_distance": 0,
                "position_house_way": "default",
                "position_house_tag": "",
                "position_node_usegameplay": false,
                "x": -1530,
                "y": 986,
                "z": 23
            }
        ],
        "objectives": [{
                "title": "Go to the point",
                "tag": "amazingMission_01",
				"unlock":["amazingMission_02"],
                "state": 2,
                "isoptionnal": false,
                "trigger": {
                    "playeratposition": {
                        "name": "entity_is_at_mappin_position",
                        "tag": "amazingmission_mappin_01",
                        "entity": "player",
                        "range": 5
                    }
                },
                "requirement": [
                    [
                        "playeratposition"
                    ]
                ],
                "action": [
				   {
                    "name": "notify",
                    "value": "You are at the good place !"
                }
                ],
                "failaction": [],
                "resume_action": []
            }, {
                "title": "Fight the enemies",
                "tag": "amazingMission_02",
				"unlock":["amazingMission_03"],
                "state": 1,
                "isoptionnal": false,
                "trigger": {
                    "trigger": {
                        "name": "auto"
                    }
                },
                "requirement": [
                    [
                        "trigger"
                    ]
                ],
                "action": [
	                {
                        "name": "create_group",
                        "tag": "amazingMission_02_npc_group"
                    }, 
					{
                        "name": "spawn_npc",
                        "tag": "amazingMission_02_npc",
                        "spawnlevel": 42,
                        "use_police_prevention_system": true,
                        "group": "amazingMission_02_npc_group",
                        "appearance": "none",
                        "create_group_if_not_exist": false,
                        "source": "npc",
                        "source_tag": "Character.cpz_maelstrom_grunt2_ranged2_ajax_wa",
                        "source_list": [],
                        "source_use_vip": false,
                        "source_use_rival": false,
						"position": "relative_to_entity",
                        "position_tag": "player",
                        "position_way": "behind",
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
                        "amount": 3
                    },
					{
                        "name": "wait_second",
                        "value": 3
                    },
                    {
                        "name": "move_group_at_entity_relative_position",
                        "entity": "player",
                        "x": -3,
                        "y": -3,
                        "z": 0,
                        "move": "Sprint",
                        "tag": "amazingMission_02_npc_group"
                    },
                    {
                        "name": "new_map_point_to_group",
                        "group": "amazingMission_02_npc_group",
                        "typemap": "EffectShootVariant",
                        "wall": true,
                        "active": false,
                        "mapgroup": "amazingMission_02_npc_group_mappin"
                    },
					{
                        "name": "attitude_group_against_entity",
                        "entity": "player",
                        "tag": "amazingMission_02_npc_group",
                        "attitude": "hostile"
                    }, 
					{
                        "name": "play_group_voice",
                        "tag": "amazingMission_02_npc_group",
                        "voice": "battlecry_curse"
                    }, 
					{
                        "name": "wait_second",
                        "value": 3
                    } 
					
                ],
                "failaction": [],
                "resume_action": []
            },
            {
            "title": "Kill them all !",
            "tag": "amazingMission_03",
			"unlock":[],
            "state": 1,
            "isoptionnal": false,
            "trigger": {
                "trigger": {
                    "name": "killed_group",
                    "tag": "amazingMission_02_npc_group"
                }
            },
            "requirement": [
                [
                    "trigger"
                ]
            ],
            "action": [],
            "failaction": [],
            "resume_action": []
        }
        ],
        "end_action": [

         {
            "name": "wait_second",
            "value": 2
         },
         {
            "name": "delete_map_group",
            "mapgroup": "amazingMission_02_npc_group_mappin"
         },
         {
            "name": "delete_map_point",
            "tag": "amazingmission_mappin_01"
         },
         {
            "name": "despawn_group",
            "tag": "amazingMission_02_npc_group"
         },
         {
            "name": "remove_group",
            "tag": "amazingMission_02_npc_group"
         },
         {
            "name": "phone_notification",
            "title": "Rogues",
            "desc": "You are so cool, V !",
            "duration": 14
        }, 
        {
            "name": "give_random_money",
            "min": 1000,
            "max": 2000
        }
        ],
        "failure_action": [ ]
    }
```

# Test your mission !

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be



```structure
📂myAmazingDatapack
├── 📃 desc.json
└── 📁 mission
    └── 📃 amazingMission.json
```

Then load your game. Load a save, go to Pause Menu, go to Mod , Go to Cyberscript Datapack Manager and enable myAmazingDatapack. MAKE SURE to have Auto refresh on!

Then go to see Rogue, open your journal and look under the "Available " section. You will see your mission !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)
