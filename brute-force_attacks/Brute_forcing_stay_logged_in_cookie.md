This lab allows users to stay logged in even after they close their browser session. The cookie used to provide this functionality is vulnerable to brute-forcing.

To solve the lab, brute-force Carlos's cookie to gain access to his My account page.

- Your credentials: wiener:peter 
- Victim's username: carlos
- Candidate passwords


1. Notice that the request has an stay logged in option and this will deploy a stay-logged-in cookie:

<img width="1458" height="552" alt="image" src="https://github.com/user-attachments/assets/168a71ce-813e-4fbd-83ad-6167cf6de029" />


2. Send the request to intruder and mark the stay-logged-in cookie, we will brute force it 

<img width="1302" height="948" alt="image" src="https://github.com/user-attachments/assets/fe4aac7e-5d18-4fba-91ea-a2745a0204ca" />

3. configure rules like:

Grep the Update email command on every Response, and paste the list of passwords.


4. Initiate the attack and you will see the Carlos' password:
<img width="1308" height="466" alt="image" src="https://github.com/user-attachments/assets/6459d053-d308-4b11-965c-541f704741a8" />
