## Challenge Specification v0.1

Challenges have a standard header that ensures runtime compatiblity. The header format has a version number and a special token that identifies it as a challenge.

header format:

	{
		"sessions": "0.1.0"
	}

The next layer of a challenge identifies a name and description. This is useful when a challenge is inside a repository and needs to be found in some way. It also helps the author summarize the challenge in plain english.

It is recommended to use your own company, blog or personal name in the title to help people locate your challenge and connect it back to your brand.

	{
		"name": "Fitstar 30 day challenge",
		"summary": "perform 20 sessions in 30 days"
	}

The next layer defines an array of sequeuntial segments that make up the challenge:

	{
		"segments": [
			{
				"type": "sessions",
				"count": 20,
				"days": 30,
				filter: {
					"types": [
						"run",
						"walk"
					],
					"minutes": 25
				}
			}
		]
	}

In this example, running and cycling count, but walking doens't. Also, if the session does not last for at least 15 minutes, the session will not count towards the goal. The "Before" and "After" messages will get sent to the user hwen they accept the challenge and once they complete it. It will use the profile picture and username associated with the account specified by "account". The runtime might cache this data, but it should strive to use the most updated data when the message is fired.

This could be stored in a database system or on disk. The runtime decides how to manage challenges.
The sessions mobile runtime (SMRT) can load challenges in raw 'application/json' format from any http endpoint.

### Example Challenges

[Couch to 5k](https://sessions.io/s/c25k)
[365 miles in 365 days](https://sessions.io/s/365in365)
