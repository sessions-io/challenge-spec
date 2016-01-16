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

This challenge is a single segment of a 30 day period where the person must run or walk 20 times. Each activity must be at least 25 minutes in legnth to count.

The sessions mobile runtime (SMRT) can load challenges in raw 'application/json' format from any http endpoint.
