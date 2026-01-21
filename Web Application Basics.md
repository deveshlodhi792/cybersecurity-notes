Date: 05-01-2026

🔴 Web Application Basics

**Front End of a Web Application**

- A web application use a number of technologies such as HTML, CSS, and JavaScript to do this.
- HTML
  * HTML (Hyper Text Markup Language) is a foundational aspect of web application.
  * It is the set of instruction and code that instructs the web browser on what to display and how to display it.
- CSS (Cascading Style Sheets)
  * This Language in web applications describes a standard appearance, such as certain colours, types of text, and layouts.
- JS (JavaScript)
  * JavaScript in a web application helps to perform more complex activity in the web browser.
  * JavaScript is a more advanced set of instruction that allows choices and decisions to be made on what to display.

 **Back End of a Web Application**

- The Back end of web application consists many things which one cannot see within a web browser but they are important for the web application to work.
- Database:
   * Websites store, modifiy and retrieve information about their users from their Database.
   * A web application may want to store and retrieve info about a visitor's preferences on what to show or not; this would be stored in a database.
- Other Infrastructure components:
  * There are many other infrastructure components that underpinning Web Applications.
  * Web Server, Application servers, storage, Various networking devices. and other software that supports the web application to work properly.
- WAF (Web Application Firewall)
  * WAF provides protection to the web Application
  * WAF helps a web application to filter out suspicious and dangerous requests away from the web servers.
 


 🔴 Uniform Resource Locator
 - A Uniform Resource Locator (URL) is a web address that lets one to access all kinds of online content like a webpage, a video, an image or other media.
 - URL links have the path to the specific location for the resource. In short it guides the browser to the right place on the internet.
 - A URL is made up of several parts, each part helps to get to the right resource.
 - A URL looks like this - "http://user:password@example.com:80/view-room?id=1#task3"
 - Here is a breakdown of the key components:
   * Scheme : The Scheme is the protocol used to access the website. HTTP and HTTPS are the most common.
   * User : Some URLs have user's login details (usually a username) for sites that require authentication. URL's that need credentials to access their content usually have user's details in it but it is not very safe, it can expose sensitive information, which is a security risk.
   * Host/Domain : The Host or Domain is the most important component of a URL as it tells which website you are accessing. Every domain name is unique and registered through domain registrar. Some fake domains using typosquatting often use phishing attacks and trick people to give their sensitive info.
   * Port : The port number helps direct you browser to the right service on the web server. Port numbers range from 1 to 65,535, but the most common are 80 for HTTP and 443 for HTTPS.
   * Path : The path points to the specific file or page on the server that you're trying to access. Its like a roadmap that shows the browser where to go. Websites need to secure these paths to make sure only authorised users can access sensitive resources.
   * Query String : The query string part of URL starts with a question mark (?). The query string is used in a web application to search terms or form inputs. Users can modify these query strings, it's important to handle them securely to prevent attacks like injections, where malicious code could be added.
   * Fragment : The fragment part starts with a hash symbol (#) and helps point to a specific section of a webpage - like jumping directly to a particular heading or table. Users can modify this too like query strings. Its important to check and clean up any data here to avoid issues like injection attacks.
  


🔴 HTTP Messages
- HTTP messages are the packets of data exchanged between a user (the client) and the web server.
- These messages show how user's requests and the server's responses are communicated.
- Types of HTTP messages:
  * HTTP Requests : Sent by the user to trigger actions on the web application.
  * HTTP Respnses : Sent by the server in response to the user's request.
 
- Every message follows a specific format to make communication smoothly.

- **Start Line** : The start line is like the Indroduction of the message. It tells one about what kind of message is being sent, whether it's a request from the user or a response from the server.

- **Headers** : Headers are made up of key-value pairs that provide extra information about the HTTP message. They give instructions to both the client and server handling the request or response. These headers cover all sorts of things, like security, content types, and more, making sure everything goes smoothly in the communication.

- **Empyt Line** : The empty line act as a little divider between the header and the body. It's essential because it shows where the headers stop and where the actual content of the message begins. Without empty line the client or server could misinterpret the message and can cause errors.

-  **Body** : The body is where 
                          
