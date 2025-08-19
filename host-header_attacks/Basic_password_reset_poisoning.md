
This lab is vulnerable to password reset poisoning. The user carlos will carelessly click on any links in emails that he receives. To solve the lab, log in to Carlos's account.

You can log in to your own account using the following credentials: wiener:peter. Any emails sent to this account can be read via the email client on the exploit server.


1. Email reset password link is sent to *wiener* user 




token:`jcijc0udlocg9ophtps20gv2cgnehmza`

2. In burp repeater you can change *Host Header* to any you want and you will still receive the email with the URL changed to the host to changed.




3. In burp repeater again change the *Host Header* to your exploit server URL and username to *carlos* and send it again:




4. You will notice in your exploit server access log that you got a request with a token:




password-token: `k0ueww65bqfw19rvc1jh290m3n3xs09o`

5. Then, you will go to the first URL in the first email they sent you and change the temp-forgot-password-token to the one that you received from *carlos*, you will access to carlos' account change password mode and solve the lab 


