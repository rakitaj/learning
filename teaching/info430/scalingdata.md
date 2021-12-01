# Scaling Data
**One Thousand, One Million, One Billion - Data strategies for every size**
How, when, and why do we scale our data storage systems and our data model as we grow?
Which decisions are easy to change? Which are hard?

## Our Concepts

### Data storage system
What is a data storage system?
- It's anything that lets the application keep data between requests.
- Typically an external system to the application.
- Ideally it's failure tolerant to power loss, 

### Data storage system types
- Relational database
  - Client/server architecture: MySQL, PostgreSQL, MS SQL Server
  - "Filesystem based": SQLite3
- NoSQL database: MongoDB, Cassandra, PostgreSQL with JSON type
- Something completely homegrown (Spoiler alert - that's what we did)

### Data model
What is the data model?
- The application's view of the data.
- Application's view and use data differently from the data storage system.
- Object-relational impedance mismatch

### Data model vs data storage
TODO: Insert diagrams here of a database schema vs object collections or object graphs.


## Small application
- Keep it simple
- Data on one node or one system
- Use what you know best
- Figure out your requirements
  1. Be concrete not abstract![1]
  2. How many requests per second do you expect?
  3. What do your users expect
    - How much time do you have to respond to a request
    - Can you lose data
  4. What types of requests will you have, what is their load?
    - User creation or account registration
    - Read heavy, write heavy, or balanced?
    - Social media post? To one? To many?
    - What do you need to lookup?
    - Geographical access pattern

## Medium application
- Focus on scaling out vs scaling up
- Shard data
  - What key or keys will you shard on?
  - Beware of worst case scenarios shard sizes
- Tune your ORM queries

## Large application

### Latency numbers

**Note**: These numbers are from the references below and while the scale is correct, disks are much faster because they're SSDs instead of spinning drives.

| Action | Time |
|--------|------|
| L1 cache reference | 0.5 ns |
| Branch mispredict  |   5 ns |
| L2 cache reference |   7 ns |
| Mutex lock/unlock  | 100 ns |
| Main memory reference | 100 ns |
| Compress 1K bytes with Zippy | 10,000 ns |
| Send 2K bytes over 1 Gbps network | 20,000 ns |
| Read 1 MB sequentially from memory | 250,000 ns |
| Round trip within same datacenter | 500,000 ns |
| Disk seek | 10,000,000 ns |
| Read 1 MB sequentially from network | 10,000,000 ns |
| Read 1 MB sequentially from disk | 30,000,000 ns |
| Send packet CA->Netherlands->CA | 150,000,000 ns | 

### Exercises
1. 
1. How long does it take to do 1000 reads with a Python Flask application using SQLite3?
2. How long does it take to create 100 users? Why does it take this long?
3. Ballpark the magnitude of requests per second this system can handle

## References
1. [Google System Design Exercise](https://sre.google/workbook/non-abstract-design/)
2. [Latency Numbers Every Programmer Should Know](http://norvig.com/21-days.html#answers)
3. [Google Pro Tips](http://highscalability.com/blog/2011/1/26/google-pro-tip-use-back-of-the-envelope-calculations-to-choo.html)