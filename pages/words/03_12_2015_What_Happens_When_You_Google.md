#What Happens When You Type Google.com?

If you're reading this, chances are you've come across answers to this question before. You've probably read this [GitHub](http://github.com/alex/what-happens-when) page on the topic, then gave up. You may have also come across this [blog post](http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/), which does a slightly better job.

Here's my take at it -- in colloquial terms.

###1. You type "google.com" into your browser.
###2. Your browser looks up the IP address (127.102...) for "google.com"
-	**Browser** checks its **cache**...if not found...
-	**Operating System** (Windows, MacOS) **cache** is checked...if not found...
-	**Router cache** is checked (yes, the thing that connects to your cable modem) ...
-	**ISP's DNS cache** is checked ...
-	**DNS Recursive Search** occurs -- pinging other DNS for Google's IP address.

###3. With the IP address, the Browser opens ups a TCP connection (a socket)
-	If you made a request through **HTTP**, the TCP connection opens up on **PORT 80**
-	If **HTTPS**, the connection is opened on **PORT 443**
-	The socket is necessary to send and receive information.

###4. A Transport Layer Security (TLS) Handshake Occurs
-	A.	The Client sends a *ClientHello* message with a list of specifications, like cipher and compression algorithms; the Server sends a *ServerHello* message with a chosen cipher and compression algorithm.
-	B.  Server also sends a certificate signed by a *[Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority)*; Client checks the CA for authenticity.
-	C. Client then creates pseudo-random bytes (uses this to determine a **symmetric key**), and encrypts the bytes with the server's *public key*;  Server decrypts the bytes using its *private key*, thereby creating its own copy of the **symmetric key**.
-	The TLS handshake is necessary to ensure the client and server are who they say they are. The **symmetric** key is now used for further transfer of information. It prevents hackers from getting your information.

###5. Browser finally sends the HTTP request to the Server
-	In the headers, the request will include the **User-Agent**, **Authorization**,**Accept**, **Content-Type**, **Origin**. (See [here](http://apionrails.icalialabs.com/book/chapter_two) for more)
-	Cookies (key-value pairs) are also sent to track the state of the web site in-between page requests. Also stores user log-in info, user settings, and more.
-	**GET** request parameters are typically sent through the URL
-	**POST** request parameters are sent in the request body, just under the headers

###6. Server responds with a permanent redirect to "WWW.google.com"
-	Search engines understand permanent redirects (301) response, but they're not smart enough to tell the difference between "www.google.com" and "google.com".
-	The Browser then repeats the above steps to ping "www.google.com"

###7. Server 'handles' the request
-	**Web Server Software** (ex. Apache) receives the HTTP request and decides which request handler/app (Ruby, PHP, Python, etc.) should handle the request
-	**Request Handler** reads the request, parameters, and cookies. The app generates an HTML response. Request handlers often store resources in a file hierarchy similar to URL structure.

###8. Browser begins rendering the HTML 
###9. Browser sends request for objects embedded in HTML
-	Browser fetch images, CSS, and JS files through the same steps listed above.
-	*Flash of Unstyled Content* (FOUC) may happen
###10. Browser sends further AJAX requests
-	...based on User input.