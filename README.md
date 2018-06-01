## Networking

### IP
IP, the Internet Protocol's primary focus is to get individual packets from one host to another.

### TCP
TCP, the Transmission Control Protocol, is built on top of IP. It responds to dropped packets by requesting retransmits.

### HTTP
HTTP, the Hyper Text Transfer Protocol, is build on top of TCP.

### HTTPS
HTTPS is HTTP with SSL encryption. 

### DNS
DNS is the system which translates domain names to numerical IP addresses. For example, www.google.com translates to 216.58.218.110. DNS is implemented as a distributed directory service. Each DNS server stores a database of domain names to IP addresses. If it cannot find a domain name being queried in this database, it forwards the request to other DNS servers. To improve performance, caching is heavily used.

## Database

### Relational Database
A relational database is a set of tables. Each table consists of rows. A row is a set of columns, which could be of various types. SQL is the language used to create and manipulate such databases. A key benefit of relational databases include support for ACID(Atomicity, Consistency, Isolation, Durability) transactions.


### Normalization
Database normalization is to organize the database so as to minimize redunduncy. It involves decomposing tables utilizing foreign keys (a field in one table that uniquely identifies a row of another table). The drawback is performance, joins are expensive.

### JOIN
Join is used to combine the results of two tables. To perform a join, each of the tables must have at least one field that will be used to find matching records from the other table. INNER JOIN: The result set would contain only the data where the criteria match. OUTER JOIN: The result set would also contain records that have no matching in the other table. The unmatched field will have a NULL value. LEFT OUTER JOIN: The result will contain all records from the left table regardless of match. RIGHT OUTER JOIN: The result will contain all records from the right table regardless of match. FULL OUTER JOIN: The result will contain all records from both the left and right table regardless of match.
