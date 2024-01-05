Explain about Stored XSS? What is the difference between XSS techniques we learnt?

Stored XSS (Cross-Site Scripting) is a type of web application vulnerability where an attacker injects malicious scripts or code into a web application, which is then stored and displayed to other users who access the same page. The attack occurs when the application does not properly validate or sanitize user input, allowing the attacker to inject and store malicious code that can be executed by other users' browsers. The key difference between Stored XSS and other types of XSS attacks, such as Reflected XSS and DOM-based XSS, is the way in which the malicious script is delivered to users. In Stored XSS, the attacker injects the malicious script directly into the application's database, which is then retrieved and displayed to all users who access the affected page. This makes Stored XSS particularly dangerous, as the attack is persistent and affects all users who access the affected page, not just the user who initiated the attack. In Reflected XSS, the attacker injects the malicious script into a URL or form input field, which is then reflected back to the user's browser in the application's response. This type of XSS attack is less dangerous than Stored XSS, as it requires the user to click on a link or submit a form in order to execute the malicious script. In DOM-based XSS, the attacker injects the malicious script into the Document Object Model (DOM) of the web page, which is then executed by the user's browser when certain events are triggered. This type of XSS attack is also less dangerous than Stored XSS, as it is limited to a specific user and does not affect other users who access the same page. Overall, Stored XSS is considered the most dangerous type of XSS attack, as it can have far-reaching consequences and is often difficult to detect and mitigate.

LOW

There isn't any input checking step so we can do it easily with the basic payload:

<script>alert("You have been hacked!");</script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/63aa32c9-897a-4882-841a-23723c940b59)

MEDIUM

First block is for performing input sanitization on message field. This block contains two php functions for performing input sanitization. First one is strip_tags(). It removes all html tags from the message field before storing them in database. Second function is htmlspecialchars(). It converts all the bad characters like &, ", ', > and < in their equivalent HTML character encoding so they won’t remain in their original form when they reflect back in the browser. You can confirm it by checking the page source.

So, in message field there are two levels of sanitization. Firstly strip_tags() function removes all the HTML tags from the message field and even if some text containing quotes or bad characters passes through this function, htmlspecialchars() will definitely encode them into equivalent HTML characters. So our XSS payload becomes useless. From here we conclude that the message field is completely secure and we cannot inject any XSS payload into it. This was the reason when we gave <script>alert()</script> as our input in message field it only showed alert() text in page source because strip_tags() function 
removed <script> and </script> tags from it.

Second block is for performing input sanitization on Name field. It uses just one function for performing input sanitization. The function is str_replace(). Here this function is replacing all the occurrences of <script> tag with null or blank character. We can use this field to inject our XSS payload. Since this field is replacing all occurrences of <script> tag so we cannot use any XSS payload which contains <script> tag in it. 

We can bypass this security by using some other payloads which do not contain <script> tags in it and we can use script tag with different casing enabled. Like we can use <Script> or <scRiPt> or <ScRiPt> in place of <script>. Let us inject it in Name field. So when I tried to enter this payload in Name field it does not accept all the characters of our payload because it has some client side restriction. The restriction is, that a user can enter a maximum of 10 characters in the name field. Since it is a client-side restriction so it can be bypassed very easily.

<scRipt> alert("You have been hacked!"); </scRipt>

![image](https://github.com/nahcusira/dvwa/assets/87233531/01d33c3d-5499-46f3-93b6-e2459c71663f)

![image](https://github.com/nahcusira/dvwa/assets/87233531/42d58586-e094-4fc3-8c01-9a83d390202d)

![image](https://github.com/nahcusira/dvwa/assets/87233531/ccaf3826-b5fb-4a8c-8181-37de0a022319)

HIGH

According to source code block 1 is accepting input of Message field and performing sanitization on it. Again this code is using strip_tags() and htmlspecialchars() functions to sanitize user input as we have seen in medium security. So there is no chance to inject XSS payload in this field because they will be filtered by these functions.

Block 2 is for performing input sanitization on Name field. It uses just one function for performing input sanitization. The function is preg_replace(). Here this function replaces every occurrences of <script> tag irrespective of their cases with null or blank. So here every XSS payload which includes <script> tag into it will be useless. 

To bypass this, we'll do the same step in the medium section but have to use some other XSS payload that doesn't contain the <script> tag in it.

<img src=X onerror="alert('you have been hacked!')">

![image](https://github.com/nahcusira/dvwa/assets/87233531/8148c935-bcdc-45ae-8e3c-50b3db5a30dc)

![image](https://github.com/nahcusira/dvwa/assets/87233531/fd897f59-bc68-41ab-ad06-da1402996156)

![image](https://github.com/nahcusira/dvwa/assets/87233531/67226dc1-9775-49a5-a34a-074716a526c5)
