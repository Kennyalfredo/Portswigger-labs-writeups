This lab's email change functionality is vulnerable to CSRF. It attempts to detect and block cross domain requests, but the detection mechanism can be bypassed.

To solve the lab, use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

You can log in to your own account using the following credentials: `wiener:peter`  
<br/>1\. Go to the change email request and try to change the referer header, see that it rejects the request  
<br/>![76d469fb6eaaa8961ea569486c9c9829.png](../_resources/76d469fb6eaaa8961ea569486c9c9829.png)  
<br/>2\. Try adding your lab ID as a parameter of the referer URL and now it accepts it:  
<br/>![dd6979e71865fa2b1ab8ca11ea6d284f.png](../_resources/dd6979e71865fa2b1ab8ca11ea6d284f.png)  
<br/>3\. Generate your POC CSRF in the exploit server and add your lab id to the history.pushState('', '', ','); third parameter.

![0272de5b00cbf418e371afd7b0bc8843.png](../_resources/0272de5b00cbf418e371afd7b0bc8843.png)  
<br/>And also add to the head section `Referrer-Policy: unsafe-url`  
<br/>![94107c105688de0b797776a9f0c5a570.png](../_resources/94107c105688de0b797776a9f0c5a570.png)  
<br/>4\. Store the exploit and deliver it to the victim

  
<br/><br/>