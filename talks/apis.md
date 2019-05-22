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

