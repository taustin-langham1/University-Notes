


## What is code injection?


malicious code is injected into an application which is then interpreted or executed

attacks classed as code injection or arbitrary code execution


## What is SQL injection?


this is availability loss (a) / confidentiality loss (b, c) / Integrity loss (d)

1. SELECT * FROM users WHERE `name`='$name' // name not 'sanitized', can exploit:
	a) $name = "Bob'; DROP TABLE users; --
	
	b) $name = "Bob' OR 1=1; --"
	c) $name = "' UNION SELECT a, b FROM sensitive_data;--"

	d) SELECT * FROM users WHERE `name`='Bob';
	INSERT ('Eve') INTO users; --'
	SELECT * FROM users WHERE `name`='Bob';
	UPDATE users SET `name`='Eve'; --'



## How are SQL injections mitigated?

1. general rule: do not trust any user provided input - assume that it may be in an intentionally malicious format 

2. Use prepared statements to separate the SQL logic and the data
	inputs to the query

![[Pasted image 20250513155153.png]]

this is better! 

## what is shell injection?

1. An application may need to execute an application on a shell. a website that offers image/video transcoding services might use ffmpeg for example.
2. so similar techniques are used to inject into the shell as sql does.
	1. • Command separators:
		• & (Background Execution)
		• && (Logic AND)
		• | (Pipe)
		• || (Logic OR)
		• ; (Command Separator)
		• \n (Newline)
			

	2. Analysis? remote code execution, exfiltrate system information
	3. Mitigation
		1. do not use the input on the shell, only allow user input that cannot inject a command
			1. e.g., numeric input

## what is cross site scripting? (XSS)

1. Persistent XSS: analysis
	1. 1. Adversary provides malicious input to a website that stores it
	2. The website then displays this content to other users

	• Consider all input provided by
	users to be untrusted
	• Sanitize all untrusted input before
	using it

	1. Reflected XSS: analysis
		1. User clicks a malicious
		link with attack encoded into it,
		which injects the attack into the
		visited website

	2. DOM based XSS analysis
		1. Adversary injects attack into running application