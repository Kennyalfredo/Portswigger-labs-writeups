This lab controls access to certain admin functionality based on the Referer header. You can familiarize yourself with the admin panel by logging in using the credentials `administrator:admin`.

To solve the lab, log in using the credentials `wiener:peter` and exploit the flawed access controls to promote yourself to become an administrator.  
<br/>1\. When you log in as administrator notice the request that activates the function to upgrade or downgrade an user is:  
<br/>![70c10547a899371b9d0848aac11350cf.png](../_resources/70c10547a899371b9d0848aac11350cf.png)  
<br/>![d9e159f2340b7a3f1e33e0b5711c89da.png](../_resources/d9e159f2340b7a3f1e33e0b5711c89da.png)  
<br/>2\. Send the request to the repeater and hold it for a moment, then we are going to log in wiener:peter user and try to send the request again using this account's session cookie:  
![48765600844270eab9537dd616cb84ce.png](../_resources/48765600844270eab9537dd616cb84ce.png)

![21a7404cc1d8874b500826cfeb911804.png](../_resources/21a7404cc1d8874b500826cfeb911804.png)  
<br/>It means this request is not sanitized to be used just by users that have admin privileges.