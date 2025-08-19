This lab is vulnerable to web cache poisoning because it handles input from an unkeyed header in an unsafe way. An unsuspecting user regularly visits the site's home page. To solve this lab, poison the cache with a response that executes alert(document.cookie) in the visitor's browser.


1. In the main GET / request we are going to add a *cache buster* query parameter such as `?cb=1234`. Then we are going to add an `X-Forwarded-Host` header and a value like `test.com` and send the request again. 

  Notice that in the response `X-Forwarded-Host` header has been used to dynamically generate an absolute URL for importing a JavaScript file stored at /resources/js/tracking.js. And the response has a header `X-Cache:hit` which means that the response came from the cache. 

<img width="1412" height="872" alt="image" src="https://github.com/user-attachments/assets/510aa057-4883-4c9c-9dc5-bc3ade6925af" />



2. In the exploit server change the file path to `/resources/js/tracking.js` and the body to `alert(document.cookie)` and store the exploit.

<img width="1416" height="824" alt="image" src="https://github.com/user-attachments/assets/7ac715cb-5b75-4a05-996f-02ef71df01e4" />



3. In the GET request again, first delete the *cache buster* and change the `X-Forwarded-Host` to your exploit server, in this case `0aca0098030181ec8884fcc400b000c3.web-security-academy.net` and send it again, until you got in your response the header `X-Cache:hit`. Reload the site and it will deploy an error message.

<img width="1456" height="772" alt="image" src="https://github.com/user-attachments/assets/7022914b-c9ed-432b-90ea-91cf711130b2" />
