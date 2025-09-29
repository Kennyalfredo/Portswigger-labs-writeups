This lab contains a web cache poisoning vulnerability that is only exploitable when you use multiple headers to craft a malicious request. A user visits the home page roughly once a minute. To solve this lab, poison the cache with a response that executes `alert(document.cookie)` in the visitor's browser.  
<br/><br/>1\. Notice this curious request:  
<br/>![44e6d6d1f37c3f3761bcccf12057dc62.png](../_resources/44e6d6d1f37c3f3761bcccf12057dc62.png)  
<br/>2\. Try to poison the headers:  
<br/>**X-Forwarded-Host:  
**This header identifies the original host requested by the client in the Host HTTP request header. It is added by a proxy or load balancer because, as requests pass through intermediaries, the Host header can change, and the backend might need to know the actual hostname the user accessed. Helps in scenarios with virtual hosting, so the backend can route requests properly, generate correct links, or log the original host accessed.  
<br/>Example: `X-Forwarded-Host: example.com`  
<br/>**X-Forwarded-Scheme****:  
**This header tells the backend what protocol (HTTP or HTTPS) was originally used by the client, even if the proxy itself modified the connection type. Useful for web applications to generate absolute URLs or redirects with the correct scheme, and for security-sensitive features (e.g., knowing if the initial connection was secure).  
<br/>Example: `X-Forwarded-Scheme: https`  
<br/>\- X-Forwarded-Host:  
use a payload like example.com, nothing happens and the webpage responds the same  
<br/>![99d040240979c6a877e4e7213fc50b88.png](../_resources/99d040240979c6a877e4e7213fc50b88.png)  
<br/>\- X-Forwarded-Scheme  
use a payload like https, the respond will be 302 Found  
<br/>![9efbeab2e7e8728ab8dd9e947523f46f.png](../_resources/9efbeab2e7e8728ab8dd9e947523f46f.png)  
<br/>\- Now try with both headers, but this time `X-Forwarded-Scheme: nohttps` and notice it responds with a 302 Found, but this time the Location: is example.com  
<br/>![d35b9b037c71b14d0aa8dc85b777e617.png](../_resources/d35b9b037c71b14d0aa8dc85b777e617.png)  
<br/>3\. Exploit:  
Go to exploit server and create a payload like alert(document.cookie) to the directory /resources/js/tracking.js, store it  
<br/>![70106d0c3456a7408a8eedb0d36ea549.png](../_resources/70106d0c3456a7408a8eedb0d36ea549.png)  
<br/>In the request change the X-Forwarded-Host to your exploit server Domain and leave the X-Forwarded-Scheme as nohttps   
<br/>![ac7e2fa1733753a34797c176320d6021.png](../_resources/ac7e2fa1733753a34797c176320d6021.png)  
<br/>You will get a 302 Found response, try this until you get a X-Cache: hit  
![85722ecef2324d9191573ed9314269cc.png](../_resources/85722ecef2324d9191573ed9314269cc.png)  
<br/>4\. Wait for the victim:  
Go to the home page, load it and wait until the victim loads the page and solve the lab  
<br/><br/>

## Why the Exploit Works

- The vulnerability comes from the server’s logic that mishandles both `X-Forwarded-Host` and `X-Forwarded-Scheme`, allows user input into redirection and caching decisions, and doesn’t properly separate cache keys by those header values
    
- Attackers abuse this by injecting a malicious host (pointing to their payload) and scheme, tricking the cache into storing and serving a harmful script to legitimate users.
    

Each of these steps is necessary because the cache only accepts poisoned responses when both headers are manipulated together; otherwise, the separate use of each header would either have no effect or not result in a cacheable response, leaving the application vulnerable to cache poisoning.