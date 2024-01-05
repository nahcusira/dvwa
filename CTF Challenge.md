PHP Fairy

Source code shows that we have to bypass two if conditions to get the flag. We know the `pass` variable. it's md5 of 
"admin1674227342" so: $pass = "0e463854177790028825434984462555"; 
First condition is this:
 ((((((((($_GET['pass'] == $pass)))) && (((($pass !== $_GET['pass']))))) || ((((($pass == $_GET['pass'])))) && ((($_GET['pass'] !== 
$pass))))))))
Summery of above condition is this:
 $_GET['pass'] == $pass && $pass !== $_GET['pass']
we know that first condition($_GET['pass'] == $pass) is using `equal operator`,
While second condition($pass !== $_GET['pass']) uses `Not Identical Operator`
We can bypass both condition by using "0" as input,
 "0" == "0e463854177790028825434984462555" => True
 "0e463854177790028825434984462555" !== "0" => True
Second condition is:
 (strlen($pass) == strlen($_GET['pass']))
or
 (32 == strlen($_GET['pass']))
So to bypass second one, we just have to use 32 zeros ( "0" * 32 )
Our final payload looks like this:
 00000000000000000000000000000000
 
![image](https://github.com/nahcusira/dvwa/assets/87233531/b4921ce5-b479-4ab6-b620-6f62a81c7416)

Hacking skill are optional

![image](https://github.com/nahcusira/dvwa/assets/87233531/8580f79b-bb79-4d60-8b44-0576d80a522e)

The article is about data theft with more than half due to love password, default password or stole n password but after looking through the website we don't see any place to log in then I think go to ringzer0's login page and try through 
default or guessable accounts and passwords and when trying admin/admin i got into admin account then i searched in admin account and found the flag in my profile this account

![image](https://github.com/nahcusira/dvwa/assets/87233531/e253d78f-9292-406e-b4ae-f75356685ca7)
