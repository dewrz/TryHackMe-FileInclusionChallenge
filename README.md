# TryHackMe-FileInclusionChallenge

Ok, we have here a challenge to capture 4 flags from a website by using path traversal and manipulating the URL through GET, POST, COOKIE, or HTTP header values!
<br>
<br>
<b>Challenge 1:</b><br>
<br>
Ok, so the input form is broken and we have to send a POST request manually. They want us to retrieve the flag at /etc/flag1.<br>
<br>
<a href="https://imgur.com/a4280FT"><img src="https://i.imgur.com/a4280FT.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
After inspecting the page source, it appears that we will use the 'GET' method and the 'file' parameter. We will use curl from the CLI to do this<br>
<br>
<a href="https://imgur.com/rxqEQoc"><img src="https://i.imgur.com/rxqEQoc.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
And we can see the first flag below.<br>
<br>
<a href="https://imgur.com/l958iR2"><img src="https://i.imgur.com/l958iR2.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
<b>Challenge 2:</b><br>
<br>
Ok, so this is similar, they want us to retrieve /etc/flag2, but it appears we will need to manipulate a cookie so we will need to pull up Burpsuite.<br>
<br>
<a href="https://imgur.com/Oamd82B"><img src="https://i.imgur.com/Oamd82B.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
Ok, so after we pull up Burpsuite we go over to the "proxy" tab, turn on "intercept" and change the "Guest" cookie to "admin" and forward it to the site. Below is the message we receive. The message divulges some information like the current file path we're on.<br>
<br>
<a href="https://imgur.com/gK9fCdg"><img src="https://i.imgur.com/gK9fCdg.jpg" title="source: imgur.com" /></a><br>
<br>
<a href="https://imgur.com/pN5VFdm"><img src="https://i.imgur.com/pN5VFdm.jpg" title="source: imgur.com" /></a><br>
<br>
So next we'll try to manipulate the file path in Burpsuite to see if we can reveal the flag. I will add a path traversal of ../../../../etc/flag2 to see what we get.<br>
<a href="https://imgur.com/h2mGAkX"><img src="https://i.imgur.com/h2mGAkX.jpg" title="source: imgur.com" /></a><br>
<br>
Ok, so we have a php extension holding us back, so we'll add a null byte at the end of the path traversal and see what happens.<br>
<br>
<a href="https://imgur.com/oT0HR3s"><img src="https://i.imgur.com/oT0HR3s.jpg" title="source: imgur.com" /></a><br>
<br>
And that worked out and revealed the flag.<br>
<br>
<a href="https://imgur.com/r3itglv"><img src="https://i.imgur.com/r3itglv.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
<b>Challenge 3:</b><br>
<br>
Just like the first two challenges, they want us to retrieve the flag from /etc/flag3. I tried a path traversal, but it appears the code is filtered.<br>
<br>
<a href="https://imgur.com/CIAfeLc"><img src="https://i.imgur.com/CIAfeLc.jpg" title="source: imgur.com" /></a><br>
<br>
I tried to go with this format: ....//....//....//....//, but it was still receiving an error. So lets pull up the CLI and try to send a request via curl.<br>
<br>
<a href="https://imgur.com/o91WF4k"><img src="https://i.imgur.com/o91WF4k.jpg" title="source: imgur.com" /></a><br>
<br>
After sending that request we reveal the flag.<br>
<br>
<a href="https://imgur.com/ysSfUmh"><img src="https://i.imgur.com/ysSfUmh.jpg" title="source: imgur.com" /></a><br>
<br>
<br>
<b>Challenge 4:</b><br>
<br>

