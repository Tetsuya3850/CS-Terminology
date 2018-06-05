## Networking

### HTTP
HTTP, the Hyper Text Transfer Protocol, is the application protocol for transmitting hypermedia documents, such as HTML. Due to its extensibility, it is also used for fetching images and videos or to post content to servers. After the original request to fetch the HTML document, it then parses this file and fetches additional requests corresponding to execution scripts, layout information (CSS) to display, and sub-resources contained within the page (usually images and videos). The Web browser then mixes these resources to present to the user a complete document, the Web page. Scripts executed by the browser can fetch more resources in later phases and the browser updates the Web page accordingly. HTTP follows a client-server model, with a client (web browser) opening a connection to make a request, then waiting until it receives a response. HTTP is a stateless protocol, meaning that the server does not keep any data between two requests. However, HTTP cookies allow the use of stateful sessions. 

### HTTP Messages
Requests consists of an HTTP method (like GET, POST), the path of the resource to fetch, the version of the HTTP protocol, optional headers and a body(for POST). Responses consists of the version of the HTTP protocol, a status code indicating if the request has been successful or not (ex. 200, 404), a status message (short description of the status code), headers and optionally a body containing the fetched resource.

### HTTP/2

### HTTPS
HTTPS is HTTP with SSL encryption. 

### TCP/IP
TCP (Transmission Control Protocol) is responsible for routing application protocols to the correct application on the destination computer. When the TCP layer receives the application layer protocol data from above, it segments it into manageable 'chunks' and then adds a TCP header to each 'chunk'. The information contained in the TCP header includes the port number of the application the data needs to be sent to. When the TCP layer receives a packet from the IP (Internet Protocol) layer below it, the TCP layer strips the TCP header data from the packet, does some data reconstruction if necessary, and then sends the data to the correct application using the port number taken from the TCP header. Notice that there is no place for an IP address in the TCP header. This is because TCP doesn't know anything about IP addresses. TCP's job is to get application level data from application to application reliably. The task of getting data from computer to computer is the job of IP. IP packets are independent entities and may arrive out of order or not at all. It is TCP's job to make sure packets arrive and are in the correct order.

### IP Address
IP (Internet Protocol) address is a network addressable location. Each IP address must be unique within its network. The addresses are in the form nnn.nnn.nnn.nnn where nnn must be a number from 0 - 255. Any Internet-connected computer can be reached through a public IP Address, which consists of 32 bits for IPv4 (they are usually written as four numbers between 0 and 255, separated by dots (e.g., 173.194.121.32) or which consists of 128 bits for IPv6 (they are usually written as eight groups of 4 hexadecimal numbers, separated by colons (e.g., 2027:0da8:8b73:0000:0000:8a2e:0370:1337). Computers can handle those addresses easily, but people have a hard time finding out who's running the server or what service the website offers. IP addresses are hard to remember and might change over time. To solve all those problems we use human-readable addresses called domain names.

### DNS
DNS is a distributed database system which translates human-friendly domain names to numerical IP addresses. For example, www.google.com translates to 216.58.218.110. DNS is implemented as a distributed directory service. Each DNS server stores a database of domain names to IP addresses. If it cannot find a domain name being queried in this database, it forwards the request to other DNS servers. To improve performance, caching is heavily used. DNS results can also be cached by your browser or OS for a certain period of time,

### CORS
CORS (Cross-Origin Resource Sharing) is a mechanism that uses additional HTTP headers to let a user agent gain permission to access selected resources from a server on a different origin (domain) than the site currently in use. A user agent makes a cross-origin HTTP request when it requests a resource from a different domain, protocol, or port than the one from which the current document originated. For security reasons, browsers restrict cross-origin HTTP requests initiated from within scripts. For example, XMLHttpRequest and the Fetch API follow the same-origin policy. This means that a web application using those APIs can only request HTTP resources from the same domain the application was loaded from unless CORS headers are used.

### Cookie
Cookie is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. It remembers stateful information for the stateless HTTP protocol. Cookies are mainly used for session management (logins, shopping carts, game scores), personalization(user preferences and themes), and tracking(recording and analyzing user behavior).

### Bandwidth Latency

## Security

### DoS Attack
DoS (Denial of Service) is a network attack that prevents legitimate use of server resources by flooding the server with requests. Computers have limited resources, for example computation power or memory. When these are exhausted, the program can freeze or crash, making it unavailable. A DoS attack consists of various techniques to exhaust these resources and make a server or a network unavailable to legitimate users, or at least make the server perform sluggishly.

### XSS
Cross-site scripting (XSS) is a security exploit which allows an attacker to inject into a website malicious client-side code. This code is executed by the victims and lets the attackers bypass access controls and impersonate users. These attacks succeed if the Web app does not employ enough validation or encoding. The user's browser cannot detect the malicious script is untrustworthy, and so gives it access to any cookies, session tokens, or other sensitive site-specific information, or lets the malicious script rewrite the HTML content. Cross-site scripting attacks usually occur when 1) data enters a Web app through an untrusted source (most often a Web request) or 2) dynamic content is sent to a Web user without being validated for malicious content. The malicious content often includes JavaScript, but sometimes HTML, Flash, or any other code the browser can execute. The variety of attacks based on XSS is almost limitless, but they commonly include transmitting private data like cookies or other session information to the attacker, redirecting the victim to a webpage controlled by the attacker, or performing other malicious operations on the user's machine under the guise of the vulnerable site. XSS attacks can be put into three categories: stored (also called persistent), reflected (also called non-persistent), or DOM-based.

### CSRF
CSRF (Cross-Site Request Forgery) is an attack that impersonates a trusted user and sends a website unwanted commands. This can be done, for example, by including malicious parameters in a URL behind a link that purports to go somewhere else.

### SQL Injection
SQL injection is a code injection technique that might destroy your database. SQL injection is the placement of malicious code in SQL statements, via web page input. SQL injection usually occurs when you ask a user for input, like their username/userid, and instead of a name/id, the user gives you an SQL statement that you will unknowingly run on your database.To protect a web site from SQL injection, you can use SQL parameters. SQL parameters are values that are added to an SQL query at execution time, in a controlled manner.

## Object Oriented Programming

### Favor Composition Over Inheritance
Code reuse should be achieved by assembling smaller units of functionality instead of inheriting from classes. In other words, use can-do, has-a, or uses-a relationships instead of is-a relationships.

### MVC
The Model-View-Controller (MVC) is an architectural pattern that organizes an application into three components: the model, the view, and the controller. The Model corresponds to the data-related logic. The View component is used for all the UI logic. Controllers act as an middle man between Model and View to process incoming requests, manipulate data using the Model component and interact with the Views to render the final output. Ruby on Rails.

## Functional Programming

### Pure Function
A function that given the same input, will always return the same output. Produces no side effects (it can’t alter any external state). Since they are independent of outside state, bugs that have to do with shared mutable state can be avoided. 

### Side Effect
Modifying external variable or object property (e.g., a global variable, or a variable in the parent function)<br/>
Logging to the console<br/>
Writing to the screen, a file or to the network<br/>

## System Design

### Load Balancing
Load balancing is the process of spreading requests across multiple resources according to some metric (random, round-robin, session/cookies, random with weighting for machine capacity, etc) and their current status (available for requests, not responding, elevated error rate, etc) to achieve scalability and redundancy. A moderately large system may balance load at three layers, user to web servers, web servers to an internal platform layer, internal platform layer to database. Load balancers can be implmented with hardware or software, but the hardware tends to be costly. One famous software solution is HAProxy, where for each service you want to load-balance, a locally bound port should be configured. Additional benefits of load balancers include, SSL termination (Decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations), session persistence (issue cookies and route a specific client's requests to same instance if the web apps do not keep track of sessions). To protect against failures, it's common to set up multiple load balancers.
 
### Caching
Caching consists of: precalculating results (e.g. the number of visits from each referring domain for the previous day), pre-generating expensive indexes (e.g. suggested stories based on a user's click history), and storing copies of frequently accessed data in a faster backend (e.g. Memcached instead of PostgreSQL.) Memcached and Redis are fast since they are in-memory, not disk. However, RAM space is generally far less than disk space, so you should only keep a hot subset of your data in cache. To decide which to hold, last recently used is a good strategy (recently requested data is likely to be requested again). By placing cache near to the front-end, it could  instantly serve the results and also mitigate the load to downstream backends. However, when the original data gets updated, relating cache data should be invalidated. The solution is, each time a value changes, write the new value into the cache (this is called a write-through cache) or simply delete the current value from the cache and allow a read-through cache to populate it later. Adding fixed expirations to cached data is also an important strategy. Multiple caches makes the problem yet trickier.


### Horizontal / Vertical Scaling
Scale up, Scale out.

Scaling vertically means adding more resources to an individual server. This might mean adding more hard drives so a single server can contain the entire data set, or moving the computation to a bigger server with a faster CPU or more memory. In each case, vertical scaling is accomplished by making the individual resource capable of handling more on its own.

Scaling horizontally, on the other hand, is to add more nodes. This might be a second server to store parts of the data set, or splitting the operation or load across some additional nodes. One of the more common techniques is to break up your services into partitions, or shards. The partitions can be distributed such that each logical set of functionality is separate; this could be done by geographic boundaries, or by another criteria like non-paying versus paying users.


### Stateless/Stateful System
A stateless system's output depends only on the input. A stateful system's output depends on the input and internal state. Therefore, the same set of input can generate different output. This makes multiple actors accessing the system a trickier problem.

### Latency / Throughput
Latency is the time to perform some action or to produce some result. Throughput is the number of such actions or results per unit of time. Generally, you should aim for maximal throughput with acceptable latency.


### CAP Theorem
In a distributed computer system, you can only support two of the following guarantees:
Consistency - Every read receives the most recent write or an error<br/>
Availability - Every request receives a response, without guarantee that it contains the most recent version<br/>
Partition Tolerance - The system continues to operate despite arbitrary partitioning due to network failures<br/>
Networks aren't reliable, so you'll need to support partition tolerance. Therefore, the tradeoff is between consistency and availability. If you choose consistency, waiting for a response from the partitioned node might result in a timeout error. CP is a good choice if your business needs require atomic reads and writes. If you choose availability, responses return the most recent version of the data available on the a node, which might not be the latest. Writes might take some time to propagate when the partition is resolved. AP is a good choice if the business needs allow for eventual consistency or when the system needs to continue working despite external errors.

### Consistency
Weak consistency (After a write, reads may or may not see it. A best effort approach is taken.) is seen in systems such as memcached. Weak consistency works well in real time use cases such as VoIP, video chat, and realtime multiplayer games. For example, if you are on a phone call and lose reception for a few seconds, when you regain connection you do not hear what was spoken during connection loss.<br/>
Eventual consistency (After a write, reads will eventually see it typically within milliseconds, data is replicated asynchronously.) This approach is seen in systems such as DNS and email. Eventual consistency works well in highly available systems.<br/>
Strong consistency (After a write, reads will see it. Data is replicated synchronously.) This approach is seen in file systems and RDBMSes. Strong consistency works well in systems that need transactions.<br/>

### Fail-Over
With active-passive fail-over, heartbeats are sent between the active and the passive server on standby. If the heartbeat is interrupted, the passive server takes over the active's IP address and resumes service. The length of downtime is determined by whether the passive server is already running in 'hot' standby or whether it needs to start up from 'cold' standby. Only the active server handles traffic. In active-active, both servers are managing traffic, spreading the load between them. If the servers are public-facing, the DNS would need to know about the public IPs of both servers. If the servers are internal-facing, application logic would need to know about both servers. Disadvantages of failover are, more hardware and additional complexity, potential loss of data if the active system fails before any newly written data can be replicated to the passive.

### Replication
Master-Slave: The master serves reads and writes, replicating writes to one or more slaves, which serve only reads. Slaves can also replicate to additional slaves in a tree-like fashion. If the master goes offline, the system can continue to operate in read-only mode until a slave is promoted to a master or a new master is provisioned.<br/>
Master-Master: Both masters serve reads and writes and coordinate with each other on writes. If either master goes down, the system can continue to operate with both reads and writes. Most master-master systems are either loosely consistent (violating ACID) or have increased write latency due to synchronization.<br/>
Disadvantages of replication include, potential loss of data if the master fails before any newly written data can be replicated to other nodes, read replicas can get bogged down with replaying writes and can't do as many reads when there a lot of writes, more read slaves leads to greater replication lag.

### Federation
Federation (or functional partitioning) splits up databases by function. For example, instead of a single, monolithic database, you could have three databases: forums, users, and products, resulting in less read and write traffic to each database and therefore less replication lag. Smaller databases result in more data that can fit in memory, which in turn results in more cache hits due to improved cache locality. With no single central master serializing writes you can write in parallel, increasing throughput. Disadvantages include the necessity to update application logic to determine which database to read and write and joining data from two databases is more complex with a server link.

### Sharding
Sharding distributes data across different databases such that each database can only manage a subset of the data. Taking a users database as an example, as the number of users increases, more shards are added to the cluster. Sharding results in less read and write traffic, less replication, and more cache hits. Index size is also reduced, which generally improves performance with faster queries. If one shard goes down, the other shards are still operational, although you'll want to add some form of replication to avoid data loss. Like federation, there is no single central master serializing writes, allowing you to write in parallel with increased throughput. Common ways to shard a table of users is either through the user's last name initial or the user's geographic location. Disadvantages include, need to update your application logic to work with shards, which could result in complex SQL queries, data distribution can become lopsided in a shard ( a set of power users on a shard could result in increased load to that shard compared to others), rebalancing adds additional complexity (sharding function based on consistent hashing can reduce the amount of transferred data, joining data from multiple shards is more complex.

### Denormalization
Denormalization improves read performance at the expense of some write performance. Redundant copies of the data are written in multiple tables to avoid expensive joins. Once data becomes distributed with techniques such as federation and sharding, managing joins across data centers further increases complexity. Disadvantages include, data duplication, a denormalized database under heavy write load might perform worse than its normalized counterpart.


### Reverse Proxy
A reverse proxy is a web server that centralizes internal services and provides unified interfaces to the public. Requests from clients are forwarded to a server that can fulfill it before the reverse proxy returns the server's response to the client. Additional benefits include, increased security (hide information about backend servers, blacklist IPs, limit number of connections per client), increased scalability and flexibility (clients only see the reverse proxy's IP, allowing you to scale servers or change their configuration), SSL termination (decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations), compress server responses, return the response for cached requests, serve static content directly. Load balancing solutions such as HAProxy can support reverse proxying as well.

### Application Layer
Separating out the web layer from the application layer (also known as platform layer) allows you to scale and configure both layers independently. Adding a new API results in adding application servers without necessarily adding additional web servers. The single responsibility principle advocates for small and autonomous services that work together. Small teams with small services can plan more aggressively for rapid growth. Related to this discussion are microservices, which can be described as a suite of independently deployable, small, modular services. Each service runs a unique process and communicates through a well-defined, lightweight mechanism to serve a business goal. Systems such as Consul, Etcd, and Zookeeper can help services find each other by keeping track of registered names, addresses, and ports



### ACID Transaction
ACID is a set of properties of relational database transactions.
Atomicity - Each transaction is all or nothing<br/>
Consistency - Any transaction will bring the database from one valid state to another<br/>
Isolation - Executing transactions concurrently has the same results as if the transactions were executed serially<br/>
Durability - Once a transaction has been committed, it will remain so<br/>

### SQL / NoSQL
Reasons for SQL:

Structured data
Strict schema
Relational data
Need for complex joins
Transactions
Clear patterns for scaling
More established: developers, community, code, tools, etc
Lookups by index are very fast
Reasons for NoSQL:

Semi-structured data
Dynamic or flexible schema
Non-relational data
No need for complex joins
Store many TB (or PB) of data
Very data intensive workload
Very high throughput for IOPS
Sample data well-suited for NoSQL:

Rapid ingest of clickstream and log data
Leaderboard or scoring data
Temporary data, such as a shopping cart
Frequently accessed ('hot') tables
Metadata/lookup tables


### Key-Value Database
A key-value store generally allows for O(1) reads and writes and is often backed by memory or SSD. Data stores can maintain keys in lexicographic order, allowing efficient retrieval of key ranges. Key-value stores can allow for storing of metadata with a value. Key-value stores provide high performance and are often used for simple data models or for rapidly-changing data, such as an in-memory cache layer. Since they offer only a limited set of operations, complexity is shifted to the application layer if additional operations are needed.

### Document Database
A document store is centered around documents (XML, JSON, binary, etc), where a document stores all information for a given object. Document stores provide APIs or a query language to query based on the internal structure of the document itself. Note, many key-value stores include features for working with a value's metadata, blurring the lines between these two storage types. Based on the underlying implementation, documents are organized in either collections, tags, metadata, or directories. Although documents can be organized or grouped together, documents may have fields that are completely different from each other. Some document stores like MongoDB and CouchDB also provide a SQL-like language to perform complex queries. DynamoDB supports both key-values and documents. Document stores provide high flexibility and are often used for working with occasionally changing data.

### Column Database
A wide column store's basic unit of data is a column (name/value pair). A column can be grouped in column families (analogous to a SQL table). Super column families further group column families. You can access each column independently with a row key, and columns with the same row key form a row. Each value contains a timestamp for versioning and for conflict resolution. Google introduced Bigtable as the first wide column store, which influenced the open-source HBase often-used in the Hadoop ecosystem, and Cassandra from Facebook. Stores such as BigTable, HBase, and Cassandra maintain keys in lexicographic order, allowing efficient retrieval of selective key ranges. Wide column stores offer high availability and high scalability. They are often used for very large data sets.

### Graph Database
In a graph database, each node is a record and each arc is a relationship between two nodes. Graph databases are optimized to represent complex relationships with many foreign keys or many-to-many relationships. Graphs databases offer high performance for data models with complex relationships, such as a social network. They are relatively new and are not yet widely-used; it might be more difficult to find development tools and resources. Many graphs can only be accessed with REST APIs. Neo4j

### Message queues
For processing you'd like to perform inline with a request but is too slow, the easiest solution is to create a message queue (for example, RabbitMQ). Message queues allow your web applications to quickly publish messages to the queue, and have other consumers processes perform the processing outside the scope and timeline of the client request.

Dividing work between off-line work handled by a consumer and in-line work done by the web application depends entirely on the interface you are exposing to your users. Generally you'll either:

perform almost no work in the consumer (merely scheduling a task) and inform your user that the task will occur offline, usually with a polling mechanism to update the interface once the task is complete (for example, provisioning a new VM on Slicehost follows this pattern), or
perform enough work in-line to make it appear to the user that the task has completed, and tie up hanging ends afterwards (posting a message on Twitter or Facebook likely follow this pattern by updating the tweet/message in your timeline but updating your followers' timelines out of band; it's simple isn't feasible to update all the followers for a Scobleizer in real-time).

Message queues have another benefit, which is that they allow you to create a separate machine pool for performing off-line processing rather than burdening your web application servers. This allows you to target increases in resources to your current performance or throughput bottleneck rather than uniformly increasing resources across the bottleneck and non-bottleneck systems.

### MapReduce
If your large scale application is dealing with a large quantity of data, at some point you're likely to add support for map-reduce, probably using Hadoop, and maybe Hive or HBase.
Adding a map-reduce layer makes it possible to perform data and/or processing intensive operations in a reasonable amount of time. You might use it for calculating suggested users in a social graph, or for generating analytics reports.

For sufficiently small systems you can often get away with adhoc queries on a SQL database, but that approach may not scale up trivially once the quantity of data stored or write-load requires sharding your database, and will usually require dedicated slaves for the purpose of performing these queries (at which point, maybe you'd rather use a system designed for analyzing large quantities of data, rather than fighting your database).

### HTTP Caching

### Reverse Proxy

### Platform layer
platform layer, such that your web applications communicate with a platform layer which in turn communicates with your databases.
First, separating the platform and web application allow you to scale the pieces independently. If you add a new API, you can add platform servers without adding unnecessary capacity for your web application tier. (Generally, specializing your servers' role opens up an additional level of configuration optimization which isn't available for general purpose machines; your database machine will usually have a high I/O load and will benefit from a solid-state drive, but your well-configured application server probably isn't reading from disk at all during normal operation, but might benefit from more CPU.)

Second, adding a platform layer can be a way to reuse your infrastructure for multiple products or interfaces (a web application, an API, an iPhone app, etc) without writing too much redundant boilerplate code for dealing with caches, databases, etc.

Third, a sometimes underappreciated aspect of platform layers is that they make it easier to scale an organization. At their best, a platform exposes a crisp product-agnostic interface which masks implementation details. If done well, this allows multiple independent teams to develop utilizing the platform's capabilities, as well as another team implementing/optimizing the platform itself.

### CDN
A content delivery network (CDN) is a globally distributed network of proxy servers, serving content from locations closer to the user. Generally, static files such as HTML/CSS/JS, photos, and videos are served. CDNs improve performance in two ways: Users receive content at data centers close to them. Your servers do not have to serve requests that the CDN fulfills. In a typical CDN setup, a request will first ask your CDN for a piece of static media, the CDN will serve that content if it has it locally available. If it isn't available, the CDN will query your servers for the file and then cache it locally and serve it to the requesting user.

### Read-Heavy/Write-Heavy System

## Programming Language

### Scope
Scope is the set of rules that determines where and how a variable can be looked-up. 

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

### Type
A type is an intrinsic, built-in set of characteristics that uniquely identifies the behavior of a particular value and distinguishes it from other values, both to the engine and to the developer.

### Value copy / Reference copy
Primitives are always assigned/passed by value-copy: null, undefined, string, number, boolean, and ES6's symbol.<br/>
Compound values (object and functions) always create a copy of the reference on assignment or passing.

```
var a = 2;
var b = a;
b++;
a; // 2
b; // 3

var c = [1, 2, 3];
var d = c;
d.push(4);
c; // [1, 2, 3, 4]
d; // [1, 2, 3, 4]
```

### Garbage Collection
Garbage Collection is the process of finding data objects in a running program that cannot be accessed in the future, and to reclaim the resources, particulary memory, used by those objects. In Java, C#, Python and many other languages, garbage collection happens automatically. In contrast, in writing C, the programmer is responsible to know when to allocate and deallocate memory.

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

### Cross Browser Testing
・Use caniuse.com to check for feature support.
・Autoprefixer for automatic vendor prefix insertion.
・Feature detection using Modernizr.
・Use CSS Feature queries @support

## CSS

### Resetting/Normalizing
Resetting: Strip all default browser styling on elements.
Normalizing: Preserves useful default styles rather than "unstyling" everything.

### Position relative, absolute, fixed, static
relative:The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).<br/>
absolute - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.<br/>
fixed - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.<br/>
static - The default position; the element will flow into the page as it normally would. The top, right, bottom, left and z-index properties do not apply.<br/>


## Performance

### Minification



## JavaScript

### this
“this” is not an author-time binding but a runtime binding. It is contextual based on the conditions of the function's invocation. this binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called. When a function is invoked, an activation record, otherwise known as an execution context, is created. This record contains information about where the function was called from (the call-stack), how the function was invoked, what parameters were passed, etc. One of the properties of this record is this reference which will be used for the duration of that function's execution. Determining the this binding for an executing function requires finding the direct call-site of that function. Once examined, four rules can be applied to the call-site, in this order of precedence:
1 Called with new? Use the newly constructed object.<br/>
2 Called with call or apply (or bind)? Use the specified object.<br/>
3 Called with a context object owning the call? Use that context object.<br/>
4 Default: undefined in strict mode, global object otherwise.<br/>

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

### var, let, const
While var is function scoped, let and const are block scoped. const creates a variable name binding which can’t be reassigned (it does not create immutable objects, you can still change the properties of the object). let can be reassigned.

### Promise
A promise is an synchronously returned object from an asynchronous function that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

### Asynchronous programming
Asynchronous programming means that the engine runs in an event loop. When a blocking operation is needed, the request is started, and the code keeps running without blocking for the result. When the response is ready, an interrupt is fired, which causes an event handler to be run, where the control flow continues. In this way, a single program thread can handle many concurrent operations.
