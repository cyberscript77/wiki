# Context

**Definition**

For each action you can now add field "context":

```json
{
    "name": "notify",
    "value": "Hello",
    "context": [
        {
            "trigger": {
                "auto": {
                    "name": "auto"
                }
            },
            "requirement": [["auto"]],
            "prop": 
			{
				"value": {
					"text": "##gangname are at x : ##posx  and y : ##posy",
					"values":{
						"gangname": {
							"type": "faction",
							"tag": "faction_mox",
							"prop": "Name"
						},
						"posx": {
							"type": "mappin",
							"tag": "MyMappin",
							"prop": "x"
						},
						"posy": {
							"type": "mappin",
							"tag": "MyMappin",
							"prop": "y"
						}
					}
				}
			}
		}
	]
}
```

in this example

we assume that we have already an mappin name "MyMappin" at x200, y300, z23

 The value of field "value" of the action "notify" will be replaced by the text of context[1].props.value.text, who will be filled with values of

- gangname(faction.faction_mox.Name)
- posx(mappin.mymappin.x)
- posy(mappin.mymappin.y)

the result will be : "Hello" become "Mox are at x: 200 and y:300"

# Returned Type

An context can return : 

- number : write "type":"number" as field in the context (same level than trigger)
- text : write "type":"text" as field in the context (same level than trigger)
- boolean (true/false) : write "type":"boolean" as field in the context (same level than trigger)
- don't write nothing means by default it will be the type of the returned value in props (text,number, boolean, list or object)

```json
"context": [
        {
            "trigger": {
                "auto": {
                    "name": "auto"
                }
            },
            "requirement": [["auto"]],
            "prop": 
			{
				"value": {
					"text": "##posx",
					"type":"number",
					"values":{
						"posx": {
							"type": "mappin",
							"tag": "MyMappin",
							"prop": "x"
						},
					}
				}
			}
		}
	]
```

# List of possible source of context

This is the list of every possible property of every possible object that you can call for now in an context

# "faction" :

- DistrictTag
- Name
- Logo
- Tag

```json 
"type": "faction",
"tag":"mytag",
"prop":"DistrictTag"
```

**Note :**

- if you put "player" as "Tag", it will be the current player faction
- if you put "random" as "Tag", it will be a random faction

# "player" :

- key : "item_amount"<br>
value : "Items.Preset_Pulsar_Pimp"
- key : "item_is_equipped"<br>
value : "Items.Preset_Pulsar_Pimp"
- key : "query_equipped_item"<br>
value : "Pulsar_Pimp"
- key : "skill"<br>
value : "Athletics"
- key : "perk"<br>
value : "Regeneration"
- key : "attribute"<br>
value : "Body"
- key : "current_gang"

```json
"type": "player",
"key":"skill",
"value ":"Athletics"
```


# "current_district"
- tag
- state (0 - Friendly, 1 - Neutral, 2 - Hostile) 
- subdistrict (return subdistrict enum)

```json
"type": "current_district",
"prop":"tag"
```

# "corpo" :

- tag
- title
- category
- owner
- ownerLibelle
- lastOwner
- lastOwnerLibelle
- progression
- progressionLibelle
- price
- buyable
- lastRank
- rank
- lastState
- lastStateLibelle
- faction

```json
"type": "corpo",
"tag":"biotechnica",
"prop":"faction"
```

# "lang"

- tag

```json
"type": "lang",
"tag":"mylangressource"
```

# "random_lang"

```json
"random_lang" : 
 "type": "random_lang",
 "list":["MyLangKey03","MyLangKey04","MyLangKey05","MyLangKey06"]
```

# "district_leader":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "district_leader",
"tag":"district_westbrook",
"prop":"Name"
```

# "subdistrict_leader":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "subdistrict_leader",
"tag":"CharterHill",
"prop":"Name"
```

# "current_district_leader":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "current_district_leader",
"prop":"Name"
```

# "current_subdistrict_leader":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "current_subdistrict_leader",
"prop":"Name"
```


# "district_rival":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "district_rival",
"tag":"mytag",
"prop":"Name"
```


# "subdistrict_rival":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "subdistrict_rival",
"tag":"mytag",
"prop":"Name"
```

# "current_district_rival":

- DistrictTag
- Name
- Logo
- Tag


```json
"type": "current_district_rival",
"tag":"mytag",
"prop":"Name"
```

# "current_subdistrict_rival":

- DistrictTag
- Name
- Logo
- Tag

```json
"type": "current_subdistrict_rival",
"tag":"mytag",
"prop":"Name"
```

For  district_rival/subdistrict_rival/current_district_rival/current_subdistrict_rival

Note : if in your props you define tag :"player", it will take the current player gang. 

For the NON Current one, add an field district to your prop.

Example :

```json
"gangname": {
            "type":"district_rival",
            "tag":"player",
		    "district":"district_westbrook",
            "prop":"Name"
        },
```

Will take the name of the rival of the player gang in westbrook

```json
"gangname": {
            "type":"current_district_rival",
            "tag":"player",
            "prop":"Name"
        },
```

Will take the name of the rival of the player gang in the current player district

```json
"gangname": {
            "type":"district_rival",
            "tag":"faction_mox",
            "district":"district_westbrook",
            "prop":"Name"
        },
```

Will take the name of the rival of the Mox gang in westbrook

```json
"gangname": {
            "type":"current_district_rival",
            "tag":"faction_mox",
            "prop":"Name"
        },
```

Will take the name of the rival of the Mox in the current player district

# "entity"

- key : position, prop : x/y/z
- key : forward, prop : x/y/z
- key : orientation, prop : yaw/pitch/roll ([Explanation](https://en.wikipedia.org/wiki/Aircraft_principal_axes#/media/File:Yaw_Axis_Corrected.svg))
- key : tag
- key : appearance
- key : tweak
- key : context
- key : displayname
- key : group

```json
 "type":"entity",
 "tag":"judy",
 "key":"position"
 "prop":"x"
```

# "mappin"

- tag
- x
- y
- z
- title
- desc
- group

```json
"type": "mappin",
"tag":"mymappintag",
"prop":"x"
```

# "fixer" or "current_fixer"(if not null) :

- Name
- LOC_X
- LOC_Y
- LOC_Z
- range
- Faction
- Tag
- NPCId

```json
"type": "fixer",
"tag":"mytag",
"prop":"LOC_X"
```

# "place" or "current_place" (if not nothing) :

- name
- tag
- posX
- posY
- posZ
- range
- Zrange
- EnterX
- EnterY
- EnterZ
- ExitX
- ExitY
- ExitZ
- price
- rent

```json
"type": "place",
"tag":"mytag",
"prop":"EnterY"
```

# "current_room" (if not nothing) :

- posX
- posY
- posZ
- range
- Zrange
- name
- tag

```json
"type": "current_room",
"prop":"tag"
```

# "poi" :

- x
- y
- z
- yaw
- pitch
- roll
- Tag
- subdistrict

Argument : 
- position_tag
- position_poi_district
- position_poi_subdistrict
- position_poi_is_for_car
- position_poi_type
- position_poi_from_position
- position_range
- position_poi_from_position_x
- position_poi_from_position_y
- position_poi_from_position_z
- position_poi_search
- position_poi_searchdistance

```json
"type": "poi",
"tag":"mytag",
"prop":"yaw",
"argument":{
	"position_tag":"",
	"position_poi_district":"",
	"position_poi_subdistrict":"",
	"position_poi_is_for_car":false,
	"position_poi_type":77,
	"position_poi_from_position":true,
	"position_range":50,
	"position_poi_from_position_x":0,
	"position_poi_from_position_y":0,
	"position_poi_from_position_z":0,
	"position_poi_search":"type",
	"position_poi_searchdistance":"random"
}
```

# "current_poi": (if not nothing)

- x
- y
- z
- yaw
- pitch
- roll
- tag
- district
- subdistrict
- type


```json
"type": "current_poi",
"prop":"type"
```

# "node":

- name
- tag
- X
- Y
- Z
- GameplayX
- GameplayY
- GameplayZ

```json
"type": "node",
"tag":"mytag",
"prop":"GameplayX"
```

# "custom_npc" :

- name
- tag
- tweakDB
- appeareance
- x
- y
- z
- radius

```json
"type": "custom_npc",
"tag":"mynpc",
"prop":"name"
```

# "npc" :

- ID
- Names
- TweakIDs

tag field is equal to Names in database

```json
"type": "npc",
"tag":"Judy",
"prop":"Names"
```

# "variable":

- variable
- key
- it can be translated by currentSave.Variable[variable][key]

```json
"type": "variable",
"variable":"myVar",
"key":"MyKey"
```

# "random_variable_key"

```json
"type": "random_variable_key",
"variable":"myVar"
```

# "text"

```json
"text":
"type": "text",
"value":"Helloworld"
```

# "random_text"

```json
"random_text" : 
 "type": "random_text",
 "list":["test1","test2","test3","test4"]
```

# "number":

```json
"type": "number",
"value":5
```

# "random_number"

```json
"random_number": 
"type": "random_number",
"list":[1,6,8,64]
```

# "random_range"

```json
"random_range": 
"type": "random_range",
"min":1,
"max":5
```

# "scannerdata"

```json
 "type": "scannerdata",
 "prop":"primaryname",
 "prop":"secondaryname",
 "prop":"text",
 "prop":"entityname",
 "prop":"level",
 "prop":"rarity",
 "prop":"attitude",
 "prop":"reward",
 "prop":"streetreward",
 "prop":"danger",
 "prop":"issuedby",
 "prop":"customtransgressions", (take random element of the list)
 "prop":"transgressions" (take random element of the list)
```

# "current_scannerdata"

```json
 "type": "current_scannerdata",
 "prop":"primaryname",
 "prop":"secondaryname",
 "prop":"text",
 "prop":"entityname",
 "prop":"level",
 "prop":"rarity",
 "prop":"attitude",
 "prop":"reward",
 "prop":"streetreward",
 "prop":"danger",
 "prop":"issuedby",
 "prop":"customtransgressions", (take random element of the list)
 "prop":"transgressions" (take random element of the list)
```

# "corpo_news":

Will return an random corpo news from online server

```json
"type": "corpo_news"
```

# "stock"

- userQuantity
- tag
- title
- statut
- quantity
- price
- inflate
- defaultStatut
- lastprice
- trend (boolean) (means the value have been increased or decreased from latest transaction
- trendvalue , percent of trend since the latest transaction

```json
"type": "stock",
"tag": "militech_action",
"prop": "price"
```

# "object"

You can define an whole new json object here. 

Free typing.

```json
"type": "object",
"value":{
"myprop1":"hellothere",
"myprop2":1
}
```

```json
"object":
"type": "object",
"value":["test","testt"]
```

# "list"

This one is complex. You can define an list of item. Each item is a context.

```json
"type": "list",
"items": [
	{
	"type": "random_text",
	"list": ["Items.WhistleLvl2Program", "Items.WhistleLvl2Program"]
	},
	{
	"type": "text",
	"value": "Items.GenericJunkItem6"
	},
	{
	"type": "random_text",
	"list": ["Items.ma_wat_kab_06_map", "Items.Mask_03_old_02"]
	},
	{
	"type": "variable",
	"variable":"special_items",
	"key":"skippy"
	},
]
```

# Extra Note: 

**Random :**

If in the tag field you put "random" for faction/ mappin /fixer /place  / node /npc, it will choose randomly an object of the list.

**Trigger and requirement**

An context have trigger and requirement<br>
Also, each props of an context can have trigger and requirements (optional)

For example : 

```json
"context": [
	{
		"trigger": {
			"nite": {
				"name": "time",
				"min": 2000,
				"max": 2359,
				"helper": "This trigger will be triggered when time in game will be between min and max value (format HHMM)",
				"helperTitle": "UI : Time is between"
			}
		},
		"requirement": [["nite"]],
		"prop": 
		{
			"value": {
				"text": "##msg",
				"values":{
					"msg": {
						"type": "text",
						"value":"Small nite !!!",
						"trigger": {
							"nite": 
								{
								"name": "time",
								"min": 2100,
								"max": 2200,
								"helper": "This trigger will be triggered when time in game will be between min and max value (format HHMM)",
								"helperTitle": "UI : Time is between"
								}
						},
						"requirement": [["nite"]],
					},
					"msg": {
						"type": "text",
						"value":"Big Nite !!!",
						"trigger": {
							"nite": 
							{
								"name": "time",
								"min": 2200,
								"max": 2359,
								"helper": "This trigger will be triggered when time in game will be between min and max value (format HHMM)",
								"helperTitle": "UI : Time is between"
							}
						},
						"requirement": [["nite"]],
					}
				}
			}
		}
	}
]
```

**Several context for one action :**

```json
{
	"name":"simple_message",
	"value":"Entity have bounty",
	"context": [
		{		
			"trigger": {
				"nite": {
						"name": "time",
						"min": 2000,
						"max": 2359,
						"helper": "This trigger will be triggered when time in game will be between min and max value (format HHMM)",
						"helperTitle": "UI : Time is between"
					}
				},
				"requirement": [["nite"]],
				"prop": 
				{
					"value": {
						"text": "##msg",
						"values":{
							"msg": {
								"type": "text",
								"value":"Nite !!!"
							}
						}
						
					}
				}
		},
		{		
			"jstrigger": {
					"day": {
						"name": "time",
						"min": 0800,
						"max": 1959,
						"helper": "This trigger will be triggered when time in game will be between min and max value (format HHMM)",
						"helperTitle": "UI : Time is between"
					}
			    },
				"requirement": [["day"]],
				"prop": 
				{
					"value": {
						"text": "##msg",
						"values":{
							"msg": {
								"type": "text",
								"value":"Mornin' !!!"
							}
						}
					}
				}
			}
	    ]
}
```

**In this case, the first context will work only when game time is between 8pm and 11;59pm. It will display Nite !!! the second context will work only when game time is between 8am and 7:59pm. It will display Mornin' !!!**

**Replace from another context prop:**

You can set an prop as vairable that can be usued in another prop. It's the best way to get from one object prop another object. for example get the faction_name of the player current faction.

Example :

```json
{
	"name":"simple_message",
	"value":"Test",
	"context": [
        {
					
			"trigger": {
				"auto": {
						"name": "auto"
						}
				},
				"requirement": [["auto"]],
				"prop": 
				{
				    "value": {
							"text": "Your faction is ##faction_name.",
							"values":{
								"playerfaction": {
									"type": "variable",
									"variable":"player",
									"key":"current_gang"
								},
								"faction_name": {
									"type": "faction",
									"tag":"faction_mox",
									"prop":"Name",
									"replace":"tag",
									"context_value":"playerfaction"
						        }
						    }
					    }
				    } 
			    }
		    ]
	    }
```

Here we defined an prop context "playerfaction" and we take the defined variable "player_gang" that will return the player's current gang tag.

Then in another props, we will replace the "tag" field by the value returned by the prop context "playerfaction" . So the mod will take the faction who have the tag that is equal to the player's current faction. Then it will display the Name of this faction.

Search an item from a specifc value of one of his field: 

only for faction, fixer, corpo, mappin, place, npc, custom_npc, node

Example :

```json
"context": [
	{
		"trigger": {
			"auto": {
				"name": "auto"
			}
		},
		"requirement": [["auto"]],
		"prop": 
		{
			"value": {
				"text": "Your faction is ##faction_name .Your fixer is ##fixer_faction_name",
				"values":{
					"playerfaction": {
						"type": "variable",
						"variable":"player",
						"key":"current_gang"
					},
					"fixer_faction_name": {
						"type": "fixer",
						"tag":"fixer_rogue",
						"prop":"Name",
						"searchprops":"Faction",
						"searchvalue":"faction_ncpd",
						"replace":"searchvalue",
						"context_value":"playerfaction"
					},
					"fixer_faction_tag": {
						"type": "fixer",
						"tag":"fixer_rogue",
						"prop":"Tag",
						"searchprops":"Faction",
						"searchvalue":"faction_ncpd",
						"replace":"searchvalue",
						"context_value":"playerfaction"
					},
					"faction_name": {
						"type": "faction",
						"tag":"faction_mox",
						"prop":"Name",
						"replace":"tag",
						"context_value":"fixer_faction_tag"
					}
				}
			}
		}
	}
]
```

Here we defined an prop context "playerfaction" and we take the defined variable "player_gang" that will return the player's current gang tag.

Then in another props, we will replace the "searchvalue" field by the value returned by the prop context "playerfaction" . So the mod will find an Fixer who have the Faction field that is equal to the player's current faction tag. Then it will display the Name of this fixer. Then from this fixer we will take the faction Name.

# Some Example

```json
"action": [{
        "name": "notify",
        "value": "Hello",
        "context": [
		{
			"trigger":{
				"condition01":{
					"name":"auto"	
				}
			},
			"requirement": [
				["condition01"]
			],
            "prop": {
                "value": {
                    "text": "##gangname are at x : ##posx  and y : ##posy",
                    "values": {
                        "gangname": {
                            "type": "faction",
                            "tag": "faction_mox",
                            "prop": "Name"
                        },
                        "posx": {
                            "type": "mappin",
                            "tag": "MyMappin",
                            "prop": "x"
                        },
                        "posy": {
                            "type": "mappin",
                            "tag": "MyMappin",
                            "prop": "y"
                        }
                    }
                }
            }
		}
    ]
}],
	
	
	"action": [{
        "name": "notify",
        "value": "Hello",
        "context": [
		{
			"trigger":{
				"condition01":{
					"name":"auto"	
				}
			},
			"requirement": [
				["condition01"]
			],
            "prop": {
                "value": {
                    "text": "##gangname are at x : ##posx  and y : ##posy",
                    "values": {
                        "gangname": {
                            "type": "faction",
                            "tag": "random",
                            "prop": "Name"
                        },
                        "posx": {
                            "type": "mappin",
                            "tag": "MyMappin",
                            "prop": "x"
                        },
                        "posy": {
                            "type": "mappin",
                            "tag": "MyMappin",
                            "prop": "y"
                        }
                    }
                }
            }
        }
		]
    }],

	possible result : 
	Mox are at x:200 y:300
	Scavengers are at x:200 y:300
	VoodooBoys are at x:200 y:300


	
	
	"action": [{
        "name": "notify",
        "value": "Hello",
        "context": [
			{
				"trigger":{
					"condition01":{
						"name":"auto"
					}
				},
				"requirement": [
					["condition01"]
				],
				"prop": {
					"value": {
						"text": "##text1 ##number1 ##text2",
						"values": {
							"text1": {
								"type": "random_text",
								"list": ["I eat ", "I stole ","I cook ","I throw "]
							},
							"number1": {
								"type": "random_number",
								"list": [1,2,6,65,85,9545,465,55,55654,4,777]
							},
							"text2": {
								"type": "random_text",
								"list": [" cookies", " muffins"," burgers"," banana"]
							}
						}
					}
				}
			}
		]
    }],


	possible result : 
	I eat 1 cookies
	I stole 465 muffins
	I cook 55654 burgers
	I throw 777 banana
```
