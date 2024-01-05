DOM XSS in jQuery anchor href attribute sink using location.search source

Go to the feedback page to analyze the back button, we see that it will take the value of the returnPath parameter from the search URL parameter and set the href attribute value of the backLink tag to return to the previous page

![image](https://github.com/nahcusira/dvwa/assets/87233531/bc0ae089-915d-4124-bf46-60d9d3bfecd0)

try to replace '/' on URL with 'abcd123' the value of href changes and it will lead to an unknown page

![image](https://github.com/nahcusira/dvwa/assets/87233531/85b903f4-8b26-4034-a5c1-8abdfa00a1e8)

![image](https://github.com/nahcusira/dvwa/assets/87233531/d9291953-1076-46dc-87c7-2791ff624894)

thereby we determine that simply changing the '/' value on the URL we can navigate the back button to the result we want.
javascript:alert(document.cookie)

![image](https://github.com/nahcusira/dvwa/assets/87233531/d3ee52e9-ae5b-4ab8-8412-f85c2e6a8419)

Reflected XSS into attribute with angle brackets HTML-encoded
search 1 any text 'abcd123' then check the value se is received by the website and send the request with what value, we see 
value="abcd123" that will be the value that the website will receive and do

![image](https://github.com/nahcusira/dvwa/assets/87233531/cbec7c9b-233e-485d-88ba-d48bccd2dd4e)

through which we only need to change the value we enter so that the website will perform the action we expect to succeed. For 
example, we will make the website execute the command to display cookies when we point the mouse pointer in the search box 
by payload:
"onmouseover="alert(document.cookie)

![image](https://github.com/nahcusira/dvwa/assets/87233531/fd6f818f-47cf-421b-820d-901217ec0bfb)

Stored XSS into anchor href attribute with double quotes HTML-encoded
we will go to any post and leave a random comment, then we see that when we leave a comment and post it on someone else, when we click on our name, we will be redirected to another website that we left in the website section that we have filled out above through which we see that we only need to change the value in the website section when we leave a comment and we can perform the action we want when we click on our name. the website will take the value in the href and execute
javascript:alert(document.cookie)

![image](https://github.com/nahcusira/dvwa/assets/87233531/ebf41a9c-3e7e-4dde-b3e7-6f8c55eb5afb)

![image](https://github.com/nahcusira/dvwa/assets/87233531/4e0ab3b2-6572-471a-985e-daa29816e1d4)

![image](https://github.com/nahcusira/dvwa/assets/87233531/bbfd6d27-f231-40f5-ad1d-7dfabde8515e)

![image](https://github.com/nahcusira/dvwa/assets/87233531/a0ff6ff6-0dfc-40d2-a05e-d1ef19f364d2)

![image](https://github.com/nahcusira/dvwa/assets/87233531/124aed7d-5977-4cc9-afa1-043fa2cd5e53)
