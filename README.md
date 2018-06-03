## Networking

### HTTP
HTTP, the Hyper Text Transfer Protocol, is the application protocol that web browsers and servers use to communicate with each other over the Internet. Clients (web browsers) send requests to web servers for web elements such as web pages and images. After the request is serviced by a server, the connection between client and server across the Internet is disconnected. HTTP is a connectionless text based protocol.

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


## Object Oriented Programming

### Favor Composition Over Inheritance
Code reuse should be achieved by assembling smaller units of functionality instead of inheriting from classes. In other words, use can-do, has-a, or uses-a relationships instead of is-a relationships.

## System Design

### Stateless/Stateful System
A stateless system's output depends only on the input. A stateful system's output depends on the input and internal state. Therefore, the same set of input can generate different output. This makes multiple actors accessing the system a trickier problem.

### Read-Heavy/Write-Heavy System


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

### Contrast Prototypal Inheritance with Class Inheritance
In class inheritance, instances inherit from classes and create hierarchical sub-class relationships. Instances are typically instantiated via constructor functions with the 'new' keyword. In prototypal inheritance, instances inherit directly from other objects and may be composed from many different objects, allowing easy selective inheritance. Instances are typically instantiated via factory functions or 'Object.create()'.

### == and ===
== allows coercion in the equality comparison
=== disallows coercion in the equality comparison.

### Falsy values / Truthy values
Falsy values are, undefined, null, false, +0, -0, and NaN, ””.
All others are Truthy values.

### NaN
A special value given when Number coercion fails.

