---
published: false
---
This march 21 to march 23 was Yogosha's GISEC CTF 2022 in which I participated. This was a team competition but I decided to participate solo. My team was PsyDucks in which I (letigredununavu) was the only participant. I manage to end the CTF at the 14th place. Here are some challenges and solutions I found interesting.\ 

## WEB

### EatC00KiEs

Looking at the challenge's title, we already know we'll have to deal with some cookies. Upon arriving on the website, the first thing I do is looking at the cookies with the developper's tool. Here, I find a cookie named 'role' with the value 'Guest' and the site hint us that we need to make this cookie 'Admin'.\
![cookie1](/images/cookie2.png)\
To do this, I fire up burp suite and setup the proxy to this site. I intercept the request and add this line to it 'Cookie: role=Admin', when we get the response, we can see the flag in the html code.\
![cookie2](/images/Inkedcookies.jpg)\
We get the flag : GISEC{Cookies_C4n_B3_ModIfIeD_TOO?}

Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.
