# Create custom phone conversation

> In this page, you will be able to follow an small tutorials about making your own phone conversation in JSON and play it with Cyberscript.

**It will be an long but fully complete tutorial. At the end you will be able to see the described phone conversation.**

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
<br>We will create .... Phone Dialog !

# 💬 Create a phone conversation

**📂 Setup the folder**

First : in your datapack folder, create a folder named "phone_dialog". It will contain every phone_dialog script of your datapack. Logic !

In this folder, create a JSON text file, like for example : amazingPhoneDialog.json

Open it with your favorite text editor.

**💀 Write the phone conversation skeleton**

Now we have a blank page. But don't worry, we will fill it step by step.

Let's talk about phone conversation structure :

A phone conversation is :
- A Tag
- A speaker
- a unlock field
- conversation field

Now let's make it in JSON :

```json

	{
       
        "tag": "amazingPhoneDialog",
		"unlock": true,
		"speaker": "Judy Alvarez",
		"conversation": []
    }

```

This is the skeleton of our phone dialog. For resume what you see below : The choice is have "Judy Alvarez" as speaker, it's unlocked by default,

Cyberscript know it as "amazingPhoneDialog".
it have a empty conversation list.

Lets fill it with one conversation :

```json

	{
       
        "tag": "amazingPhoneDialog",
		"unlock": true,
		"speaker": "Judy Alvarez",
		"conversation": [
		
			{
				"tag": "judy_phone_01",
				"name": "Think about you <3",
				"unlock": true,
				"message": []
			
			}
		
		
		
		
		]
    }

```

Here you have an new object : connversation. Let's describe it !

```json
[

			{
				"tag": "judy_phone_01",
				"name": "Think about you <3",
				"unlock": true,
				"message": []
			
			}
	
]
```

It contains another bunch of field : 

- "tag":tag of the conversation
- "name": the name who will be displayed in the conversation list journal 
it will be like


"Judy Alvarez"
		--->	"Think about you <3"
								---> (sms conversation here)
								
- "unlock": determine if the conversation is unlocked by default
- "message": list of the SMS by order.

Ok, we have an contact, an conversation, now fill that connversation with message !


```json
{
	"tag": "amazingPhoneDialog",
	"unlock": true,
	"speaker": "Judy Alvarez",
	"conversation": [
		{
			"tag": "judy_phone_01",
			"name": "Think about you <3",
			"unlock": true,
			"message": 
			[
				
				{
					"tag": "judy_phone_01_msg_01",
					"text": "Hey you, I was thinking about Johnny",
					"sender": 0,
					"unlock": true,
					"readed": false,
					
					"choices": [
						
						{
								"tag": "judy_phone_01_chc_01",
								"text": "Why do you think of him ?",
								"unlocknext":"judy_phone_01_msg_02",
								"trigger":{
									"condition01":{
										"name":"auto"
										
									}
								},
								"requirement": [

									["condition01"]
									

								],
								"action_bypassmenu_execution":false,
								"action":[
								
									
								]
								


						},
						
						{
								"tag": "judy_phone_01_chc_02",
								"text": "I'm sure it wasn't good",
								"unlocknext":"judy_phone_01_msg_03",
								"trigger":{
									"condition01":{
										"name":"auto"
										
									}
								},
								"requirement": [

									["condition01"]
									

								],
								"action_bypassmenu_execution":false,
								"action":[
									
									
								]
								


						},
					]
				},
						
						
				{
					"tag": "judy_phone_01_msg_02",
					"text": "Why do you think of him ?",
					"sender": 1,
					"unlock": false,
					"readed": false,
					"unlocknext":"judy_phone_01_msg_04",
					"choices": [
						
						
						
					]


				},
				{
					"tag": "judy_phone_01_msg_03",
					"text": "I'm sure it wasn't good",
					"sender": 1,
					"unlock": false,
					"readed": false,
					"unlocknext":"judy_phone_01_msg_05",
					"choices": [
						
						
						
					]


				},
				
				
				{
					"tag": "judy_phone_01_msg_04",
					"text": "I don't know.. I was wondering how that guy become what he is now. Nevermind, see you later !",
					"sender": 0,
					"unlock": false,
					"readed": false,
					"unlocknext":"",
					"choices": [
						
						
					]


				},
				
				{
					"tag": "judy_phone_01_msg_05",
					"text": "Look like it's not a topic you want speak, sorry about that ! Talking later !",
					"sender": 0,
					"unlock": false,
					"readed": false,
					"unlocknext":"",
					"choices": [
						
						
						
					]


				},
				
			]


		},
	]
}
```



Ok ! Many things appears here ! But don't worry, let's dive in step by step.


First, let's take a look about message structure :

```json



{
					"tag": "judy_phone_01_msg_01",
					"text": "Hey you, I was thinking about Johnny",
					"sender": 0,
					"unlock": true,
					"readed": false,
					
					"choices": [
						
						{
								"tag": "judy_phone_01_chc_01",
								"text": "Why do you think of him ?",
								"unlocknext":"judy_phone_01_msg_02",
								"trigger":{
									"condition01":{
										"name":"auto"
										
									}
								},
								"requirement": [

									["condition01"]
									

								],
								"action_bypassmenu_execution":false,
								"action":[
								
									
								]
								


						},
						
						{
								"tag": "judy_phone_01_chc_02",
								"text": "I'm sure it wasn't good",
								"unlocknext":"judy_phone_01_msg_03",
								"trigger":{
									"condition01":{
										"name":"auto"
										
									}
								},
								"requirement": [

									["condition01"]
									

								],
								"action_bypassmenu_execution":false,
								"action":[
									
									
								]
								


						},
					]
				},
				
				
				
	```



It contains fields : 

- "tag":tag of the conversation
- "text": the text of the message 
- "sender" : type of the message. 0 is received message to V, 1 is sended message from V.
- "unlock": Message is unlocked by default.
- "readed": Message is readed by default.
- "choices": An list of possible answers by V.

Let's talk about choices(answers) structures now : 

```json

		"tag": "judy_phone_01_chc_01",
		"text": "Why do you think of him ?",
		"unlocknext":"judy_phone_01_msg_02",
		"trigger":{
			"condition01":{
				"name":"auto"
				
			}
		},
		"requirement": [

			["condition01"]
			

		],
		"action_bypassmenu_execution":false,
		"action":[
		
			
		]
		


},

```


It contains fields : 

- "tag": tag of the answer
- "text": the text of the answer
- "unlocknext" : what message(by tag) it will unlock when you click on it ?
- "trigger": triggers of the message.
- "requirement": requirements order for the triggers.
- "action" : list of action that will be performed when you click on the answer.
- "action_bypassmenu_execution": by default, Cyerscript only execute actions list when you are not in menu. Put that field to true will bypass this restriction.


Of we have it all. Now let's resume our conversation ("amazingPhoneDialog"):


You talk to "Judy Alvarez". 
It's topic named "Think about you <3".("judy_phone_01")

When you click on it, it will display the message : 

"Hey you, I was thinking about Johnny" ("judy_phone_01_msg_01")

then V have 2 possibles answers : 
- "Why do you think of him ?"("judy_phone_01_chc_01") : click on it will unlock :
	- V's answer message "Why do you think of him ?" ("judy_phone_01_msg_02")
	- Judy's message "I don't know.. I was wondering how that guy become what he is now. Nevermind, see you later !" ("judy_phone_01_msg_04")
	
- "I'm sure it wasn't good"("judy_phone_01_chc_02") : click on it will unlock : 
	- V's answer message "I'm sure it wasn't good"("judy_phone_01_msg_03")
	- Judy's message "Look like it's not a topic you want speak, sorry about that ! Talking later !" ("judy_phone_01_msg_05")


# Make an interact that will call your phone dialog in an sms popup !

Phone conversation are called through an action or directly in conversation jorunal menu if unlocked.



you can follow this tutorial to make an interact : [How to make an custom Interact ?](create-custom-interact.md)

There is a small example that will work :

```json
{
	"name": "Test My Amazing Phone dialog",
	"tag": "myamazinginteractphonedialog",
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
            "name": "phone_notification",
            "title": "Judy Alvarez",
            "desc": "Think about you <3",
            "duration": 8,
            "conversation": "judy_phone_01"
        }, ]
}
```


You will have an sms notification, open the dialog will show you an sms popup with your dialog in it ! 

# Test your interact and your phone dialog !

Copy your whole datapack folder in (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/

so it should be in our case (GOG or steam game folder)/Cyberpunk 2077/bin/x64/plugins/cyber_engine_tweaks/mods/quest_mod/json/datapack/myAmazingDatapack

the structure of the folder should be


```structure
📂myAmazingDatapack
├── 📃 desc.json
├── 📁 phone_dialog
|    └── 📃 amazingPhoneDialog.json
└── 📁 interact
     └── 📃 myamazinginteractphonedialog.json
```

Select the datapack "myAmazingDatapack" in cycle interact ([What are you talking about ?](cet-key-binding.md))

then hit the key for use your interact. Dialog should show !

<h2>Enjoy ! 🤠</h2><hr>

# 🔥 Want more ?
- [Creating Content with Cyberscript](creating-content-with-cyberscript.md)