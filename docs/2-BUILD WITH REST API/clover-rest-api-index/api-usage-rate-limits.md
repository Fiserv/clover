---
title: "Work with API usage and rate limits"
slug: "api-usage-rate-limits"
excerpt: ""
hidden: false
metadata: 
  description: "Learn about Clover’s API usage and rate limits, including per-second and concurrent rate limits, best practices to avoid 429 HTTP error messages, and how to respond to them"
  image: 
    - "https://files.readme.io/7183372-clover-symbol-green_2.png"
    - "clover-symbol-green (2).png"
    - 144
    - 144
    - "#228800"
  robots: "index"
createdAt: "Fri Sep 07 2018 02:58:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 04:16:23 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!-- This page has content shared with the partner docs. If you update\nthis page, be sure to check if the same change applies to the partner \ndoc. -->"
}
[/block]


[block:html]
{
  "html": "<!--JIRA DS-3009; Region pill icon added to topic on 3.22.2023-->\n\n<div class=\"container\">\n<!--US-->\n  <div class=\"pill\">\n    <div class=\"label\">United States</div>\n  </div>\n<!--Canada-->\n  <div class=\"pill\">\n    <div class=\"label\">Canada</div>\n</div>\n  <!--Europe-->\n  <div class=\"pill\">\n    <div class=\"label\">Europe</div>\n</div>\n     <!--Latin America-->\n  <div class=\"pill\">\n    <div class=\"label\">Latin America</div>\n</div>\n</div>\n\n<style>\nbody {\n  font-family: \"Segoe UI\", \"Roboto\",\n    \"Segoe UI Symbol\";\n}\n.container {\n  align-items: center;\n  min-width: 10%;\n  text-align: left;\n   overflow: auto;\n}\n/*Pill format*/\n.pill {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n\n}\n/*Text positioning inside the pill*/\n.pill,\n.pill__addon {\n  display: inline-block;\n  box-sizing: border-box;\n  padding: 0px 10px;\n  border-radius: 10px;\n  position: relative;\n  box-sizing: border-box;\n  height: 1.5rem;\n}\n/*Text format inside the pill*/\n.pill .label,\n.pill__addon .label {\n  font-style: normal;\n  font-weight: normal;\n  font-size: 0.70rem;\n  color: #fff;\n  display: inline-block;\n  vertical-align: middle;\n \n}\n</style>"
}
[/block]


There are four different rate limits placed on Clover REST API usage. For consistent access to the API services, ensure that your apps adhere to the rate limits and best practices.

# Rate limits

Rate limits are set for the number of new API requests your apps can make per second.

| Level     | Per-second rate limit |
| :-------- | :-------------------- |
| Per app   | 50                    |
| Per token | 16                    |

# Concurrent rate limits

In addition to rate limiting, we maintain concurrent rate limiting to better control multiple retry requests to CPU-intensive API endpoints. Concurrent rate limits are set for the number of in-progress API requests your apps can make at the same time.

| Level     | Concurrent rate limit |
| :-------- | :-------------------- |
| Per app   | 10                    |
| Per token | 5                     |

For instance, if the concurrent rate limit has been set to five, you can make up to five running API requests at the same time. While the server is responding to these five requests, a sixth request will return to a 429 HTTP Too Many Requests\` error message.

# 429 HTTP error messages

You receive a 429 `Too Many Requests` error message when the number of API requests made by your app exceeds the rate limits.

## Best practices to avoid 429 HTTP error messages

Use the following best practices to reduce interruptions due to 429 HTTP error messages:

- Use [Webhooks](doc:webhooks) to avoid constant polling for updates.
- Cache your data for storing specialized values or for rapidly reviewing large data sets.
- Query with the `modifiedTime` filters to avoid re-polling unmodified data.
- Stagger requests to multiple merchants to avoid bursts of high traffic volume.
- Backfill data only during non-peak business hours. Also, use our <a href="https://github.com/clover/export-api-examples" target="_blank">Export API</a> to backfill orders or payments data older than two months old.

## Types of 429 HTTP error messages

### X-RateLimit-{type}

The following table can help you identify the type of 429 HTTP error message you are receiving in the response header.

| Level                  | Response header                         |
| :--------------------- | :-------------------------------------- |
| Per app                | `X-RateLimit-crossTokenLimit`           |
| Per token              | `X-RateLimit-tokenLimit`                |
| Per app (Concurrent)   | `X-RateLimit-crossTokenConcurrentLimit` |
| Per token (Concurrent) | `X-RateLimit-tokenConcurrentLimit`      |

### retry-after

Concurrent rate limit responses also include a `retry-after` header. The value of this header is the number of seconds your app must wait before making another request. If a request is made before this time, the waiting period increases. 

The following example shows a `retry-after` interval of 21 seconds.

```
retry-after: 21
```

## Respond to 429 HTTP error messages

Design your app with necessary fallbacks to gracefully handle 429 HTTP error messages.

- In response to a 429 message, your app must pause for one second before making another API request.
- If you continue to receive 429 messages, your app must exponentially increase the time between API requests until you receive a successful response.

The following example demonstrates exponential backoff.

```python Exponential backoff Python sample
max_attempts = 10
attempts = 0

while attempts < max_attempts:
	# Make a request to Clover REST API
	response = requests.get(request_url, headers = {"Authorization": "Bearer " + api_token})
	
	# If not rate limited, break out of while loop and continue with the rest of the code
	if response.status_code != 429:
		break
	
	# If rate limited, wait and try again
	time.sleep((2 ** attempts) + random.random())
	attempts = attempts + 1
```
