# Scripting Basics

> Want to create your own quest, datapacks, entity ? This is the place for you

# Scripting

You can create your own missions and share it with the community. Also you can bound and mix mission with dialogs, places, npcs, interactions and more.

Check the in-game Editor under CM Menu-> Tools-> Editor

# Trigger and action system

**What is Trigger**<br>
- A "Trigger" is a condition that needs to be fulfilled to trigger something.

**Example**:
```json
"playerposition": {
		    "name": "entity_at_position",
		    "x": -1530,
			"y": 986,
         	"z": 23,
		    "range": 20,
		    "tag": "player"
    }		
```

**Requirement**

A "Trigger Requirement" is a logical order for a bunch of triggers like "Or and AND"

**Example**:

Let's say you have TriggerA, TriggerB and TriggerC. You want that the condition is fullfilled when TriggerA AND TriggerB are fullfilled OR TriggerC is fullfilled

this can be translated in JSON as :

```json
"requirement": [
     ["TriggerA","TriggerB"],["TriggerC"]
],
```

like 

```json
"requirement": [
     ["TriggerA" AND "TriggerB"] OR ["TriggerC"]
],
```

**Action**

An "Action" is a script engine action that will perform some things like spawn a NPC, move it...

**Example**:

```json
{
		"name": "subtitle",
		"title": "Some bonks attack the afterlife, show them some respect !",
		"type": 1,
		"target": "player",
		"speaker": "Rogue",
		"persistent": false,
		"duration": 3
}
```

**Execution**

When the **TRIGGERS** conditions are met according to the **REQUIREMENTS**, scripting engine will perform the corresponding **ACTIONS**.

For example,

if (REQUIREMENT)<br>
the player arrives to a position (TRIGGER)<br>
summon some enemies and make them hostile (ACTION x2).<br>

# Logic

**Conditional statement**

- Action "If" will test a trigger then depending on the result, will run if_action list if the condition is fulfilled or else_action if the condition is not fulfilled;
- Action "goto" can jump to another action index; (as GOTO)
- Action "for" will repeat a bunch of actions;

**Logic operation**

- Trigger "testFor" will test a bunch of triggers together with AND or OR logic;
- Trigger "compare" will compare an expected result to a trigger (can be used to make a NOT operation of triggers);

**Function definition**

- Action "function" can define a list of actions, and allow other actions in this file call the list to execute. A function doesn't have any trigger, it's just a list of actions in another function file;
- Action "event" can execute a world event (like ambush or maxtac intervention). It's a list of actions with triggers and requirement in another event file；
- Action "do_random_event" and "do_random_function" call random event and function in list;

# 🔥Want more ?
- [Creating Content with CyberScript](creating-content-with-cyberscript.md)

?>😋 **Useful Link**<br>&nbsp;Datapack flag list: [Flag List](datapack-flag.md)
