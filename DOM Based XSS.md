DOM XSS (Cross-site scripting) is a type of web vulnerability that occurs when an attacker is able to inject malicious code into a web page, and the code is executed by the victim's browser in the context of the victim's session. 

Unlike other forms of XSS, DOM XSS attacks occur entirely on the client-side and are not dependent on server-side vulnerabilities. The attacker can inject malicious code into the page by exploiting vulnerable JavaScript code that takes user input without proper sanitization and validation.

When the user interacts with the page, the injected code can modify the page's DOM (Document Object Model) to steal sensitive information such as login credentials, session tokens, and personal data. The attacker can also use the compromised session to perform unauthorized actions on behalf of the victim, such as changing their account settings, making purchases, or accessing confidential data.

LOW

Since there is no any protection method, we can insert any payload we want 

?default=<script> alert("You have been hacked!"); </script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/255e48c6-7f02-4354-85db-469ccfe0ab51)

MEDIUM

Checks if there is an input in the URL query parameter "default". If the input exists and is not null, the code assigns it to a variable called "$default". It uses the "stripos" function to check if the string contains the "<script" tag, which is commonly used in XSS attacks. If the "<script" tag is found in the input, the code redirects the user to a default page "English" by sending a "Location" header in the response, thus preventing the malicious code from executing on the client-side. but instead of using the <script> tag, we can use the <image> tag to perform the attack

?default=</select><img src=X onerror="alert('you have been hacked!')">

![image](https://github.com/nahcusira/dvwa/assets/87233531/d1517c76-7b4c-44f5-97f9-fe6347fa4e6d)

HIGH

Checks if there is an input in the URL query parameter "default". If the input exists and is not null, the code performs a security check to ensure that the input is one of the allowed languages - French, English, German, or Spanish. Uses a "switch" statement to check if the input matches any of the allowed languages. If the input matches one of the cases in the switch statement, the code continues executing. If the input does not match any of the cases, the code redirects the user to a default page "English" by sending a "Location" header in the response, thus preventing potential security risks associated with allowing unauthorized input. The fragment section of a URL (anything after the # symbol) does not get sent to the server and so cannot be blocked.

#?default=<script> alert("You have been hacked!"); </script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/4863ad9d-47d4-4a61-ab9f-d43e15969974)
