This lab contains a DOM-based open-redirection vulnerability. To solve this lab, exploit this vulnerability and redirect the victim to the exploit server.  
<br/>1\. Notice this piece of cod when you visit a post from the blog  
![2ecd867356d382ddd1e002c01faf095f.png](../_resources/2ecd867356d382ddd1e002c01faf095f.png)

&nbsp;**Dynamic URL Extraction:**  
The code uses a regular expression to extract the URL from the current browser location:

```
javascript





`returnUrl = /url=(https?:\/\/.+)/.exec(location)location.href = returnUrl ? returnUrl[1] : "/"`
```

This means if the current URL contains a `url=` parameter, the user will be redirected to whatever value is found after `url=`.

- **Unvalidated Redirect (Open Redirect):**  
    The code does not check if `returnUrl[1]` belongs to a safe or trusted domain. Anyone can craft a malicious link like:
    
    ```
    text
    
    
    
    
    
    `https://web-security-academy.net/post?postId=4&url=https://evil.com`
    ```
    
    When a user clicks the link, and then the JavaScript executes, it will send them to `https://evil.com.`  
    <br/><br/><br/><br/><br/>
    

2\. Change the url to your exploit server   
<br/>![e94e0a51c761b64cd1f4948c5816d5a7.png](../_resources/e94e0a51c761b64cd1f4948c5816d5a7.png)