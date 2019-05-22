# Day Two
## Producer Consumer Programming

> if there's data in the database that is not used to load the site then get it out of master

### Resuce
- put your stuff in a queue
- put stuff in an offline database

### big picture
- pro/con is not the an end in itself

**Tools**
- [CloudAMQP](https://www.cloudamqp.com/)

### Strategy for large data
- Store the data in a key/value store like redis
- put the key from the store in the queue for the workers to consume and reference
