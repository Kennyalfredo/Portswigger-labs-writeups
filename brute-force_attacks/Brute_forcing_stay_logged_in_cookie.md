This lab allows users to stay logged in even after they close their browser session. The cookie used to provide this functionality is vulnerable to brute-forcing.

To solve the lab, brute-force Carlos's cookie to gain access to his My account page.

- Your credentials: wiener:peter 
- Victim's username: carlos
- Candidate passwords


1. Notice that the request has an stay logged in option and this will deploy a stay-logged-in cookie:

2. Send the request to intruder and mark the stay-logged-in cookie, we will brute force it 

3. configure rules like:

Grep the Update email command on every Response, and paste the list of passwords.


4. Initiate the attack and you will see the Carlos' password:
