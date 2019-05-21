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