# Internal

- The challenge is a PHP code review where the goal is to bypass some restrictions to achieve Server Side Request Forgery (SSRF) to retrieve the flag
- We need to fetch the URL: http://localhost/flag.php or any similar domain that resolves to 127.0.0.1 or ::1
- The restrictions are
	1. The URL has to start with http://egcert or https://egcert
	2. The URL cannot contain @ characters, so we cannot use the http://egcert:anypassword@localhost trick

- Tried using some payloads with the "egcert" prefix followed by encoded CRLF or LF or null bytes and finally localhost or http://localhost but none of them was parsed as localhost by the fetch function call
- There is an awesome tool [1u.ms](https://github.com/neex/1u.ms) which is useful for SSRF-related vulnerabilities
- It has a public server that can be used to generate domain names that resolve to whatever IP someone might want and it also has other advanced options
- Explored its usage options and luckily it has an option for adding prefix

Payload:

![Testing the payload using host command](Host.png "Testing the payload using host command")

Flag:
![Flag](Flag.png "Flag")
