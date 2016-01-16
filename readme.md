## Challenge Spec 0.1.0

Challenges have a standard header that ensures runtime compatiblity:

header format:

	{
		"sessions": "0.1.0"
	}

The next layer defines a name and description. This should describe the specifics of the challenge in plain english so people can read & understand the requirements.

	{
		"name": "Fitstar 30 day challenge",
		"summary": "perform 20 sessions in 30 days"
	}
	
The segments array defines the challenge itself:

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

This example is a single segment. Multiple segments would need to satisfied linearly in order to compelte the challenge. The segment says the person needs to run or walk for more than 25 minutes at least 20 times within a 3 day window.

### Loading 

The sessions mobile run-time (SMRT) is capable of loading challenges straight from http endpoints. The Sessions mobile apps for iOS and Android will automatically load challenges when tapping on "https://sessions.io/s/*" links from any app or website.

### Example Challenges

[Couch to 5k](https://sessions.io/s/c25k)

[365 miles in 365 days](https://sessions.io/s/365in365)
