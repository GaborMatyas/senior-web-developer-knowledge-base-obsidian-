# Authentication


Authentication is **WHO YOU ARE**
(while Authorization is *what you can do* .... [[OAuth 2.0]] is an authorization framework)

- Use HttpOnly cookies for tokens: The hacker can not use Javascript to get the value out from the cookie. 

- Use secure cookies. When the cookie is being setted, set it as secure, so the browser will only send request over HTTPS. 

- Consider expiring logins after a time. (for example when the user has not been active for a daz, it is required to log in again, whether he has a cookie or not)

- Set a cookie expiration and remove session files. 

- Do not accept any session identifiers from GET and POST variables. 

- Regenerate session IDs periodically. 

- Use HTTPS. 

- [[Single SIgn-on Services]]
- - [[OAuth]]