---
published: true
---
This march 21 to march 23 was Yogosha's GISEC CTF 2022 in which I participated. This was a team competition but I decided to participate solo. My team was PsyDucks in which I (letigredununavu) was the only participant. I manage to end the CTF at the 14th place. Here are some challenges and solutions I found interesting.\

## WEB

### EatC00KiEs

Looking at the challenge's title, we already know we'll have to deal with some cookies. Upon arriving on the website, the first thing I do is looking at the cookies with the developper's tool. Here, I find a cookie named 'role' with the value 'Guest' and the site hint us that we need to make this cookie 'Admin'.\
![cookie1](/images/cookie2.png)\
To do this, I fire up burp suite and setup the proxy to this site. I intercept the request and add this line to it 'Cookie: role=Admin', when we get the response, we can see the flag in the html code.\
![cookie2](/images/Inkedcookies.jpg)\
We get the flag : GISEC{Cookies_C4n_B3_ModIfIeD_TOO?}\

## RecurPHP

In this challenge, we arrived at some php code. The code take an argument named 'naruto' and some lines later it compares it with the string secret, so first thing I do is insert the secret string into the argument, but we get 'Are u understanding the cod ?'.\
![php1](/images/Inkedphp1.jpg)\
I look a bit more at the code given and see that it use the preg_replace function to remove instances of the secret string in our input. So I google a little bit about this function and what I learn is that this function is not recursive. So if it found one or many instance of 'I_want_to_become_a_hockage', it will replace it with the null string, and then give the result away, but do not check if the result does contain the secret string, so we just need to make so that once the function replace our secret string, another secret string is created that the preg_replace won't check.\
![php2](/images/Inkedphp3.jpg)\
We get the flag : GISEC{I_1Ov3_Php_4nd_NaruT0_Oukii?}\

## TypeJugg

For this challenge I had to search a bit more, by the title I knew I had to exploit the type and the '==' operation of php which look at the value of the operand and not the type. We were given code that takes 2 arguments from the url, look that they are not equal and then verify that their hashes are equal, if yes, it gives us the flag. After a bit, I found some old CTF writeups that explained the concept of magic hashes. Thoses magic hashes are hashes that starts with '0e' so when used as operands with the '==' operator, they evaluates to 0 if all the digits after '0e' are in the range 0-9. So I look at the list of strings that gives us magic hashes on github and chose 2 that were differents, input it in the arguments and got this result !\
![typeJugg](/images/InkedmagicHash.jpg)\
We got the flag : GISEC{php_typing_is_weak_just_like_you:)}\

Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.
