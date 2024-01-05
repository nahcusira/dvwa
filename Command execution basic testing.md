I. Low

![image](https://github.com/nahcusira/dvwa/assets/87233531/61853413-0a94-4945-8fd9-32b4561ae932)

We can use “&&” so the program can run both requests

II. Medium

![image](https://github.com/nahcusira/dvwa/assets/87233531/cba2d0e0-e47e-4ebd-9948-0a0bf97b37e4)

Here the flaw is only checking input with 2 cases "&&" and ";" but do not check the case that we only use 1 character

![image](https://github.com/nahcusira/dvwa/assets/87233531/3c1ae157-4694-4ebf-b6d1-1d1edb734ebb)

We can use “&” so the program can run both requests

III. High

![image](https://github.com/nahcusira/dvwa/assets/87233531/1c965feb-48db-4ff3-84c3-7eb3a936ea22)

Here we can see that the input has been checked very carefully through all the cases above but in case number 3 we see a space right after the "|" character. this could be a vulnerability that we can exploit in this case

![image](https://github.com/nahcusira/dvwa/assets/87233531/fbc9140e-ca07-451e-93d8-110c21d72529)

We can write "8.8.8.8|cat /etc/hosts" instead of "8.8.8.8 | cat /etc/hosts"
