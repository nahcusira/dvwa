Most basic SQLi pattern

First we try to enter the basic command : 1' or 1=1 into the user,password then we get the result "You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' AND password = '1' or 1=1'' at line 1". From that we can guess that the query will look like: SELECT ..... FROM ..... Where username='$user' AND password='$password';

so we just need to comment(#) everything after 1=1 (always true) then we will get flag1' or 1=1#

![image](https://github.com/nahcusira/dvwa/assets/87233531/9334c4cb-ac51-4672-83c1-8c54b25e0e6f)

![image](https://github.com/nahcusira/dvwa/assets/87233531/1ee7fad3-475b-48ce-9423-25652e85653a)

Random Login Form

First create any account, log in but receive the message "Welcome back a, Seems like your not an admin!".then go back to register for an account with the user "admin" and receive the message "This account already exists.". After a few tries when adding a space before admin "admin" I still get the message "This account already exists." from that we can guess that the site removed the whitespace with "trim()". because "trim()" 
only removes spaces at the beginning, so we try to register for an "ad min" account, it was successful and we log in to that account, we will get a flag

![image](https://github.com/nahcusira/dvwa/assets/87233531/c8f5012b-eb5c-4390-b5f8-5491cb055731)

![image](https://github.com/nahcusira/dvwa/assets/87233531/e479a354-0516-4e32-b05c-489540fea17c)

Po po po po postgresql

First we try to enter the basic command: 1' or 1=1 into the user, the password will get the result "Illegal characters detected." so we can guess the match "=" has been filtered out. then we try again with: 1' then we get the result: "ERROR: syntax error at or near "da39a3ee5e6b4b0d3255bfef95601890afd80709" LINE 1: ...M users WHERE (username = ('1'') AND password = ( 'da39a3ee5e... ^" from that we can guess that the query will look like: "SELECT ..... FROM ..... Where (username=('...') AND password=('.. ...'));"

so to get the result we need to always be true on the user part and omit the password because the "=" sign has been removed so we will replace to “true”: 1')) or true -- 

the query will be: SELECT ..... FROM ..... Where (username=('1')) or true --') AND password=('.....'));

![image](https://github.com/nahcusira/dvwa/assets/87233531/ed931352-5b61-4718-9fe8-9674ba267d7b)

![image](https://github.com/nahcusira/dvwa/assets/87233531/6de2c36a-9a11-46d6-8cac-d76a8516c9f8)
