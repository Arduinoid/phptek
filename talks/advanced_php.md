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

-------------------

## Managing large data sets with streams

### you are already dealing with streams
- file()
- open()
- fwrite()
- fclose9)
- file_get_contents()
- file_put_contents()

### Stream Transports
> use `stream_get_transports()` to see what streams you have

### Stream Wrappers
`stream_get_wrappers()`

### Stream Filters
`stream_get_filters()`

### Stream Context


### save memory
`stream_copy_to_stream()`

```php
function handle()
{
    $source = fopen('some/path/to/something', 'rb');
    $destination = fopen('path/to/destination/file', 'w');
    stream_copy_to_stream($source, $destination);
}
```

> php-office for handling Excel files

---------------------

## Static analysis and strict types
**PHP Stan** and **PHP Phan** and **php inspection**

Phan is a static analyzer Tools

-------------------
## Application and Service Architecture

### Loose Coupling Services
- not aware of outside 
- interact through interfaces
- open/closed

### services are composable

### Service are abstract
- small and coherent set of logic
- details hidden
- services should be able to be implemented in any langauge
- interface segregation
- consumers of the service shouldn't need to change based on implementation changes in the service layer

### Services are discoverable
- consumers should be able to learn how to interact with it
- think of dependency injection (service locator)

### Service should be stateless
- should be cacheable
- application code shouldn't need to have state
- database state is ok

### Service should be portable
- not needing to live in one place on the network

### Contractual
- implement contracts
- legal inputs and outputs
- contracts between components in the application

### applications do a lot of nothing

> (micro)services

> front end controller with a service client that talks to all your services
