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

