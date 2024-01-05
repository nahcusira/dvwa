SQL Direct

Use query of PostgreSQL show all information in flags table we got flag

![image](https://github.com/nahcusira/dvwa/assets/87233531/1714e5b0-a11e-4fe7-bc59-b01960906ecd)

![image](https://github.com/nahcusira/dvwa/assets/87233531/7a220999-8851-49bb-a844-6e775e2fbf22)

SQLiLite

First login with any username and password we will get the message "Login failed." and SQL query: SELECT * FROM users WHERE name='.....' AND password='.....' We just need to add 1' or true-- to the username then we have successfully logged in. But we won't get the flag, it's hidden, just press F12 and check

![image](https://github.com/nahcusira/dvwa/assets/87233531/3bcb7bec-d0fb-4c5b-8c39-2beee623a603)

![image](https://github.com/nahcusira/dvwa/assets/87233531/8cf0c6fa-2451-40dc-ae94-e86ae22425b6)

Inj3ction Time

Intercepted the request using burpsuite and copied the request to a file so that i could ran SQLMap using it

![image](https://github.com/nahcusira/dvwa/assets/87233531/460d975a-0814-4506-8e65-64d1e35a294d)

sqlmap -r id.req --batch -t 10 --dbs mysql

After a few seconds it came back with results that it had found three different techniques that it can use to exploit the SQL Injection

![image](https://github.com/nahcusira/dvwa/assets/87233531/90ea9252-3371-4cbf-8fb7-471a0bdd74ab)

sqlmap -r id.req --batch -t 10 --dbs mysql --dump

then get the whole database with --dump command and we got flag

![image](https://github.com/nahcusira/dvwa/assets/87233531/dcaf272c-b821-43da-bc2e-0f96de5e3f24)

![image](https://github.com/nahcusira/dvwa/assets/87233531/40bfb932-d109-49d0-8d57-1e21ec609a7e)

Basic Injection

At the start we got 2 queries right away: Original Query and Your Resulting Query so we just need to try the basic sql injection query ' or 1=1# then we get the flag

![image](https://github.com/nahcusira/dvwa/assets/87233531/b144937a-0d92-4db0-908f-5ce458a1942c)

![image](https://github.com/nahcusira/dvwa/assets/87233531/81628f6b-6678-47b0-b5fc-aaa042ee1bd6)

ACL Rulezzz the world

When we found drop down form we found nothing like login form so we check the source file by using an inspect element and we found value that's means what the command send the user request by method 'POST'. We try to change the value admin in the command by using admin' and we found an error which is sql vulnerability. Then we try a basic syntax admin' or 1=1# and we got flags

![image](https://github.com/nahcusira/dvwa/assets/87233531/0e11c6e8-0cb8-4cfa-a266-397191441511)

![image](https://github.com/nahcusira/dvwa/assets/87233531/e4cebf80-4792-4065-a57e-1a40a83178c8)

Login Portal 1

First use the basic query admin' or 1=1# then get the result "Illegal characters detected.". After a few tries I guess the "=,#,--" sign has been removed and I just need to make the username field always true by adding admin' or 'true so the query will become username='admin' or 'true' and no need for the removed characters on

![image](https://github.com/nahcusira/dvwa/assets/87233531/67e3f94e-60c3-4626-996b-9a99c2008dab)

![image](https://github.com/nahcusira/dvwa/assets/87233531/f7974d27-5131-4ce2-9794-943bac0c4d8c)

Login Portal 2

Tried simple sql injection into username and password ' or true#. We got “Wrong password for impossibletoguess.” → username = impossibletoguess

![image](https://github.com/nahcusira/dvwa/assets/87233531/aa376932-c965-4373-bfe9-3163d8e18c96)

Get name table by query: ' UNION SELECT table_name,NULL FROM information_schema.tables #

![image](https://github.com/nahcusira/dvwa/assets/87233531/f20b12c6-fd10-46f5-95da-6d78e90df423)

Get password of impossibletoguess by query: ' UNION SELECT password, NULL FROM users WHERE username='impossibletoguess' # → password: 1b2f190ad705d7c2afcac45447a31b053fada0c4

![image](https://github.com/nahcusira/dvwa/assets/87233531/ef2cf16c-070e-4ce5-80cc-1ad87c951312)

But it looks like this password is a SHA-1 hash because it has 40 characters. Thereby we can guess that when logging in will go through 2 steps: get the username and password from the database then hash the entered password value and check it against the returned value of the database. Since we can inject our own query into the username field, we can pass our own username and password hash and by pass the login.
SHA-1 of he153722: a55ee9c7f744fbd4617acf5e0b2e5d006e5eeb4b
Uername: 'UNION SELECT ALL 'admin', 'a55ee9c7f744fbd4617acf5e0b2e5d006e5eeb4b'# 
Password: he153722

![image](https://github.com/nahcusira/dvwa/assets/87233531/5f0fe904-5b8e-41db-8c53-440a76461a26)
