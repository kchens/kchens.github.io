#Preventing Attacks on Cookies and Sessions

Much of internet security is centered around protecting the user and the user's information. In building web apps, there are two main ways to store that information:  **cookies** and **sessions**. Here let's go over a few quick differences of the two, and delve into the high level of protecting your users against some of these attacks.

#Sessions
One thing that makes a session different is that the session is deleted **when the user closes the browser**.

How? Well, sessions uses a temporary cookie on the user's browser to store information -- usually it's an encrypted version of the user's id. In a Rails application, the client would pass this encrypted user id back to the server -- where the server would decrypt it and query the right id. 

As per usual protocol, the session is created and destroyed when logging-in and logging-out.

#Cookies

Cookies persist *even after the browser closes*. Moreover, cookies persist while the users navigates from one page to the next. 

A cookie is essentially a small pieced of text (~4kb) that stores user information, like a user id. Using a cookie, a Rails application can retrieve the logged-in user from the database.
 
Unfortunately, users can block or delete cookies -- making cookie-based features useless.

###Attacking Cookies
Unlike Sessions, Cookies are not automatically secure. There are 4 main ways cookies can be compromised:  

1.	Using a packet sniffer to detect and decode cookies passing over an insecure network
2.	Compromising a database with remember tokens 
3.	Using a cross-site scripting (XSS) 
4.	Gaining physical access to a machine with a logged-in user. 

To prevent these attacks, you can respectively:

1.	Ensure you're using a Secure Socket Layer (SSL) or Transfer Layer Security (TLS).
2.	Store a hash digest of the remember token instead of the token itself. 
3.	Rails prevents escaping any content inserted into the view templates. 
4.	Change tokens every time a user logs out. 

######XSS vs. XSRF
Cross-site scripting (XSS) enables attackers to inject client-side scripts into web pages that the user trusts (like through a form's comments). A XSS vulnerability may be used to let attackers bypass access controls such as the same-origin policy.

Cross-site request forgery (XSRF), or one-click attack, exploits the trust a site has in a user's browser. While authenticated on a website (like a bank website), the user might accidentally click on a script that instigates the XSRF attack. See more [here](http://www.owasp.org/index.php/Cross-Site_Request_Forgery_%28CSRF%29).

###Implementing a cookie

1.	Create a random string of digits for use as a remember token.
2.	Place the token in the browser cookies with an expiration date far in the future.
3. 	Save the hash digest of the token to the database.
4.	Place an encrypted version of the user’s id in the browser cookies.
5.	When presented with a cookie containing a persistent user id, find the user in the database using the given id, and verify that the remember token cookie matches the associated hash digest from the database.
6.	(Optional) Store the expiration date of the cookie and check against it.

#Thanks!
[Rails Tutorial](http://www.railstutorial.org/book/log_in_log_out)
[More on Security](http://crackstation.net/hashing-security.htm#normalhashing)

