## User Authentication And Authorization

Its not a fair game that anyone can update your TO-DO List. So we need to secure our application with some mechanism.

Predix out of the box has UAA as Service 
Checkout this service by typing ` cf marketplace -s predix-uaa `

This service is inspired by [Cloudfoundry/UAA](https://github.com/cloudfoundry/uaa) and API documentation [here](https://github.com/GESoftware-CF/uaa/blob/master/docs/UAA-APIs.rst#management-endpoints).

If you are not sure what [OAuth2](http://oauth.net/2/) / [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) works. Checkout some of the references given below.

## Long story short.

* Resource here is the entity `to-do`
* The User's (Resource Owner)  identity belongs to the some bigger ecosystem. For eg: Company SSO, Facebook, Google, Twitter, Yahoo etc.
* ` todo-server ` is Resource Server's. These operate on Resource.
* ` todo-client ` is the Client who wants to access the to-do list belonging to a  particular Owner/User

## What we want to accomplish

* [Create Predix UAA Instance](./creating_predix_uaa_instance.md)
* [Talking to UAA Instance](./talking_to_uaa_instace.md)
* [Registering Client](./registering_client_in_uaa.md)
* [Create Dummy Users](./create_dummy_users_in_uaa.md)
* [Getting Token For A User](./getting_token_from_uaa.md)

## References
* [SAML What it is](https://www.youtube.com/watch?v=50ogFCF56qE)
* [OAuth2](https://www.youtube.com/watch?v=io_r-0e3Qcw)
* [OAuth 2 Simplified](https://aaronparecki.com/articles/2012/07/29/1/oauth2-simplified)