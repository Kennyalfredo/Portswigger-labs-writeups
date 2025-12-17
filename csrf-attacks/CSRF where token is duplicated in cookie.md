This lab's email change functionality is vulnerable to CSRF. It attempts to use the insecure "double submit" CSRF prevention technique.

To solve the lab, use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

You can log in to your own account using the following credentials: `wiener:peter`  
<br/>1\. Notice that there are two csrf tokens in the requests:  
<br/>![a1311f91ea69be6332add7fff8d275be.png](../_resources/a1311f91ea69be6332add7fff8d275be.png)  
<br/>It validates the two are the same to accept the request.  
<br/>2\. Notice that when you search a term it reflects the term in the Set-cookie response header   
<br/>![c301149f87ca435a1b5cebf4ef5a3567.png](../_resources/c301149f87ca435a1b5cebf4ef5a3567.png)  
<br/>3\. So what we can do is create a fake csrf cookie so it reflects in the Cookie: request. Use this payload:  
`?search=test%0d%0aSet-Cookie:%20csrf=fake%3b%20SameSite=None`. See how it gets reflected:  
<br/>![63f632d25c1a26349de37490823f3583.png](../_resources/63f632d25c1a26349de37490823f3583.png)  
<br/>4\. Create CSRF POC in the change email request and ensure the csrf is 'fake'. Change the &lt;script&gt;....&lt;/script&gt; section to  `<img src="https://YOUR-LAB-ID.web-security-academy.net/?search=test%0d%0aSet-Cookie:%20csrf=fake%3b%20SameSite=None" onerror="document.forms[0].submit();"/>`. Store the exploit and deliver it to the victim  
<br/>![744692ba116439691f4140fbd46e4775.png](../_resources/744692ba116439691f4140fbd46e4775.png)