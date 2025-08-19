
This lab is vulnerable to password reset poisoning. The user carlos will carelessly click on any links in emails that he receives. To solve the lab, log in to Carlos's account.

You can log in to your own account using the following credentials: wiener:peter. Any emails sent to this account can be read via the email client on the exploit server.


1. Email reset password link is sent to *wiener* user 

<img width="1444" height="268" alt="image" src="https://github.com/user-attachments/assets/b94f7413-7fd2-44e4-81ac-4f1a2fd92c36" />

token:`jcijc0udlocg9ophtps20gv2cgnehmza`

2. In burp repeater you can change *Host Header* to any you want and you will still receive the email with the URL changed to the host to changed.

<img width="1452" height="832" alt="image" src="https://github.com/user-attachments/assets/f7e1de21-d0d1-45e9-8223-bb15f2a4e79a" />

<img width="1456" height="386" alt="image" src="https://github.com/user-attachments/assets/47e538b2-c2d2-4153-9833-7cdd8243eebd" />


3. In burp repeater again change the *Host Header* to your exploit server URL and username to *carlos* and send it again:


<img width="1446" height="816" alt="image" src="https://github.com/user-attachments/assets/5eb9fa4b-0da3-4080-a42d-122e09b5f13f" />


4. You will notice in your exploit server access log that you got a request with a token:

<img width="1464" height="680" alt="image" src="https://github.com/user-attachments/assets/63db82e1-c231-4d78-b89d-581a0d75974e" />

password-token: `k0ueww65bqfw19rvc1jh290m3n3xs09o`

5. Then, you will go to the first URL in the first email they sent you and change the temp-forgot-password-token to the one that you received from *carlos*, you will access to
carlos' account change password mode and solve the lab 

<img width="1450" height="804" alt="image" src="https://github.com/user-attachments/assets/6a0a7144-b7f7-40a3-846e-6f8e8a3e6d01" />



