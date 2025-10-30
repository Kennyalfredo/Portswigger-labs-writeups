This lab is vulnerable to server-side template injection due to the way it unsafely uses a Tornado template. To solve the lab, review the Tornado documentation to discover how to execute arbitrary code, then delete the `morale.txt` file from Carlos's home directory.

You can log in to your own account using the following credentials: `wiener:peter`  
<br/><br/>1\. Notice there is a functionality to change the preferred name:  
<br/>![7fd9a3e6c99257a8de6ce22bbd8ab95c.png](../_resources/7fd9a3e6c99257a8de6ce22bbd8ab95c.png)  
<br/>2\. It creates this request:  
![d17400cf0ff981f417630f041f74b053.png](../_resources/d17400cf0ff981f417630f041f74b053.png)  
<br/>3\. It uses Tornado template insecurely and studying it you can view that it can execute python code using the payload to delete morale.txt file:   
<br/>`{% import os %} {{os.system('rm /home/carlos/morale.txt')`

![28b61e3f90cbfbccd0f23d5ccc126307.png](../_resources/28b61e3f90cbfbccd0f23d5ccc126307.png)