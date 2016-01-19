## Challenge Spec 0.1.0

Challenges are specified in the following JSON format which describes a device/vendor/platform independent set of constraints that a person must meet in order to qualify as "complete". Our open source [Android](https://github.com/sessions-io/smrt-android) and [iOS](https://github.com/sessions-io/smrt-ios) apps load challenges in this format and track completion automatically by connecting with wearable fitness devices.

Challenges have a standard header that ensures runtime compatiblity:

header format:

	{
		"sessions": "0.1.0"
	}

Next, the challenge has a name, and a summary in words:

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

This example is a single segment. Multiple segments would need to satisfied linearly in order to compelte the challenge. If a segment needs to be restarted, the whole challenge is restarted. The segment says the person needs to run or walk for more than 25 minutes at least 20 times within a 30 day window.

### Loading 

The open source apps for [iOS](https://github.com/sessions-io/smrt-ios) and [Android](https://github.com/sessions-io/smrt-android) can fetch and load challenges from any URL.
Challenges should be available on http(s) endpoints with content-type "application/json".

### Hosted Example Challenges

[Couch to 5k - https://sessions.io/s/c25k](https://sessions.io/s/c25k)

[365 miles in 365 days - https://sessions.io/s/365in365](https://sessions.io/s/365in365)
