# Python-Projects

# Rest api With Authorization and mongodb: 

 

 

* https://github.com/vikasdo/Pan_card_restapi 
*  [demo](https://youtu.be/iqyrj7DXfDg)

 

## Libraries 

* Flask Restex(Flask-RESTX is an extension for Flask that adds support for quickly building REST APIs.)
* MongoEngine
* python ORM for MongoDB. 
* Flask-JWT-Extended for managing authentication using JWT Bearer tokens. 

There are two main collections, a User collection for which token would be generated, and a PanClient collection which will be related to the User collection. For each new verification request a new client with client_id will be generated. 

 implemented Bearer Token authentication, where with a secret password you can generate a Bearer Token(JWT token), which will be used in further requests. 

There should be 3 endpoints: 

One where you would generate a Auth token which could be used in further requests. 

One where you would take the pan number as input, parse it for bad input, and return the response, whether the PAN number is wrong, or some error occured, or the successful response. 

And one last endpoint where the user can submit the client_id received in second endpoint and get the saved data. 

Endpoints second and third(as mentioned above) are only be accessible via the Bearer token. And the First request should only be accessible via a pre-shared secret 
