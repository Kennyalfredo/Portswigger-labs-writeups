Payload used: `<svg><animatetransform%20onbegin=alert(1)>`

1. First used intruder to test allowed tags: <svg><animatetransform>  
2. Then used intruder to get allowed events: onebegin  
<br/>SVG alone not very common with XSS, another tag will be used
