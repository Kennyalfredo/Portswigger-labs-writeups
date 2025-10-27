This lab's email change functionality is vulnerable to CSRF.

To solve the lab, use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

You can log in to your own account using the following credentials: `wiener:peter`  
<br/><br/>1\. We are going to the change email functionality and notice it sends a csrf token, but if we delete it we can send it and get a 302 response  
<br/>![6fe385380f7eac6f453cc2eb9f462023.png](../_resources/6fe385380f7eac6f453cc2eb9f462023.png)  
<br/>3\. Right-click and generate CSRF-POC, paste in the exploit server, change the email to one different than yours and send it to the victim  
<br/>![81473d9023184f21b92d4f0d5bba6e26.png](../_resources/81473d9023184f21b92d4f0d5bba6e26.png)  
<br/>