LOW LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/4f5a7755-3085-4bd9-9836-ce4a4b3f2394)

Since the uploaded file check does not go through any filter, we can easily upload a php file to perform the exploit.

![image](https://github.com/nahcusira/dvwa/assets/87233531/bef0284b-ccd0-4fda-ba94-f9b8e92a937b)

![image](https://github.com/nahcusira/dvwa/assets/87233531/ae0a1eaa-5376-4851-913e-c0e7fc12cec1)

This is a PHP script that uses the built-in "system" function to execute a command passed through the GET parameter "cmd". It is a type of code injection vulnerability and could allow an attacker to execute arbitrary commands on the server.

![image](https://github.com/nahcusira/dvwa/assets/87233531/ad53159f-a69b-4edc-9bba-fe09b4a20471)

MEDIUM LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/055a03e8-b363-4d2c-a3ff-f9865bfdff4b)

An uploaded file is a JPEG or PNG image and is less than 100,000 bytes in size. If both conditions are true, the code block following this statement will be executed.

![image](https://github.com/nahcusira/dvwa/assets/87233531/847f565c-4bd0-4acc-8250-b3a5cf81466f)

![image](https://github.com/nahcusira/dvwa/assets/87233531/7418c6eb-bf8c-4b9b-af94-9670291c9cd1)

I can bypass the security by changing the content type of the file to image/jpeg during file upload. Simply upload the test.php file and before uploading to server intercept it in burp proxy. Then replace the content type from application/x-php to image/jpeg or image/png

![image](https://github.com/nahcusira/dvwa/assets/87233531/39da1c90-59c8-44db-8e6d-6d24261f901b)

![image](https://github.com/nahcusira/dvwa/assets/87233531/5fc4457f-f091-4275-b986-5dc7e72d1fff)

![image](https://github.com/nahcusira/dvwa/assets/87233531/11a01fa1-a072-4d11-a335-7239bf309490)

Then we can proceed to mine like LOW LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/52becedc-1d65-44c3-96ea-70231278fc83)

HIGH LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/bdeca7ae-8c9c-4735-a24a-26b7cdc13422)

An uploaded file has a jpeg or png extension and is less than 100,000 bytes in size. If both conditions are true, the code block following this statement will be executed. This method uses the "strtolower" function to convert the file extension to lowercase before comparing it to the valid extensions "jpg","jpeg" and "png". This is a more robust method of checking file extension, as file extension can be manipulated by attackers.

![image](https://github.com/nahcusira/dvwa/assets/87233531/6003204e-4656-4a99-bbaa-13dff5debd56)

Firstly I need to embed shell command in an image file. For this purpose I'll use the exiftool utility to insert a PHP code injection payload into the comment field of a JPEG image file named "high.jpg". The payload is designed to execute arbitrary commands passed through a GET parameter "cmd" when the image is processed on a server with a PHP interpreter.

![image](https://github.com/nahcusira/dvwa/assets/87233531/fd66b814-4939-4f81-b9d2-d6de29bcfbe2)

The image with the shell code was successfully uploaded but the code does not get executed. I need to rename the file to ".php". To do the renaming I will use command injection 

“127.0.0.1|mv ../../hackable/uploads/high.jpg ../../hackable/uploads/high.php”

![image](https://github.com/nahcusira/dvwa/assets/87233531/aa9196ba-641c-47cb-81e0-fff59780876c)

![image](https://github.com/nahcusira/dvwa/assets/87233531/90b34a67-4a3e-4972-b72a-397b8b84959f)

![image](https://github.com/nahcusira/dvwa/assets/87233531/2a36c6a7-504a-4592-a8a8-bc9c8eeef52b)

Then we can proceed to exploit like the above levels

![image](https://github.com/nahcusira/dvwa/assets/87233531/084d2566-d44b-4af0-9030-006876f98c1e)

![image](https://github.com/nahcusira/dvwa/assets/87233531/288a03a3-9d08-4824-8875-7fa39f861b44)
