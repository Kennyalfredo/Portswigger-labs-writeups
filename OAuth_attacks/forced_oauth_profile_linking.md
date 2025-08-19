
This lab gives you the option to attach a social media profile to your account so that you can log in via OAuth instead of using the normal username and password. Due to the insecure implementation of the OAuth flow by the client application, an attacker can manipulate this functionality to obtain access to other users' accounts.

To solve the lab, use a CSRF attack to attach your own social media profile to the admin user's account on the blog website, then access the admin panel and delete carlos.

The admin user will open anything you send from the exploit server and they always have an active session on the blog website.

You can log in to your own accounts using the following credentials:

- Blog website account: wiener:peter
- Social media profile: peter.wiener:hotdog


1. Notice that the website send to important request when trying to log in with a social media 

<img width="1454" height="714" alt="image" src="https://github.com/user-attachments/assets/18678adb-e3ae-43d3-afa2-349150e899fe" />

<img width="1460" height="706" alt="image" src="https://github.com/user-attachments/assets/89717542-7c9c-42e7-a213-fd7112524a4b" />



And this activates a code that in the GET /oauth request.

2. We are going to intercept one of this requests, copy the URL, and drop it so the code is not used anymore.


3. We are going to create an `<iframe>` request with the previously copied URL and we will deliver it to the administrator victim:

`<iframe src="https://0a420003036f49db8006440800840021.web-security-academy.net/oauth-linking?code=cUJbzWuLSTqIo0_645XlQvaTCp6I1zJOhxUtpqkcNlI"></iframe>`


4. With delivered the victim will open the URL and when he logs in the social media account that will be associated with his account will be our social media account, so when we log in with our social media account again, we will be logged as the administrator victim.

