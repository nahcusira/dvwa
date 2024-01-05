What is in-band SQL Injection?

In-band SQL injection is a type of SQL injection attack where the attacker can extract data from a database by sending SQL commands through the same channel used by the application to communicate with the database. This type of attack is characterized by the attacker being able to directly observe the results of their injected commands in the application's responses, typically in the form of error messages or data returned from the database.

LOW LEVEL

database’s name

![image](https://github.com/nahcusira/dvwa/assets/87233531/c9727ced-a2f5-420a-9fb8-b807cdb6ce66)

tables’ names

![image](https://github.com/nahcusira/dvwa/assets/87233531/a90496fb-57c3-4073-b1bc-ffd32331ada4)

columns’ names

![image](https://github.com/nahcusira/dvwa/assets/87233531/1750b049-2690-45ca-8347-7b6212d337f5)

usernames and password

![image](https://github.com/nahcusira/dvwa/assets/87233531/2e723f6b-be99-4e3d-8598-e2ee208ab376)

MEDIUM LEVEL

database’s name

![image](https://github.com/nahcusira/dvwa/assets/87233531/9681927f-397a-400c-bcba-0f259b23aaa0)

tables’ names

![image](https://github.com/nahcusira/dvwa/assets/87233531/71ec613f-40c7-4b28-adcf-838ebc95cca1)

columns’names

![image](https://github.com/nahcusira/dvwa/assets/87233531/7515859c-1417-46f5-9752-b121d8c2ef33)

usernames and password

![image](https://github.com/nahcusira/dvwa/assets/87233531/62fec8a1-1088-4eef-9cdf-1da4afad960e)

HIGH LEVEL

database’s name

![image](https://github.com/nahcusira/dvwa/assets/87233531/69c9c733-59eb-43c5-9c95-c570ba7041f7)

tables’ names

![image](https://github.com/nahcusira/dvwa/assets/87233531/5bdec292-5186-48b0-ad83-5f3e44e45342)

columns’ names

![image](https://github.com/nahcusira/dvwa/assets/87233531/840765e3-fde7-41d0-92a8-3fb2cc0c0d03)

usernames and passwords

![image](https://github.com/nahcusira/dvwa/assets/87233531/668de9f3-c378-4084-9c47-64dae8051432)

Explain the solution in Impossible level

The code first checks if the form has been submitted. If the form has been submitted, it checks an Anti-CSRF token to ensure that the form request is valid. The code then retrieves the input from the form (the 
user ID) and checks if it's numeric. If the input is numeric, the code selects data from the database using either MySQL or SQLite, depending on the configuration. The selected data is the first name and last name of the user with the specified ID. Finally, the code generates a new Anti-CSRF token for the next form request
