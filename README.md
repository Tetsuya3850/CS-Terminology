## Networking

### HTTP
HTTP, the Hyper Text Transfer Protocol, is the application protocol for transmitting hypermedia documents, such as HTML. Due to its extensibility, it is also used for fetching images and videos or to post content to servers. After the original request to fetch the HTML document, the web browser parses the file and makes additional HTTP requests corresponding to execution scripts, layout information (CSS) to display, and sub-resources contained within the page (usually images and videos). HTTP follows a client-server model, with a client (web browser) opening a connection to make a request, then waiting until it receives a response. HTTP is a stateless protocol, meaning that the server does not keep any data between two requests (cookies enable stateful sessions).

### HTTP Messages
Requests consists of an HTTP method (like GET, POST), the path of the resource to fetch, the version of the HTTP protocol, optional headers and a body (for POST). Responses consists of the version of the HTTP protocol, a status code indicating if the request has been successful or not (ex. 200, 404), a status message (short description of the status code), headers and optionally a body containing the fetched resource.

### TCP/IP
TCP (Transmission Control Protocol) is responsible for routing application protocols to the correct application on the destination computer. When the TCP layer receives the application layer protocol data from above, it segments it into manageable 'chunks' and then adds a TCP header to each 'chunk'. The information contained in the TCP header includes the port number of the application the data needs to be sent to. When the TCP layer receives a packet from the IP (Internet Protocol) layer below it, the TCP layer strips the TCP header data from the packet, does some data reconstruction if necessary, and then sends the data to the correct application using the port number taken from the TCP header. As such, while the TCP's job is to get application level data from application to application reliably, the task of getting data from computer to computer is the job of IP. IP packets are independent entities and may arrive out of order or not at all, but the TCP make sure packets arrive and are in the correct order (requests a resubmit if necessary). TCP is useful for applications that require high reliability but are less time critical. Some examples include web servers, database, SMTP, FTP, and SSH.

### IP Address
IP address is a network addressable location. Each IP address must be unique within its network. Any Internet-connected computer can be reached through a public IP Address, which consists of 32 bits for IPv4 (they are usually written as four numbers between 0 and 255, separated by dots (e.g., 173.194.121.32) or which consists of 128 bits for IPv6 (they are usually written as eight groups of 4 hexadecimal numbers, separated by colons (e.g., 2027:0da8:8b73:0000:0000:8a2e:0370:1337). Although computers can handle those addresses easily, people have a hard time finding out who's running the server or what service the website offers. To solve these problems we use human-readable addresses called domain names.

### DNS
DNS is a distributed database system which translates human-friendly domain names to numerical IP addresses. For example, www.google.com translates to 216.58.218.110. DNS is implemented as a distributed directory service. Each DNS server stores a database of domain names to IP addresses. If it cannot find a domain name being queried in this database, it forwards the request to other DNS servers. When the IP address is found, the original database will cache it to improve performance. DNS results can also be cached by your browser or OS.

### CORS
CORS (Cross-Origin Resource Sharing) is a mechanism that uses additional HTTP headers to let a user agent gain permission to access selected resources from a server on a different origin (domain) than the site currently in use. For security reasons, browsers restrict cross-origin HTTP requests initiated from within scripts. For example, XMLHttpRequest and the Fetch API follow the same-origin policy. 

### Cookie
Cookie is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. It remembers stateful information for the stateless HTTP protocol. Cookies are mainly used for session management (logins, shopping carts, game scores), personalization(user preferences and themes), and tracking(recording and analyzing user behavior).

### UDP
UDP (User Datagram Protocol), contrast to TCP, do not support congestion control (make sure all packets arrive and is in order) and connectionless (no need to establish connection prior to data transfer). Therefore, it is less reliable but more efficient. Use UDP over TCP when you need the lowest latency and late data is worse than loss of data. Examples are real time use cases such as VoIP (transmit voice messages over IP such as Skype), video chat, streaming, and realtime multiplayer games.

### Bandwidth/Throuhput/Latency
Bandwidth: Maximum amount of data that can be transferred in a unit of time. Typically expressed in bits per second.<br/>
Throughput: Actual amount of data that is transferred in a unit of time.<br/>
Latency: How long it takes data to go from one end to the other.<br/>

### SSL/TLS/HTTPS
SSL (Secure Sockets Layer) is the standard encryption technology for keeping an internet connection secure and safeguarding any sensitive data that is being sent between two systems, preventing criminals from reading and modifying any information. TLS (Transport Layer Security) is an updated, more secure successor version of SSL. HTTPS (Hyper Text Transfer Protocol Secure) appears in the URL when a website is secured by an SSL certificate.

### Serialization
The process whereby an object or data structure is translated into a format suitable for transferral over a network, or storage (e.g. in an array buffer or file format).

## System Design

### Horizontal/Vertical Scaling
Scaling vertically means adding more resources to an individual server. This might mean adding more hard drives so a single server can contain the entire data set, or moving the computation to a bigger server with a faster CPU or more memory. In each case, vertical scaling is accomplished by making the individual resource capable of handling more on its own. However, it can only scale to the best one machine on Earth. Scaling horizontally, on the other hand, is to add more nodes. This might be a second server to store parts of the data set, or splitting the operation or load across some additional nodes. 

### CAP Theorem
In a distributed computer system, you can only support two of the following guarantees:<br/>
Consistency - Every read receives the most recent write or an error<br/>
Availability - Every request receives a response, without guarantee that it contains the most recent version<br/>
Partition Tolerance - The system continues to operate despite arbitrary partitioning due to network failures<br/>
Networks aren't reliable, so you'll need to support partition tolerance. Therefore, the tradeoff is between consistency and availability. If you choose consistency, waiting for a response from the partitioned node might result in a timeout error. This is a good choice if your business needs require atomic reads and writes. If you choose availability, responses return the most recent version of the data available on the node, which might not be the latest. Writes might take some time to propagate when the partition is resolved. This is a good choice if the business needs allow for eventual consistency or when the system needs to continue working despite external errors.

### Consistency Patterns
Weak consistency: after write, reads may or may not be seen. ex VoIP, video chat, and multiplayer games (realtime). <br/>
Eventual consistency: after a write, reads will eventually see it (typically within milliseconds) ex DNS and email. <br/>
Strong consistency: after a write, data is replicated synchronously. ex file systems and RDBMSes.<br/>

### Availability/Reliability
Availability is a function of the percentage of time the system is operational.<br/>
Reliability is a function of the probability that the system is operational for a certain unit of time.<br/>

### Read-heavy/Write-heavy
If read-heavy, consider caching. If write-heavy, consider queuing up the writes.

### Load Balancing
Load balancing is the process of spreading requests across multiple resources according to some metric (random, round-robin, session/cookies, random with weighting for machine capacity, etc) and their current status (available for requests, near capacity, not responding, elevated error rate, etc) to achieve scalability and redundancy (if one server in a cluster of servers fail, the load balancer can temporarily remove that server from the cluster, and divide the load onto the functioning servers). Generally, servers should be stateless and functionaly identical. A moderately large system may balance load at three layers, user to web servers, web servers to an internal platform layer, internal platform layer to database. Load balancers can be implmented with hardware or software, but the hardware tends to be costly. One software solution is HAProxy. Load balancing is implemented by configuring a locally bound port for each service. Additional benefits of load balancers include, SSL termination (Decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations), session persistence (issue cookies and route a specific client's requests to same instance). In order not introduce another single point of failure, it is common to set up multiple load balancers.

### Reverse Proxy
A reverse proxy is a web server that centralizes internal services and provides unified interfaces to the public. Requests from clients are forwarded to a server that can fulfill it by the proxy. Additional benefits include, increased security (hide information about backend servers, blacklist IPs, limit number of connections per client), increased flexibility (clients only see the reverse proxy's IP, allowing you to scale servers or change their configuration), increased scalability (similar data access requests can be collapsed into one request), SSL termination (decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations). Load balancing solutions such as HAProxy can support reverse proxying as well.
 
### Caching
Caching stores copies of frequently accessed data as a key-value pair (e.g. Memcached instead of PostgreSQL.) Memcached and Redis are fast since they are in-memory, not disk. However, RAM space is generally far less than disk space, so only a hot subset of the data should be kept in cache. To decide which to hold, last recently used is a good strategy (recently requested data is likely to be requested again). By placing cache near to the front-end, it could instantly serve cached results and also mitigate the load to downstream backends. However, when the original data gets updated, relating cache data should be invalidated.

### Cache Invalidation
Cache-aside: The application is responsible for reading and writing from storage. The cache does not interact with storage directly. The application does the following: 1. Look for entry in cache, resulting in a cache miss 2. Load entry from the database 3. Add entry to cache 4. Return entry. Memcached is generally used in this manner. Cache-aside is also referred to as lazy loading. Only requested data is cached, which avoids filling up the cache with data that isn't requested. Disadvantages include, each cache miss results in three trips, which can cause a noticeable delay, data can become stale if it is updated in the database. This issue is mitigated by setting a time-to-live (TTL) which forces an update of the cache entry, or by using write-through.<br/>
Write-through cache: Under this scheme data is written into the cache and the corresponding database at the same time. The cached data allows for fast retrieval, and since the same data gets written in the permanent storage, we will have complete data consistency between cache and storage. Also, this scheme ensures that nothing will get lost in case of a crash, power failure, or other system disruptions. Although write through minimizes the risk of data loss, since every write operation must be done twice before returning success to the client, this scheme has the disadvantage of higher latency for write operations.<br/>
Write-around cache: This technique is similar to write through cache, but data is written directly to permanent storage, bypassing the cache. This can reduce the cache being flooded with write operations that will not subsequently be re-read, but has the disadvantage that a read request for recently written data will create a “cache miss” and must be read from slower back-end storage and experience higher latency.<br/>
Write-back cache: Under this scheme, data is written to cache alone, and completion is immediately confirmed to the client. The write to the permanent storage is done after specified intervals or under certain conditions. This results in low latency and high throughput for write-intensive applications, however, this speed comes with the risk of data loss in case of a crash or other adverse event because the only copy of the written data is in the cache.<br/>

### CDN
A content delivery network (CDN) is a globally distributed network of proxy servers, serving content from locations closer to the user. Generally, static files such as HTML/CSS/JS, photos, and videos are served. CDNs improve performance in two ways: Users receive content at data centers close to them. Servers do not have to serve requests that the CDN fulfills. In a typical CDN setup, a request will first ask the CDN for a piece of static media, the CDN will serve that content if it has it locally available. If it isn't available, the CDN will query the servers for the file and then cache it locally and serve it to the requesting user.

### Asynchronism
Asynchronous workflows help reduce request times for expensive operations that would otherwise be performed in-line. One example is a Message queue. First, an application publishes a job to the queue. Jobs could represent a simple write to a database, or generating a thumbnail preview image for a document. Then, a worker picks up the job from the queue, processes it, then signals the job is complete. The user is not blocked and the job is processed in the background. During this time, the client might optionally do a small amount of processing to make it seem like the task has completed (posting a tweet, the tweet could be instantly posted to your timeline, but it could take some time before your tweet is actually delivered to all of your followers). Message queues allow you to create a separate machine pool for performing off-line processing rather than burdening your web application servers. RabbitMQ and Amazon SQS are common tools to implement this. Queue sizes becoming larger than memory could result in cache misses, disk reads, and even slower performance. Therefore, limiting the queue size and informing clients that server is busy in such situation is important.

### Fail-Over
With active-passive fail-over, heartbeats are sent between the active and the passive server on standby. If the heartbeat is interrupted, the passive server takes over the active's IP address and resumes service. The length of downtime is determined by whether the passive server is already running in 'hot' standby or whether it needs to start up from 'cold' standby. <br/>
In active-active, both servers are managing traffic, spreading the load between them. If the servers are public-facing, the DNS would need to know about the public IPs of both servers. If the servers are internal-facing, application logic would need to know about both servers. Disadvantages of failover include, more hardware and additional complexity, potential loss of data if the active system fails before any newly written data can be replicated to the passive.

### MapReduce
MapReduce is targeting batch jobs where disk I/O is the major bottleneck. It uses a distributed file system so that disk I/O can be done in parallel. Map takes in some data and emits a <key, value> pair. Reduce takes a key and a set of associated values and reduces them in someway, emitting a new key and value. MapReduce allows a lot of processing to be done in parellel which makes processing huge amounts of data more scalable.

### HTTP Long-Polling
Long-Polling is a variation of the traditional polling technique that allows the server to push information to a client, whenever the data is available. With Long-Polling, the client requests information from the server exactly as in normal polling, but with the expectation that the server may not respond immediately. If the server does not have any data available for the client, instead of sending an empty response, the server holds the request and waits until some data becomes available. Once the data becomes available, a full response is sent to the client. The client then immediately re-request information from the server so that the server will almost always have an available waiting request that it can use to deliver data in response to an event.

### WebSocket
WebSocket provides full duplex communication channels over a single TCP connection. It provides a persistent connection between a client and a server that both parties can use to start sending data at any time. The WebSocket protocol enables real-time data transfer between the client and the server. 

## Database

### Replication
Master-Slave: The master serves reads and writes, replicating writes to one or more slaves, which serve only reads. Slaves can also replicate to additional slaves in a tree-like fashion. If the master goes offline, the system can continue to operate in read-only mode until a slave is promoted to a master or a new master is provisioned.<br/>
Master-Master: Both masters serve reads and writes and coordinate with each other on writes. If either master goes down, the system can continue to operate with both reads and writes. Most master-master systems are either loosely consistent (violating ACID) or have increased write latency due to synchronization.<br/>
Disadvantages of replication include, potential loss of data if the master fails before any newly written data can be replicated to other nodes, read replicas getting bogged down with replaying writes and can't do as many reads when there a lot of writes, and many read slaves leading to greater replication lag.

### Federation
Federation (or functional partitioning) splits up databases by function. For example, instead of a single, monolithic database, you could have three databases: forums, users, and products, resulting in divided and parallel read and write traffic to each database and therefore improving performance. Disadvantages include the necessity to update application logic to determine which database to read and write and joining data from two databases becoming more complex with a server link.

### Sharding
Sharding distributes data across different databases such that each database only manages a subset of the data. Common ways to shard a table include, through alphabetical, geolocation, hash key, random (with lookup table). This results in divided and paralell read and write traffic, less replication, and more cache hits. Index size is also reduced. If one shard goes down, the other shards are still operational, although you'll want to add some form of replication to avoid data loss. Disadvantages include, data distribution can become lopsided in a shard (a set of power users on a shard could result in increased load to that shard), rebalancing adds additional complexity(this is easy in lookup table based sharding), and joining data from multiple shards is more complex.

### Consistent Hashing
The basic idea behind the consistent hashing algorithm is to hash both objects and caches using the same hash function. The reason to do this is to map the cache to an interval, which will contain a number of object hashes. In the consistent hashing scheme, the key space is finite and lie on the circumference of a ring. The virtual node id is also allocated from the same key space. For any key, its owner node is defined as the first encountered virtual node if walking clockwise from that key. If the owner node crashes, all the key it owns will be adopted by its clockwise neighbor. Therefore, key redistribution happens only within the neighbor of the crashed node, all other nodes retains the same set of keys.

### Indexes
Indexes are used to improve the speed of data retrieval operations on the data store. An index makes the trade-offs of increased storage overhead, and slower writes (since we not only have to write the data but also have to update the index) for the benefit of faster reads. Indexes are used to quickly locate data without having to examine every row in a database table. It can be created using one or more columns of a database table. An index is a data structure that can be perceived as a table of contents that points us to the location where actual data lives.

### Relational Database
A relational database is a set of tables. Each table consists of rows and columns. Each row contains all the information about one entity, and columns are all the separate data points. The database schema must be predefined. Any changes in schema necessitates a migration procedure that can take the database offline or significantly reduce application performance. SQL is the language used to create and manipulate such databases. A key benefit of relational databases include support for ACID(Atomicity, Consistency, Isolation, Durability) transactions.

### ACID Transaction
ACID is a set of properties of relational database transactions.<br/>
Atomicity - Each transaction is all or nothing<br/>
Consistency - Any transaction will bring the database from one valid state to another<br/>
Isolation - Executing transactions concurrently has the same results as if the transactions were executed serially<br/>
Durability - Once a transaction has been committed, it will remain so<br/>

### Normalization/Denomalization
Normalization is to organize the database so as to minimize redunduncy. It involves decomposing tables utilizing foreign keys (a field in one table that uniquely identifies a row of another table). Denormalization on the other hand, adds redundant data to one or more tables so as to avoid expensive joins and improve performance. However, extra effort to update the database consistently (multiple fields to update at one time) and more storage are necessary. Therefore, a denormalized database under heavy write load might perform worse than its normalized counterpart. Once data becomes distributed with techniques such as federation and sharding, managing joins across data centers further increases complexity. 

### Join
Join is used to combine the results of two tables. To perform a join, each of the tables must have at least one field that will be used to find matching records from the other table.<br/>
Inner Join: The result set would contain only the data where the criteria match.<br/>
Outer Join: The result set also contains records that have no matching. The unmatched field will have a NULL value.<br/> 
Left Outer Join: The result will contain all records from the left table regardless of match.<br/>
Rgith Outer Join: The result will contain all records from the right table regardless of match.<br/>
Full Outer Join: The result will contain all records from both the left and right table regardless of match.<br/>

### Key-Value Database
A key-value store is an array of key-value pairs. It generally allows for O(1) reads and writes and is often backed by memory or SSD. Key-value stores provide high performance and are often used for simple data models or for rapidly-changing data, such as an in-memory cache layer. Since they offer only a limited set of operations, complexity is shifted to the application layer if additional operations are needed. Well-known key value stores include Redis and Dynamo.

### Document Database
A document store is centered around documents (XML, JSON, binary, etc), where a document stores all information for a given object (data is represented in the same way that applications do). This minimizes expensive joins and makes it easier for developers to reason about the data. Some document stores like MongoDB and CouchDB also provide a SQL-like language to perform complex queries. Although documents can be organized or grouped together, documents may have fields that are completely different from each other. Such high flexibility are often utilized for working with occasionally changing requirements and data.

### Column Database
A wide column store's basic unit of data is a column (name/value pair). A column can be grouped in column families (analogous to a SQL table). Super column families further group column families. You can access each column independently with a row key, and columns with the same row key form a row. Each value contains a timestamp for versioning and for conflict resolution. Google introduced Bigtable as the first wide column store, which influenced HBase and Cassandra. 

### Graph Database
In a graph database, each node is a record and each arc is a relationship between two nodes. Graph databases are optimized to represent complex relationships with many foreign keys or many-to-many relationships. Graphs databases offer high performance for data models with complex relationships, such as a social network. An example of graph database is Neo4J.

## Object Oriented Programming

### Object
A model of something defined by their state and behavior. For example, dogs have state (name, color, breed, hungry) and behavior (barking, fetching, wagging tail). The behavior defines their interaction with others.

### Class
Class is a template definition (blueprint) of an object. Object is an instance of the class.

### Interface
Interface is a group of related methods with empty bodies.

### Constructor
A constructor runs when a class object is instantiated. It initializes the object.

### Inheritance
To get commonly used state and behavior from other classes. Bicycle is the superclass of MountainBike, RoadBike, and TandemBike (IS-A relation). This avoids code duplication. Interfaces form a contract between the class and the outside world, and this contract is enforced at build time by the compiler. If your class claims to implement an interface, all methods defined by that interface must appear in its source code before the class will successfully compile.

### Encapsulation
To hide instance variables (make it private) and restrict access only by public getters and setters. Getters return instance variables, while setters receive an argument value and use it to set the value of an instance variable. By adding check condition to the setter, we could ensure the instance variable stays appropriate.

### Method Overriding
Subclass redefined one of its inherited methods when it needs to change or extend the behavior of that method.

### Favor Composition Over Inheritance
Code reuse should be achieved by assembling smaller units of functionality instead of inheriting from classes. In other words, use can-do, has-a, or uses-a relationships instead of is-a relationships.

### MVC
The Model-View-Controller (MVC) is an architectural pattern that organizes an application into three components: the model, the view, and the controller. The Model corresponds to the data-related logic. The View component is used for all the UI logic. Controllers act as an middle man between Model and View to process incoming requests, manipulate data using the Model component and interact with the Views to render the final output. Ruby on Rails.

## Hardware

### CPU
The CPU (Central Processing Unit) is what executes all the instructions. The faster the CPU is, the the faster the computer can execute instructions. Some CPUs have multiple cores. Each core functions like a separate CPU which can execute instructions independently, regardless of what the other cores are doing. 

### RAM
The RAM (Random Access Memory) can store both instructions for the CPU to execute, and the data these instructions are processing. The more memory a computer has, the more data and instructions it can store. The RAM is normally cleared when the computer is shut down or rebooted. It is typically not a permanent storage. Having a lot of memory in a computer is useful when caching data which normally reside on disk, or which is read from a remote system via the network.

### Disk Drives
The disk drives can store data just like the RAM, but unlike the RAM the data is saved even when the computer shuts down. The disk drives are often much slower than RAM to access, so if you need to process big amounts of data, it is preferable to keep that data in RAM.

### NIC
The NIC (Network Interface Card) connects the computer to a network. This enables the computer to communicate with other computers, for instance via the internet. 

### Bus
The Bus connects the CPU to the RAM, disk drives and NIC.

## Operating System

### OS
An Operating System (OS) is an interface between a user and computer hardware. It is responsible for managing all the processes that are running on a computer and allocating each process a certain amount of time to use the CPU and memory. To keep track of the state of all the processes, the operating system maintains a process table. The process table is an array of process control blocks (PCBs). PCB is used to track the process’s status (process identification number, process state, program counter, stack pointer, status of opened files, scheduling algorithms, etc). Only one process can be in the running state at any given time. The executed process will continue until it is interrupted by some external factor or it goes for an I/O task (context switch). The process state is saved to PCB and another process loads. This multi-programming maximizes the use of CPU since another process can use CPU while one is waiting for I/O.

### Process Scheduling Algorithms
First Come First Serve (FCFS): Schedules according to arrival times of processes.<br/>
Shortest Job First(SJF): Process which have the shortest burst time are scheduled first.<br/>
Shortest Remaining Time First(SRTF): Jobs are schedule according to shortest remaining time.<br/>
Round Robin Scheduling: Each process is assigned a fixed time in cyclic way.<br/>
Priority Based scheduling: Processes are scheduled according to their prioritie.s<br/>
These algorithms are either non-preemptive or preemptive. Preemptive scheduling is based on priority, where a scheduler may preempt a low priority running process anytime when a high priority process enters into a ready state.

### Process
A process is an instance of program in execution. A process can be divided into four sections ─ stack, heap, text and data. The process stack contains the temporary data such as method/function parameters, return address and local variables. Heap is dynamically allocated memory to a process during its run time. Text includes the current activity represented by the value of program counter and the contents of the processor's registers. Data contains the global and static variables. Processes can be in one of three states: running, ready, or waiting. The running state means that the process has been given permission by the operating system to use the processor. The remaining processes are either in a waiting state (i.e., waiting for some external event to occur such as user input or a disk access) or a ready state (i.e., waiting for permission to use the processor). Each process is executed in a separate address space and one process cannot access the variables and data structs of another process. If a process wishes to access another process resources, inter-process communications have to be used. These include pipes, files, sockets, and other forms.

### Thread
A thread is a single sequence stream within in a process. Threads are popular way to improve application through parallelism. For example, in a browser, multiple tabs can be different threads. MS word uses multiple threads, one thread to format the text, other thread to process inputs, etc. A thread has its own program counter, a register set, and a stack space. Threads are not independent of one other like processes as a result threads shares with other threads their code section, data section and OS resources like open files and signals. 

## Concurrency

### Race Condition
A race condition occurs when two or more threads access shared data at the same time. Because the thread scheduling algorithm can swap between threads at any time, you don't know the order in which the threads will attempt to access the shared data. Therefore, the result of the change in data is dependent on the thread scheduling algorithm, i.e. both threads are "racing" to access/change the data.

Problems occurs typically when one thread does a "check-then-act" (e.g. "check" if the value is X, then "act" to do something that depends on the value being X) and another thread does something to the value in between the "check" and the "act". E.g:

```
if (x == 5) // The "Check"
{
   y = x * 2; // The "Act"

   // If another thread changed x in between "if (x == 5)" and "y = x * 2" above,
   // y will not be equal to 10.
}
```

The point being, y could be 10, or it could be anything, depending on whether another thread changed x in between the check and act. You have no real way of knowing.

In order to prevent race conditions from occurring, you would typically put a lock around the shared data to ensure only one thread can access the data at a time (synchronization). This would mean something like this:

```
// Obtain lock for x
if (x == 5)
{
   y = x * 2; // Now, nothing can change x until the lock is released. 
              // Therefore y = 10
}
// release lock for x
```

### Deadlock
Deadlock is a situation when two or more processes wait for each other to finish and none of them ever finish. This happens in OS when for example, Process 1 is holding Resource 1 and waiting for resource 2 which is acquired by process 2, and process 2 is waiting for resource 1. Deadlock is handled by either prevention, detection and recovery, or ignore and reboot. Some strategies to avoid such situations include, requiring process to declare upfront what locks it will need and see each locks as a graph node and check whether a cycle exists or have a global ordering on locks and acquire them in that order.

### Livelock
Livelock is a situation where processes constantly change their state in regard to one another, withoub progress. A real-world example of livelock occurs when two people meet in a narrow corridor, and each tries to be polite by moving aside to let the other pass, but they end up swaying from side to side without making any progress because they both repeatedly move the same way at the same time. Livelock is a risk with some algorithms that detect and recover from deadlock. If more than one process takes action, the deadlock detection algorithm can be repeatedly triggered. This can be avoided by ensuring that only one process (chosen randomly or by priority) takes action. Consider two processes each waiting for a resource the other has but waiting in a non-blocking manner. When each learns they cannot continue they release their held resource and sleep for 30 seconds, then they retrieve their original resource followed by trying to the resource the other process held, then left, then reaquired. Since both processes are trying to cope (just badly), this is a livelock.

### Synchronization
Thread synchronization is defined as a mechanism which ensures that two or more concurrent processes or threads do not simultaneously execute some particular program segment known as critical section. Processes’ access to critical section is controlled by using synchronization techniques.

### Mutex
Mutex is locking mechanism used to synchronize access to a resource. Only one task (can be a thread or process based on OS abstraction) can acquire the mutex(binary flag). It means there is ownership associated with mutex, and only the owner can release the lock. 

### Semaphore
Semaphore is signaling mechanism. The two most common kinds of semaphores are counting semaphores and binary semaphores. Counting semaphore can take non-negative integer values and Binary semaphore can take the value 0 & 1. only.  Semaphores is used to limit the number of access to one resource.  By convention, when a semaphore is zero it is "locked" or "in use". Otherwise, positive values indicate that the semaphore is available.



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

### Function Signature
A function signature defines input, output, exceptions and visibility of functions.

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

### Compile
Compiling is the process of transforming a computer program written in a given language into an equivalent program of another language. A compiler is a software to execute this task. Usually, a compiler transforms a higher-level language such as C or Java, which humans understand, into a machine language, such as assembly, that the CPU can understand. Some compilers which translate between similar level languages are called transpilers or cross-compilers, for instance to compile from TypeScript to JavaScript. 

## Web Programming

### DOM
The Document Object Model is an api that will allow programs to dynamically access and update the content, structure and style of documents. The DOM represents the document as a node tree.

### Graceful Degradation/Progressive Enhancement
Graceful degradation is a design philosophy that centers around trying to build a modern web site/application that will work in the newest browsers, but fall back to an experience that while not as good still delivers essential content and functionality in older browsers.<br/>
Progressive enhancement is a design philosophy that centers around providing a baseline of essential content and functionality to as many users as possible, while at the same time going further and delivering the best possible experience only to users of the most modern browsers that can run all the required code.

### Cross Browser Testing
Use caniuse.com to check for feature support.<br/>
Autoprefixer for automatic vendor prefix insertion.<br/>
Feature detection using Modernizr.<br/>
Use CSS Feature queries @support<br/>

### Resetting/Normalizing
Resetting: Strip all default browser styling on elements.<br/>
Normalizing: Preserves useful default styles rather than "unstyling" everything.<br/>

### Position relative, absolute, fixed, static
relative:The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).<br/>
absolute - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.<br/>
fixed - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.<br/>
static - The default position; the element will flow into the page as it normally would. The top, right, bottom, left and z-index properties do not apply.<br/>




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
