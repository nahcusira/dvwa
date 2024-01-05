Local File Inclusion (LFI) and Remote File Inclusion (RFI) are two types of web vulnerabilities that allow an attacker to include malicious files on a target website. 

The main difference between the two is the location of the file being included: 

Local File Inclusion (LFI) occurs when a web application allows the inclusion of local files on the server, such as system files, log files, and configuration files. An attacker can exploit this vulnerability to access sensitive information stored on the server.

Remote File Inclusion (RFI) occurs when a web application allows the inclusion of remote files, usually through a URL or a network resource. An attacker can exploit this vulnerability by tricking the web application into including a malicious file hosted on a remote server, which can lead to the execution of arbitrary code on the target server.

In summary, LFI allows an attacker to access local files on the target server, while RFI allows an attacker to execute arbitrary code on the target server by including a malicious file from a remote location.

LOW LEVEL LFI

![image](https://github.com/nahcusira/dvwa/assets/87233531/1c85fba8-9a78-488e-8b6c-4420b00c8484)

This is a simple PHP code that retrieves the value of the "page" parameter from the URL and stores it in a variable named $file. It does not validate the user input and allows an attacker to access any file on the server by manipulating the "page" parameter in the URL.

![image](https://github.com/nahcusira/dvwa/assets/87233531/7f7786a5-cad3-4581-9b30-f9850e9a2a27)

LOW LEVEL RFI

![image](https://github.com/nahcusira/dvwa/assets/87233531/b71d82df-c011-48d9-838c-5e32654dfc61)

MEDIUM LEVEL LFI

![image](https://github.com/nahcusira/dvwa/assets/87233531/34aa57fb-31f7-4ede-b1ec-45d70417a85d)

This code adds some basic input validation to the previous code. The first line of validation uses the str_replace() function to remove any instances of "http://" or "https://" from the input, which would prevent an attacker from including a remote file from a different domain. The second line of validation uses str_replace() again to remove any instances of "../" or "..\" from the input, which would prevent an attacker from accessing files outside of the intended directory on the server.

![image](https://github.com/nahcusira/dvwa/assets/87233531/e9ea2abb-de36-4eba-9517-ed9d68edba68)

MEDIUM LEVEL RFI

![image](https://github.com/nahcusira/dvwa/assets/87233531/019b3fe5-1c4e-410c-b438-e087ac16c8ca)

HIGH LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/fc1a5eaa-69c4-4acf-9d12-243bb886051c)

This code adds a more robust input validation to the previous code. The validation uses the fnmatch() function to check if the input matches a specific pattern. In this case, the pattern is "file*", which means that only files that start with "file" are allowed to be included. The code also checks if the input is equal to "include.php", which allows a specific file to be included. If the input does not match the allowed pattern or not equal to "include.php", the code outputs an error message and exits the script. An attacker may find a way to bypass the validation by finding a file that starts with "file" and has a malicious payload.

![image](https://github.com/nahcusira/dvwa/assets/87233531/3d1b0a30-4d08-448c-bc68-61e6eedf8890)

IMPOSSIBLE LEVEL

![image](https://github.com/nahcusira/dvwa/assets/87233531/cee84946-ecba-41b0-9b8d-47dbcea3e62f)

This code adds a more secure input validation to the previous code. The validation checks if the input is either "include.php" or "file1.php", "file2.php", or "file3.php". If the input does not match any of these allowed values, the code outputs an error message and exits the script. This type of validation is more secure than the previous ones because it only allows specific and known files to be included, and it denies all other files.
