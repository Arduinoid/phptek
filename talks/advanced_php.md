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

---------------------------------

# Day Three
## Data Visualization Pipline

### Extracting or Offloading work
- like not hitting the database during the first page load
- using a queue as a programming firewall

### what to Offloading
- does the site not respond depending on completing an item?
- can we process in bulk?

### worker pipeline
- one worker passe to the next
- assembly line (step one, step two, ...)

### implementation
- all flow down stream. no round trip, fire and for get.

### Tools
- [ELK stack](https://www.elastic.co/elk-stack)
    - Elasticsearch
    - Logstash
    - Kibana