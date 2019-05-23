# Day One

## API's
## Design first 

*check out [joind.in](joind.in)*

> write decisions down -have documentation that all stake holders can see had have input on

### webhooks vs async api
- webhook is where you register interest first before hand 
- async api, you make an initial request with your interest and then later get back data

### authentication
pick a standard, any, just be consitant and not reinvent the wheel
> token based is a good option
- OAuth2
- JWT


### Error Behavior
- all endpoints consistent
- status codes for success/fail 
> use *RFC 8707* for reference

### Naming things is hard
get names reviewed by as many people as possible *(because you're probably wrong)*

### documentation tools
- source controlable
- quick creation
- easy to share
- painless maintain/update

> checkout slate for api docs

### API description language
> describing your API in detail that both humans and computers can understand

it can be use to...
- generate documentation
- make a mock server
- import collection into postmane
- outline server and client

---------------------------

## Token API

> you use your id to get a token to then prove you are who you say you are

### Token Types
- simple generated random text (api key)
- signed key (OAuth1)
- long (refresher token) and short lived (OAuth2)
- ♥ with claims (JWT)

### JWT (json web token)
> base64 encoded json. [rfc7519](https://tools.ietf.org/html/rfc7519)

**attributes:**
- header
- body
- signature

```json
# example of JWT
[
    {
        "alg": "HS256",
        "type": "JWT"
    },
    {
        "sub": "1234568",
        "name": "John Doe",
        "iat": "987654325"
    }
]
```

------------------

## API tools you should be using

getting to know HTTP

### Request
- host
- path
- method
- headers
- body

### response
- status
- headers
- body

### **HTTP** Vers
- **GET** (should be safe to book mark or make repeat requests)
- **POST**
- **DELETE**
- **PUT** (having the whole record making one or more changes and sending the whole thing back)
- **PATCH** (piecing together a record with only parts of the record fields)
- **HEAD**

## HTTP headers
- request headers: `Host`, `Accept`
- response header: ` ETag`, `Location`
- *something*: `Content-Type`

### tools
- curl, postman, insomnia
- [httpbin](https://httpbin.org)

--------------------------------

## API Gateway
an API gateway is a pattern

**[GraphQL playground](https://www.graphqlhub.com/)**

------------------
# Day Two
## Versioning: Everyway is the wrong way
**Speaker:** *TJ Lytle*

### Hard for creators because...
- more routing
- what to use for a default?
- perserve old Behavior
- duplicating behavior between versions

### Hard for consumers because...
- they have to set a versions
- update working
- more documentation

### First solution, add things don't change them
> just try to avoid versioning if possible
- add resources
- add properties

> **Example** Twilio in one of there API responses has a couple redundant fields that come back because they added new ones that were named more clearly
> without droping the ild fileds that some one may depend on.

### Resource concepts
- **REST** should tie a resource to an endpoint or URI (not necessarly the code that gets the resource but the resource like "user")
    - you may have a v1 and a v2 that both accesses a user resource but one has more info or data available
- you can put the version in the header if you want
```header
API-Version: 1
# or
Accept: application/vnd.resource+1
```
- **RPC** is very flexibale when it comes to URI usage
- **HTTP API** can use both URI and headers to specify resources
- **REST** should never change URI's

---------------
## Webhooks
**speaker:** *Lorna Mitchell, Nexmo*

> it's a HTTP POST request
- They are used to notify of events
- Deliver data when available
- Broadcasting to multiple clients

### How webhooks work
- instead of requiring the client to continue making requests to check for the availability of data the server will make a request to a URL that the client provides
- the relationship with the server is flipped. Provide a URL to the server that you can receive data to
- You do need to have some server or endpoint available to listen on the provided URL

### Designing webhooks: examples
- think about what the consumers will want when receiving a webhook
- prevent a bunch of reactionary API calls to your server as a result of a webhook calls
> use **[ngrok](https://ngrok.com/)** to test your webhooks
- send back acknowledgement to the webhook as a good practice
- Don't do any long running processing upon receiving a webhook because you should respond quickly
- differ long running process after responding to the sender

### Security
- it is not secure as is and you should be cautious about data coming back
- always use SSL
- use digital signing if possible or shared secret to verify the sender

### Handling request using queues
- protects against burst traffic
- this seporates work from the webserver
- Queues: redis, rabbitMQ, laraval - horizon, sqs, beanstalk

### Getting stuff off the queue with workers
> workers are long-running scripts that process a series of jobs
** workers need to be independent**
- if things go wrong, exit
- separate thing to monitor or restart (like a supervisor)
- may not process in order of receipt

### Publishing webhooks
> webhooks are an implementation of Pub/Sub
- Put webhooks into a queue when sending to steady the rate (using workers)
- do not send from a live webserver 

### Tools for workers
- supervisorsD

---------------

## Building First Class Client Libraries

