## Networking

### HTTP
HTTP, the Hyper Text Transfer Protocol, is the application protocol for transmitting hypermedia documents, such as HTML. However, due to its extensibility, it is also used for fetching images and videos or to post content to servers, like form results. After the original request to fetch the HTML document, it then parses this file and fetches additional requests corresponding to execution scripts, layout information (CSS) to display, and sub-resources contained within the page (usually images and videos). The Web browser then mixes these resources to present to the user a complete document, the Web page. Scripts executed by the browser can fetch more resources in later phases and the browser updates the Web page accordingly. HTTP follows a client-server model, with a client (web browser) opening a connection to make a request, then waiting until it receives a response. HTTP is a stateless protocol, meaning that the server does not keep any data between two requests. However, HTTP cookies allow the use of stateful sessions. 

### HTTP Messages
Requests consists of an HTTP method (like GET, POST), the path of the resource to fetch, the version of the HTTP protocol, optional headers and a body(for POST). Responses consists of the version of the HTTP protocol, a status code indicating if the request has been successful or not (ex. 200, 404), a status message (short description of the status code) headers and optionally, a body containing the fetched resource.

### HTTP/2

### HTTPS
HTTPS is HTTP with SSL encryption. 

### TCP/IP
TCP (Transmission Control Protocol) is responsible for routing application protocols to the correct application on the destination computer. When the TCP layer receives the application layer protocol data from above, it segments it into manageable 'chunks' and then adds a TCP header to each 'chunk'. The information contained in the TCP header includes the port number of the application the data needs to be sent to. When the TCP layer receives a packet from the IP (Internet Protocol) layer below it, the TCP layer strips the TCP header data from the packet, does some data reconstruction if necessary, and then sends the data to the correct application using the port number taken from the TCP header. Notice that there is no place for an IP address in the TCP header. This is because TCP doesn't know anything about IP addresses. TCP's job is to get application level data from application to application reliably. The task of getting data from computer to computer is the job of IP. IP's job is to send and route packets to other computers. IP packets are independent entities and may arrive out of order or not at all. It is TCP's job to make sure packets arrive and are in the correct order.

### IP Address
IP (Internet Protocol) address is a network addressable location. Each IP address must be unique within its network. The addresses are in the form nnn.nnn.nnn.nnn where nnn must be a number from 0 - 255. Any Internet-connected computer can be reached through a public IP Address, which consists of 32 bits for IPv4 (they are usually written as four numbers between 0 and 255, separated by dots (e.g., 173.194.121.32) or which consists of 128 bits for IPv6 (they are usually written as eight groups of 4 hexadecimal numbers, separated by colons (e.g., 2027:0da8:8b73:0000:0000:8a2e:0370:1337). Computers can handle those addresses easily, but people have a hard time finding out who's running the server or what service the website offers. IP addresses are hard to remember and might change over time. To solve all those problems we use human-readable addresses called domain names.

### DNS
DNS is a distributed database system which translates human-friendly domain names to numerical IP addresses. For example, www.google.com translates to 216.58.218.110. DNS is implemented as a distributed directory service. Each DNS server stores a database of domain names to IP addresses. If it cannot find a domain name being queried in this database, it forwards the request to other DNS servers. To improve performance, caching is heavily used.

### CORS
CORS (Cross-Origin Resource Sharing) is a mechanism that uses additional HTTP headers to let a user agent gain permission to access selected resources from a server on a different origin (domain) than the site currently in use. A user agent makes a cross-origin HTTP request when it requests a resource from a different domain, protocol, or port than the one from which the current document originated. For security reasons, browsers restrict cross-origin HTTP requests initiated from within scripts. For example, XMLHttpRequest and the Fetch API follow the same-origin policy. This means that a web application using those APIs can only request HTTP resources from the same domain the application was loaded from unless CORS headers are used.

### Cookie
Cookie is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. It remembers stateful information for the stateless HTTP protocol. Cookies are mainly used for session management (logins, shopping carts, game scores), personalization(user preferences and themes), and tracking(recording and analyzing user behavior).

## Security

### DoS Attack
DoS (Denial of Service) is a network attack that prevents legitimate use of server resources by flooding the server with requests. Computers have limited resources, for example computation power or memory. When these are exhausted, the program can freeze or crash, making it unavailable. A DoS attack consists of various techniques to exhaust these resources and make a server or a network unavailable to legitimate users, or at least make the server perform sluggishly.

### XSS
Cross-site scripting (XSS) is a security exploit which allows an attacker to inject into a website malicious client-side code. This code is executed by the victims and lets the attackers bypass access controls and impersonate users. These attacks succeed if the Web app does not employ enough validation or encoding. The user's browser cannot detect the malicious script is untrustworthy, and so gives it access to any cookies, session tokens, or other sensitive site-specific information, or lets the malicious script rewrite the HTML content. Cross-site scripting attacks usually occur when 1) data enters a Web app through an untrusted source (most often a Web request) or 2) dynamic content is sent to a Web user without being validated for malicious content. The malicious content often includes JavaScript, but sometimes HTML, Flash, or any other code the browser can execute. The variety of attacks based on XSS is almost limitless, but they commonly include transmitting private data like cookies or other session information to the attacker, redirecting the victim to a webpage controlled by the attacker, or performing other malicious operations on the user's machine under the guise of the vulnerable site. XSS attacks can be put into three categories: stored (also called persistent), reflected (also called non-persistent), or DOM-based.

### CSRF
CSRF (Cross-Site Request Forgery) is an attack that impersonates a trusted user and sends a website unwanted commands. This can be done, for example, by including malicious parameters in a URL behind a link that purports to go somewhere else.

## Object Oriented Programming

### Favor Composition Over Inheritance
Code reuse should be achieved by assembling smaller units of functionality instead of inheriting from classes. In other words, use can-do, has-a, or uses-a relationships instead of is-a relationships.

## System Design

### Stateless/Stateful System
A stateless system's output depends only on the input. A stateful system's output depends on the input and internal state. Therefore, the same set of input can generate different output. This makes multiple actors accessing the system a trickier problem.

### Read-Heavy/Write-Heavy System

## Programming Language

### Closure
Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.
```
function foo(){
  var a = 2;
  function bar(){
    console.log(a);
  }
  return bar;
}

var baz = foo();

baz(); // 2
```

## Database

### Relational Database
A relational database is a set of tables. Each table consists of rows. A row is a set of columns, which could be of various types. SQL is the language used to create and manipulate such databases. A key benefit of relational databases include support for ACID(Atomicity, Consistency, Isolation, Durability) transactions.


### Normalization/Denomalization
Database normalization is to organize the database so as to minimize redunduncy. It involves decomposing tables utilizing foreign keys (a field in one table that uniquely identifies a row of another table). Denormalization on the other hand, adds redundant data to one or more tables so as to avoid expensive joins and improve performance. However, extra effort to update the database consistently (multiple fields to update at one time) and more storage are necessary.

### JOIN
Join is used to combine the results of two tables. To perform a join, each of the tables must have at least one field that will be used to find matching records from the other table.<br/>
Inner Join: The result set would contain only the data where the criteria match.<br/>
Outer Join: The result set also contains records that have no matching. The unmatched field will have a NULL value.<br/> 
Left Outer Join: The result will contain all records from the left table regardless of match.<br/>
Rgith Outer Join: The result will contain all records from the right table regardless of match.<br/>
Full Outer Join: The result will contain all records from both the left and right table regardless of match.<br/>

## Web Programming

### MVC
The Model-View-Controller (MVC) is an architectural pattern that organizes an application into three components: the model, the view, and the controller. The Model corresponds to the data-related logic. The View component is used for all the UI logic. Controllers act as an middle man between Model and View to process incoming requests, manipulate data using the Model component and interact with the Views to render the final output. Ruby on Rails.

### Resetting/Normalizing CSS
Resetting: Strip all default browser styling on elements.
Normalizing: Preserves useful default styles rather than "unstyling" everything. 


## Performance

### Minification



## JavaScript

### this
“this” is not an author-time binding but a runtime binding. It is contextual based on the conditions of the function's invocation. this binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called. When a function is invoked, an activation record, otherwise known as an execution context, is created. This record contains information about where the function was called from (the call-stack), how the function was invoked, what parameters were passed, etc. One of the properties of this record is this reference which will be used for the duration of that function's execution. Determining the this binding for an executing function requires finding the direct call-site of that function. Once examined, four rules can be applied to the call-site, in this order of precedence:
1 Called with new? Use the newly constructed object.
2 Called with call or apply (or bind)? Use the specified object.
3 Called with a context object owning the call? Use that context object.
4 Default: undefined in strict mode, global object otherwise.

### Prototypal Inheritance V.S. Class Inheritance
In class inheritance, instances inherit from classes and create hierarchical sub-class relationships. Instances are typically instantiated via constructor functions with the 'new' keyword. In prototypal inheritance, instances inherit directly from other objects and may be composed from many different objects, allowing easy selective inheritance. Instances are typically instantiated via factory functions or 'Object.create()'.

### == and ===
== allows coercion in the equality comparison
=== disallows coercion in the equality comparison.

### Falsy values / Truthy values
Falsy values are, undefined, null, false, +0, -0, and NaN, ””.
All others are Truthy values.

### NaN
A special value given when Number coercion fails.

