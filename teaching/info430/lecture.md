# One Thousand, One Million, One Billion - Data strategies for every size
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


## Data model for a small application
- Keep it simple
- Data on one node or one system
- Use what you know best
- Be concrete not abstract![^1]
  1. How many requests per second do you expect?
  2. What do your users expect
    - How much time do you have to respond to a request
    - Can you lose data
  2. What types of requests will you have, what is their load?
    - User creation or account registration
    - Read heavy, write heavy, or balanced?
    - Social media post? To one? To many?
    - What do you need to lookup?
    - Geographical access pattern

### 
| Action | Lower bound | Upper Bound |
|--------|-------------|-------------|
| User count | 5 | 100,000 |
| Requests per second | 0 | 


### Exercises
1. How long does it take to do 1000 reads with a Python Flask application using SQLite3?
2. How long does it take to create 100 users? Why does it take this long?
3. Ballpark the magnitude of requests per second this system can handle

## References
[^1]: [Google System Design Exercise](https://sre.google/workbook/non-abstract-design/)