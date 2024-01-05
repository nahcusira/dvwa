CSRF, or Cross-Site Request Forgery, is a type of web attack where an attacker exploits the trust of a website in a user's browser to execute unauthorized actions on behalf of the user. This is done by tricking a user into clicking a link or visiting a website controlled by the attacker while logged into a targeted website. The attacker then sends a request from the user's browser to the targeted website, which is treated as a legitimate request from the user. This can result in the attacker changing the user's settings, accessing sensitive information, or even making purchases on the user's behalf.

LOW

The script takes the user input and checks if the two passwords match, if they do the password is updated, if not the password is not updated. What we can see here is there is no protection against CSRF, such as Anti-CSRF token.

![image](https://github.com/nahcusira/dvwa/assets/87233531/dc5c8169-5d7c-48cd-bd44-f726f3e48417)

What we can see is it is a GET request and you can see the value of the new password has been changed to 123. You can also see the session ID of the user in the cookies.

![image](https://github.com/nahcusira/dvwa/assets/87233531/932a86e6-12f4-44e6-8643-93565b4abc15)

http://127.0.0.1/DVWA/vulnerabilities/csrf/?password_new=1234&password_conf=1234&Change=Change#

![image](https://github.com/nahcusira/dvwa/assets/87233531/6f56d6eb-4c78-4465-a9fb-95bacfb38553)

So just trick the user into clicking on the link above to be able to change the password to the password we want

MEDIUM

It is checking if the HTTP referer is in the server name and vice-versa. If yes the request goes ahead. A HTTP Referrer is a HTTP header field that identifies the address of the webpage (i.e. the URI or IRI) that linked to the resource being requested. By checking the referrer, the new webpage can see where the request originated.

![image](https://github.com/nahcusira/dvwa/assets/87233531/220343b7-dfc3-43c2-8da1-e0996b84ed4b)

When you send the request, you will get more information about the HTTP Referrer

![image](https://github.com/nahcusira/dvwa/assets/87233531/2fb42032-c826-47e9-b18f-c1dc522204ce)

http://127.0.0.1/DVWA/vulnerabilities/csrf/?password_new=1234&password_conf=1234&Change=Change#

So when before it is sent to the server, we just need to intercept the request and add the HTTP Referrer information and it has passed successfully.

![image](https://github.com/nahcusira/dvwa/assets/87233531/7416cba6-1e52-4699-8e18-8fd935739fab)

HIGH

This part of the site is secured in such a way that each version will have its own token so first we need to get the victim's token

![image](https://github.com/nahcusira/dvwa/assets/87233531/ba18b382-7a5e-4351-9d06-2eebb3232943)

To get token we write the following command in console: console.log(document.getElementsByName("user_token")[0].value)

![image](https://github.com/nahcusira/dvwa/assets/87233531/61a5bd7e-035c-43b0-95fe-d1b0786697d6)

http://127.0.0.1/DVWA/vulnerabilities/csrf/?password_new=password&password_conf=password&Change=Change&user_toke
