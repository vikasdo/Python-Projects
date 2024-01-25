# Python-Projects


## QEATS:  

Fashioned a Django app ‘Qeats’ as a part of crio development with the help of my mentors .This Restaurant App helps restaurant owners and managers in managing their menu (items, availability, prices), order preparation time, order status, order history, and order notifications.  

Link : https://github.com/vikasdo/Django-qeats  

 
 

## CRD OPERATION ON A MULTITHREADED KEY VALUE STORE : 
Created a key value db like redis with timeout and other features and a robust db which can work by using multiple threads at one time. 

 Link : https://github.com/vikasdo/DbStore 
 
## Rest api With Authorization(JWT) and mongodb: 

 

 

* https://github.com/vikasdo/Pan_card_restapi 
*  [demo](https://youtu.be/iqyrj7DXfDg)

 

### Libraries 

* Flask Restex(Flask-RESTX is an extension for Flask that adds support for quickly building REST APIs.)
* MongoEngine
* python ORM for MongoDB. 
* Flask-JWT-Extended for managing authentication using JWT Bearer tokens. 

There are two main collections, a User collection for which token would be generated, and a PanClient collection which will be related to the User collection. For each new verification request a new client with client_id will be generated. 

 implemented Bearer Token authentication, where with a secret password you can generate a Bearer Token(JWT token), which will be used in further requests. 

There are  3 endpoints: 
```
1. One where you would generate a Auth token which could be used in further requests. 

2. One where you would take the pan number as input, parse it for bad input, and return the response, whether the PAN number is wrong, or some error occured, or the successful response. 

3.  one last endpoint where the user can submit the client_id received in second endpoint and get the saved data. 
Endpoints second and third(as mentioned above) are only be accessible via the Bearer token. And the First request should only be accessible via a pre-shared secret 
```
##  Tiny url
https://github.com/vikasdo/tiny_url

## Rest api With AWS s3 Lambda  pdf_rotater

Input :

- REST API  will take a given PDF file, angle of rotation, page number

Output:

- The API will rotate the specified page in the given angle and replace that page back into the PDF. 

Sending  Multipart/Form-Data using API Gateway(aws)  and a Python Lambda Proxy for storage in S3

For api we are sending the Request  in the form of Multipart/Form-Data .
Why should we use Multipart-formdata rather we can also use binary data file (but in this we need to send file along with the other parameters like page_num and angle of rotation"

- But there is one more problem  in handling multipart form data( some referrences i found )- https://blog.marcinbudny.com/2014/02/sending-binary-data-along-with-rest-api.html
- so here is the code we used  (the requests_toolbelt library)

```

  from requests_toolbelt.multipart import decoder
    content_type_header = event['headers']['Content-Type']
    postdata = base64.b64decode(event['body']).decode('iso-8859-1')
    imgInput = ''
    lst = []
    out={}

    # Need this line as it does 'b'b'pdfdatacontent'.
    

    for part in decoder.MultipartDecoder(postdata.encode('utf-8'), content_type_header).parts:
 


        disposition = part.headers[b'Content-Disposition']
        params = {}
        for dispPart in str(disposition).split(';'):
            kv = dispPart.split('=', 2)
            params[str(kv[0]).strip()] = str(kv[1]).strip('\"\'\t \r\n') if len(kv)>1 else str(kv[0]).strip()
        type = part.headers[b'Content-Type'] if b'Content-Type' in part.headers else None
        out[ params["name"]]=part.content
```


https://github.com/vikasdo/pdf_rotater


