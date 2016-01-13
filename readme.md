## Challenge Specification v0.1

Challenges have a standard header that ensures runtime compatiblity. The header format has a version number and a special token that identifies it as a challenge.

header format: 

	{ 
		"magic": "challenge",
		"version": "0.1.0",
	}

The next layer of a challenge identifies a name and description. This is useful when a challenge is inside a repository and needs to be found in some way. It also helps the author summarize the challenge in plain english.

It is recommended to use your own company, blog or personal name in the title to help people locate your challenge and connect it back to your brand.

	{ 
		"name": "Fitstar 30 day challenge",
		"summary": "perform 20 sessions in 30 days"
	}

The next layer defines an array of requirements for completing the challenge.
You can compose multiple entries to create more complex challenges. Try to keep challenges as simple as possible as it makes them difficult to 
understand.

The simplest challenge is then: 

	{ 
		"challenge": [ 
			{ 
				"goal": { 
					"count": 20,
					"days": 30
				}
			}
		]
	}

The "goal" section of a challenge defines the conditions that must be met for the challenge to be completed. This says you must complete 20 sessions in 30 days.

The "filter" seciton defines addition constraints to filter sessions on. This allows you to provide more detail on exactly what must be completed in each session. You can filter by both activity time and duration of the session.

	{ 
		"challenge": [
			{
				"goal": { 
					"count": 20,
					"days": 30
				},
				"filter": { 
					"type": [ 
						"run",
						"cycle"
					],
					"min_duration": 15
				}
			}
		]
	}

In this example, running and cycling count, but walking doens't. Also, if the session does not last for at least 15 minutes, the session will not count towards the goal. The "Before" and "After" messages will get sent to the user hwen they accept the challenge and once they complete it. It will use the profile picture and username associated with the account specified by "account". The runtime might cache this data, but it should strive to use the most updated data when the message is fired.

Here is a completed JSON for the entire challenge document: 

	{ 
		"magic": "challenge",
		"version": "0.1.0",
		"name": "Fitstar 30 day challenge",
		"summary": "perform 20 sessions in 30 days",
		"challenge": [
			{
				"goal": { 
					"count": 20,
					"days": 30
				},
				"filter": { 
					"type": [ 
						"run",
						"cycle"
					],
					"min_duration": 15
				}
			}
		]
	}

This could be stored in a database system or on disk. The runtime decides how to manage challenges. 
 
