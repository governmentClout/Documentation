---
title: Gclout API Reference

toc_footers:
  - <a href='https://staybusy.ng'>By StayBusy Nigeria</a>
  - <a href='#'>For SpruceCities Limited</a>

includes:
  - errors

search: true
---

# Introduction

Government Clout as the name suggests is a social platform focused on politics, politicians and the people. The website is hosted on gclout.com, api documentation hosted on developers.gclout.com.

# Generalization

For proper responses, all requests made to the API Server should have these headers present.
* Content-Type: application/json
* Accept: application/json
* X-Requested-With: XMLHttpRequest


# Authentication

Gclout uses simple token authentication procedure. To athenticate, client must include their uuid and token in the request header. Authentication token will first be granted on registration and subsequently used for authorization during all requests to the API server 



# Errors
The API returns standard HTTP response codes which represents the status of an API request. Codes in the range of 4** and 5** typically means an error as occurred.

<aside class="notice">
You you normally get more information about the specific errors that occur. 
</aside>


# Users

The user object represents a single user on the platform, the APi allows basic CRU (without the D) function on a user. The user endpoint exposes other endpoints to get more information about the player.

## Create A user (Email)

The endpoint creates a new user using Email provider

### HTTP Request
The endpoint requires a POST request with all required feilds.

```curl
curl -X POST \
  http://api.gclout.com:3000/users \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: bnEPrq2luv7mh2XLFgxXkdWlZAAfzEs8Nw3D34V0X6cWVkzxQD54AFyGrDWXqfUdbGJNDLuqChdNjnlcG75J47faRYoUQVzD9khZ' \
  -H 'uuid: ad35a17c-2e38-4867-b690-133f61f639d0' \
  -d '{
  "phone":"08123460799",
  "email":"test@test.com",
  "dob":"19/08/1968",
  "password":"password",
  "tosAgreement":true,
  "provider":"email"
}'

```
### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>user email</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>dob</td>
    <td>string</td>
    <td>user date of birth</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>password</td>
    <td>string</td>
    <td>password</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>user phone number</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>tosAgreement</td>
    <td>boolean</td>
    <td>TOS agreement</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>provider</td>
    <td>string</td>
    <td>user method of signup, either email, or any of the social media</td>
    <td>yes</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/users`


```json
{
  "phone":"08123460799",
  "email":"test@test.com",
  "dob":"19/08/1968",
  "password":"password",
  "tosAgreement":true,
  "provider":"email"
}

```

> The above command returns JSON structured like this:

```json
{
    "Token": "UX4LmqktGgC7Ilib9qmpHTRnYxEjr7eMTiD6QUUhRSHI70nT482boFClYmB7FmM7ulcgqcE388grQLUg9IfD2Ol9mPPqM8kImoFF",
    "uuid": "055e8860-cbe9-11e8-98f8-4fae0909dc0e"
}
```

## Create A user (Social Media)

The endpoint creates a new user using social media provider

### HTTP Request
The endpoint requires a POST request with all required feilds.

```curl
curl -X POST \
  http://api.gclout.com:3000/users \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: bnEPrq2luv7mh2XLFgxXkdWlZAAfzEs8Nw3D34V0X6cWVkzxQD54AFyGrDWXqfUdbGJNDLuqChdNjnlcG75J47faRYoUQVzD9khZ' \
  -H 'uuid: ad35a17c-2e38-4867-b690-133f61f639d0' \
  -d '{
  "dob":"19/08/1968",
  "password":"password",
  "tosAgreement":true,
  "provider":"twitter"
}'

```
### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>user email</td>
    <td>no</td>
  </tr>
  <tr>
    <td>dob</td>
    <td>string</td>
    <td>user date of birth</td>
    <td>no</td>
  </tr>
  <tr>
    <td>password</td>
    <td>string</td>
    <td>password</td>
    <td>no</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>user phone number</td>
    <td>no</td>
  </tr>
  <tr>
    <td>tosAgreement</td>
    <td>boolean</td>
    <td>TOS agreement</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>provider</td>
    <td>string</td>
    <td>user method of signup, either email, or any of the social media</td>
    <td>yes</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/users`


```json
{
  "dob":"19/08/1968",
  "password":"password",
  "tosAgreement":true,
  "provider":"twitter"
}

```

> The above command returns JSON structured like this:

```json
{
    "Token": "UX4LmqktGgC7Ilib9qmpHTRnYxEjr7eMTiD6QUUhRSHI70nT482boFClYmB7FmM7ulcgqcE388grQLUg9IfD2Ol9mPPqM8kImoFF",
    "uuid": "055e8860-cbe9-11e8-98f8-4fae0909dc0e"
}
```

## Get A User
The endpoint gets a sepcified user 

### HTTP Request
The endpoint requires a GET request with uuid.


```curl
curl -X GET \
  http://api.gclout.com:3000/users/0b586619-3f35-4efb-bcb7-387d02dc7563 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 97867cec-1257-4224-8bc6-1dc27ceb2a23' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/users/d49cf994-bd8a-4077-8b30-b252ae0eb9ef`

> The above command returns JSON structured like this:

```json
[
    {
        "email": "xyluez@ymai.com",
        "dob": "19/28/40",
        "phone": "0816062784339",
        "nationality_residence": "Nigeria",
        "nationality_origin": "Nigeria",
        "state": "state",
        "lga": "lga",
        "firstName": "Seyi",
        "lastName": "Oni",
        "photo": "photo url"
    }
]
```

## Get All Users

The endpoint gets all users 

### HTTP Request
The endpoint requires a GET request.


```curl
curl -X GET \
  http://api.gclout.com:3000/users \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 7b42ed04-c58d-402d-83af-1a63304b34db' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/users/`

> The above command returns JSON structured like this:

```json
[
    {
        "uuid":"3dc17116-bf54-4c7e-8f73-7c798f096ac2",
        "email": "xyluz@ymai.com",
        "dob": "19/28/40",
        "phone": "08160624339",
        "nationality_residence": "Nigeria",
        "nationality_origin": "Nigeria",
        "state": "state",
        "lga": "lga",
        "firstName": "Seyi",
        "lastName": "Oni",
        "photo": "photo url"
    },
    {
        "uuid":"54e65fb4-d73e-4891-8dd4-61e4a846748",
        "email": "xyluez@ymai.com",
        "dob": "19/28/40",
        "phone": "0816062784339",
        "nationality_residence": "Nigeria",
        "nationality_origin": "Nigeria",
        "state": "state",
        "lga": "lga",
        "firstName": "Seyi",
        "lastName": "Oni",
        "photo": "photo url"
    }
]
```

# Login
The endpoint logs a user into the platform.

##Login Email Provider

### HTTP Request

The endpoint requires a POST request with all required feilds.

```curl

curl -X POST \
  http://api.gclout.com:3000/login \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{

  "email":"test@test.com",
  "password":"password",
  "provider":"email"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>user email</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>password</td>
    <td>string</td>
    <td>password</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>provider</td>
    <td>string</td>
    <td>provider</td>
    <td>yes</td>
  </tr>
</table>

> Sample Request

`URL: http://api.gclout.com:3000/login`

```json
{
  "email":"test@test.com",
  "password":"password",
  "provider":"email"
}

```

> The above command returns JSON structured like this:

```json
{
    "user": {
        "uuid": "d49cf994-bd8a-4077-8b30-b252ae0eb9ef",
        "email": "xyluez@ymail.com",
        "phone": "082160614229",
        "dob": "19/08/1968",
        "token": "LdIOrXzVGWWyg0xSwGOsXx0fKSXUj2w4guRAU51HmcEc0cq7qTlhdKP17TjwJgVMfZ3X9BWLQurhH0YBpNsOUvdvAtAEKf01hdFh"
    }
}
```

##Login (Social Media) Provider

### HTTP Request

The endpoint requires a POST request with all required feilds.

```curl

curl -X POST \
  http://api.gclout.com:3000/login \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{

  "email":"test@test.com",
  "provider":"google"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>user email</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>provder</td>
    <td>string</td>
    <td>provider can be google,twitter,linkedin or facebook</td>
    <td>yes</td>
  </tr>
</table>

> Sample Request

`URL: http://api.gclout.com:3000/login`

```json
{
  "email":"test@test.com",
  "provider":"google"
}

```

> The above command returns JSON structured like this:

```json
{
    "user": {
        "uuid": "d49cf994-bd8a-4077-8b30-b252ae0eb9ef",
        "email": "xyluez@ymail.com",
        "token": "LdIOrXzVGWWyg0xSwGOsXx0fKSXUj2w4guRAU51HmcEc0cq7qTlhdKP17TjwJgVMfZ3X9BWLQurhH0YBpNsOUvdvAtAEKf01hdFh"
    }
}
```

# Password Reset
The endpoint allows user to reset their password. The process is 1. User request password reset code 2. User retrieves code from email 3. user enters code in the provided field 4. user is allowed to reset password when code is verified.

##Request Password Reset Code

### HTTP Request

The endpoint requires a POST request with all required feilds.

```curl

curl -X POST \
  http://api.gclout.com:3000/resets \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
  "email":"xyluz@ymai.com"
}'
```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>user email</td>
    <td>yes</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/resets`

```json
{
  "email":"xyluz@ymai.com"
}

```

> The above command returns JSON structured like this:

```json
{
    "Success": "Password reset code has been sent"
}
```

##Verify Password Reset Code

### HTTP Request

The endpoint requires a POST request with all required feilds.

```curl

curl -X POST \
  http://api.gclout.com:3000/resets/code \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
  "reset_code":"Z3io0"
}'
```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>reset_code</td>
    <td>string</td>
    <td>Password reset code retrieved from user email</td>
    <td>yes</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/resets/code`

```json
{
  "reset_code":"Z3io0"
}
```

> The above command returns JSON structured like this:

```json
{
    "uuid": "fb8b9078-d1ac-4d29-adaa-677388ba5b4c"
}

```

##User Password Update

### HTTP Request

The endpoint requires a PUT request with all required feilds.

```curl

curl -X PUT \
  http://api.gclout.com:3000/resets/ \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
  "reset_code":"Z3io0",
  "uuid":"fb8b9078-d1ac-4d29-adaa-677388ba5b4c",
  "password":"National1"
}'
```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>reset_code</td>
    <td>string</td>
    <td>Password reset code retrieved from user email</td>
    <td>yes</td>
  </tr>
    <tr>
    <td>uuid</td>
    <td>string</td>
    <td>uuid of the user</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>password</td>
    <td>string</td>
    <td>New password</td>
    <td>yes</td>
  </tr>
</table>

> Sample Request

`URL: http://api.gclout.com:3000/resets`

```json
{
  "reset_code":"Z3io0",
  "uuid":"fb8b9078-d1ac-4d29-adaa-677388ba5b4c",
  "password":"National1"
}
```

> The above command returns JSON structured like this:

```json
{
    "Success": "Password reset Done"
}

```

# Profile
To manage a user profile, it exposes all endpoints to perform basic CRUD on user profile

##Create Profile

### HTTP Request

The endpoint requires a POST request with all required feilds.


```curl

curl -X POST \
  http://api.gclout.com:3000/profiles \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "uuid":"055e8860-cbe9-11e8-98f8-4fae0909dc0e",
  "nationality_origin":"Nigeria",
  "nationality_residence":"Nigeria",
  "state":"Lagos",
  "lga":"Akinyele",
  "photo":"linktophoto",
  "background":"urlofbackgroundphoto",
  "firstName":"Seyi",
  "lastName":"Onifade"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>uuid</td>
    <td>string</td>
    <td>user uuid</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>nationality_residence</td>
    <td>string</td>
    <td>user's country</td>
    <td>yes</td>
  </tr>
    <tr>
    <td>nationality_origin</td>
    <td>string</td>
    <td>user's country</td>
    <td>yes</td>
  </tr>
   <tr>
    <td>first name</td>
    <td>string</td>
    <td>user's name</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>last name</td>
    <td>string</td>
    <td>user's last name</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>user state</td>
    <td>yes</td>
  </tr>
    <tr>
    <td>lga</td>
    <td>string</td>
    <td>user local government area</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>photo</td>
    <td>string</td>
    <td>user photo url</td>
    <td>yes</td>
  </tr>
   <tr>
    <td>background</td>
    <td>string</td>
    <td>user profile background photo url</td>
    <td>no</td>
  </tr>
</table>

> Sample Request

`URL: http://api.gclout.com:3000/profiles`

```json
{
  "uuid":"055e8860-cbe9-11e8-98f8-4fae0909dc0e",
  "nationality_origin":"Nigeria",
  "nationality_residence":"Nigeria",
  "state":"Lagos",
  "lga":"Akinyele",
  "photo":"linktophoto",
  "firstName":"Seyi",
  "lastName":"Onifade",
  "background":"backgroundurl"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Profile created"
}

```

##Get Profile

### HTTP Request

The endpoint requires a GET request with uuid.

```curl
curl -X GET \
  http://api.gclout.com:3000/profiles/0b586619-3f35-4efb-bcb7-387d02dc7563 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/profiles/{uuid}`


> The request returns JSON structured like this:

```json

{
    "profile": [
        {
            "id": 3,
            "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "nationality_origin": "Nigeria",
            "nationality_residence": "Nigeria",
            "state": "state",
            "lga": "lga",
            "firstName": "Seyi",
            "lastName": "Oni",
            "photo": "photo url",
            "created_at": "2018-11-14T11:05:33.000Z",
            "updated_at": "2018-11-14T11:05:33.000Z"
        }
    ]
}

```

##Edit Profile

### HTTP Request

The endpoint requires a PUT request with uuid. 


```curl
curl -X PUT \
  http://api.gclout.com:3000/profiles \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "nationality_origin":"Nigeria edit",
  "nationality_residence":"Nigeria edit",
  "state":"Lagos edit"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>uuid</td>
    <td>string</td>
    <td>user uuid</td>
    <td>no</td>
  </tr>
  <tr>
    <td>nationality</td>
    <td>string</td>
    <td>user's country</td>
    <td>no</td>
  </tr>
   <tr>
    <td>first name</td>
    <td>string</td>
    <td>user's name</td>
    <td>no</td>
  </tr>
  <tr>
    <td>last name</td>
    <td>string</td>
    <td>user's last name</td>
    <td>no</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>user state</td>
    <td>no</td>
  </tr>
    <tr>
    <td>lga</td>
    <td>string</td>
    <td>user local government area</td>
    <td>no</td>
  </tr>
  <tr>
    <td>photo</td>
    <td>string</td>
    <td>user photo</td>
    <td>no</td>
  </tr>
   <tr>
    <td>background</td>
    <td>string</td>
    <td>user profile background url</td>
    <td>no</td>
  </tr>
</table>

> Sample Request

`URL: http://api.gclout.com:3000/profiles`


```json
{
  "nationality_origin":"Nigeria edit",
  "nationality_residence":"Nigeria edit",
  "state":"Lagos edit"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Profile Update Done"
}

```

#Posts
To manage all posts, it exposes all endpoints to perform basic CRUD on posts


##Create Post

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/posts \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "post":"I am a post",
  "post_type": "post"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>post</td>
    <td>text</td>
    <td>post content</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>location</td>
    <td>string</td>
    <td>if user sepcifies location in post</td>
    <td>no</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>post_type</td>
    <td>string</td>
    <td>Should be post</td>
    <td>no</td>
    <td>post</td>
  </tr>
   <tr>
    <td>attachment</td>
    <td>object/json/array</td>
    <td>attachments on a post, url of attachments</td>
    <td>no</td>
    <td>NULL</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/posts`

```json
{
  "post":"I am a post"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Post Created"
}

```

##Get All Post

### HTTP Request

The endpoint requires a GET request.

```curl
curl -X GET \
  http://api.gclout.com:3000/posts \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'
```


> Sample Request

`URL: http://api.gclout.com:3000/posts`


> The request returns JSON structured like this:

```json

[
    {
        "post": {
            "id": 1,
            "uuid": "cea61750-96c9-4c6a-8be4-e72a63aa1a44",
            "user": "fb8b9078-d1ac-4d29-adaa-677388ba5b4c",
            "post": "O a, a shfsdf sdfsdf sdfsd ydh",
            "created_at": "2018-11-14T10:35:41.000Z",
            "updated_at": "2018-11-14T10:35:41.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "post"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluz@ymai.com",
                "phone": "08160624339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    },
    {
        "post": {
            "id": 2,
            "uuid": "86af179f-0bf2-4d98-9eff-1ae743c7ff43",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "post": "O a, a shfsdf sdfsdf sdfsd ydh222",
            "created_at": "2018-11-14T10:48:19.000Z",
            "updated_at": "2018-11-14T10:48:19.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "post"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    },
    {
        "post": {
            "id": 3,
            "uuid": "80903c3c-5d26-41eb-bf8c-04bda9e2a31b",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "post": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "created_at": "2018-11-14T11:04:10.000Z",
            "updated_at": "2018-11-14T11:04:10.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "post"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Get All User Post

### HTTP Request

The endpoint requires a GET request.

```curl
curl -X GET \
  'http://api.gclout.com:3000/posts?user=0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'
```


> Sample Request

`URL: http://api.gclout.com:3000/posts?user=0b586619-3f35-4efb-bcb7-387d02dc7563`


> The request returns JSON structured like this:

```json

[
    {
        "post": {
            "id": 1,
            "uuid": "cea61750-96c9-4c6a-8be4-e72a63aa1a44",
            "user": "fb8b9078-d1ac-4d29-adaa-677388ba5b4c",
            "post": "O a, a shfsdf sdfsdf sdfsd ydh",
            "created_at": "2018-11-14T10:35:41.000Z",
            "updated_at": "2018-11-14T10:35:41.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "post"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluz@ymai.com",
                "phone": "08160624339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Get Single Post

### HTTP Request

The endpoint requires a GET request with post uuid.

```curl
curl -X GET \
  http://api.gclout.com:3000/posts/9e52b138-4972-48b0-be2a-ace5895c99bb \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```


> Sample Request

`URL: http://api.gclout.com:3000/posts/e0bc1ca0-be29-4ab3-80b5-881297b15936`


> The request returns JSON structured like this:

```json

[
    {
        "post": {
            "id": 3,
            "uuid": "80903c3c-5d26-41eb-bf8c-04bda9e2a31b",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "post": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "created_at": "2018-11-14T11:04:10.000Z",
            "updated_at": "2018-11-14T11:04:10.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "post"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Update Post

### HTTP Request

The endpoint requires a PUT request.


```curl
curl -X PUT \
  http://api.gclout.com:3000/articles/0a21b698-d088-4298-80eb-89c055ee2d4d \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "post":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>post</td>
    <td>text</td>
    <td>article content</td>
    <td>no</td>
    <td>--</td>
  </tr>
  <tr>
    <td>location</td>
    <td>string</td>
    <td>if user sepcifies location in article</td>
    <td>no</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>post_type</td>
    <td>string</td>
    <td>Should be post</td>
    <td>no</td>
    <td>post</td>
  </tr>
   <tr>
    <td>attachment</td>
    <td>object/json/array</td>
    <td>attachments on a post, url of attachments</td>
    <td>no</td>
    <td>NULL</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/posts/{uuid}`

```json
{
  "article":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Post Update Done"
}

```


##Delete Post

### HTTP Request

The endpoint requires a DELETE request with post uuid. The endpoint deletes all comments associated with the post.

```curl
curl -X DELETE \
  http://api.gclout.com:3000/posts/9e52b138-4972-48b0-be2a-ace5895c99bb \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/posts/e0bc1ca0-be29-4ab3-80b5-881297b15936`


> The request returns JSON structured like this for a successful delete (plus comments):

```json

{
    "Success": "Post Deleted"
}

```
```json
{
    "Error": "Post comments not deleted, something went wrong"
}

```

#Articles
To manage all articles, it exposes all endpoints to perform basic CRUD on articles


##Create Article

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/articles \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "article":"O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "article_title":"I am a title"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>article</td>
    <td>text</td>
    <td>article content</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>article_ttile</td>
    <td>text</td>
    <td>article title</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>location</td>
    <td>string</td>
    <td>if user sepcifies location in article</td>
    <td>no</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>post_type</td>
    <td>string</td>
    <td>Should be article</td>
    <td>no</td>
    <td>article</td>
  </tr>
   <tr>
    <td>attachment</td>
    <td>object/json/array</td>
    <td>attachments on a post, url of attachments</td>
    <td>no</td>
    <td>NULL</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/articles`

```json
{
  "article":"O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "article_title":"I am a title"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Article Created"
}

```

##Update Article

### HTTP Request

The endpoint requires a PUT request.


```curl
curl -X GET \
  http://api.gclout.com:3000/articles/0a21b698-d088-4298-80eb-89c055ee2d4d \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "article":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "article_title":"I am a title 222"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>article</td>
    <td>text</td>
    <td>article content</td>
    <td>no</td>
    <td>--</td>
  </tr>
  <tr>
    <td>article_ttile</td>
    <td>text</td>
    <td>article title</td>
    <td>no</td>
    <td>--</td>
  </tr>
  <tr>
    <td>location</td>
    <td>string</td>
    <td>if user sepcifies location in article</td>
    <td>no</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>post_type</td>
    <td>string</td>
    <td>Should be article</td>
    <td>no</td>
    <td>article</td>
  </tr>
   <tr>
    <td>attachment</td>
    <td>object/json/array</td>
    <td>attachments on a post, url of attachments</td>
    <td>no</td>
    <td>NULL</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/articles/{uuid}`

```json
{
  "article":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "article_title":"I am a title 222"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Artile Update Done"
}

```

##Get All Articles

### HTTP Request

The endpoint requires a GET request.

```curl
curl -X GET \
  http://api.gclout.com:3000/articles \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
```


> Sample Request

`URL: http://api.gclout.com:3000/articles`


> The request returns JSON structured like this:

```json
[
    {
        "article": {
            "id": 1,
            "uuid": "ee2bdba1-576a-43a3-b1a9-fe2700237daf",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "article": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "article_title": "I am a title",
            "created_at": "2018-11-14T12:43:00.000Z",
            "updated_at": "2018-11-14T12:43:00.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "article"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Get All User Articles

### HTTP Request

The endpoint requires a GET request.

```curl
curl -X GET \
  'http://api.gclout.com:3000/articles/?user=19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
```


> Sample Request

`URL: http://api.gclout.com:3000/articles?user=19993c36-8c26-4271-a85c-9fea498c8a8c`


> The request returns JSON structured like this:

```json

[
    {
        "article": {
            "id": 1,
            "uuid": "ee2bdba1-576a-43a3-b1a9-fe2700237daf",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "article": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "article_title": "I am a title",
            "created_at": "2018-11-14T12:43:00.000Z",
            "updated_at": "2018-11-14T12:43:00.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "article"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    },
    {
        "article": {
            "id": 2,
            "uuid": "0a21b698-d088-4298-80eb-89c055ee2d4d",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "article": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "article_title": "I am a title",
            "created_at": "2018-11-14T12:47:01.000Z",
            "updated_at": "2018-11-14T12:47:01.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "article"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Get Single Article

### HTTP Request

The endpoint requires a GET request with article uuid.

```curl
curl -X GET \
  http://api.gclout.com:3000/articles/ee2bdba1-576a-43a3-b1a9-fe2700237daf \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
```


> Sample Request

`URL: http://api.gclout.com:3000/articles/e0bc1ca0-be29-4ab3-80b5-881297b15936`


> The request returns JSON structured like this:

```json

[
    {
        "article": {
            "id": 1,
            "uuid": "ee2bdba1-576a-43a3-b1a9-fe2700237daf",
            "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "article": "O a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "article_title": "I am a title",
            "created_at": "2018-11-14T12:43:00.000Z",
            "updated_at": "2018-11-14T12:43:00.000Z",
            "status": null,
            "location": "unspecified",
            "attachment": "null",
            "post_type": "article"
        },
        "user": [
            {
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "nationality_residence": "Nigeria",
                "nationality_origin": "Nigeria",
                "state": "state",
                "email": "xyluez@ymai.com",
                "phone": "0816062784339",
                "dob": "19/28/40"
            }
        ],
        "comments": [],
        "reactions": [],
        "shares": [],
        "views": []
    }
]

```

##Delete Article

### HTTP Request

The endpoint requires a DELETE request with post uuid. The endpoint deletes all comments associated with the post.

```curl
curl -X DELETE \
  http://api.gclout.com:3000/posts/9e52b138-4972-48b0-be2a-ace5895c99bb \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/posts/e0bc1ca0-be29-4ab3-80b5-881297b15936`


> The request returns JSON structured like this for a successful delete (plus comments):

```json

{
    "Success": "Post Deleted"
}

```
```json
{
    "Error": "Post comments not deleted, something went wrong"
}

```


#Comments
To manage all comments, it exposes all endpoints to perform basic CRUD on comments


##Create Comment

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/comments \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "comment":"I am a post comment",
  "ref":"a20ebc3f-a2b6-40ec-b009-968336e83552"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>comment</td>
    <td>text</td>
    <td>comment content</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>ref</td>
    <td>string</td>
    <td>uuid of the post/article</td>
    <td>no</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/posts`

```json
{
  "comment":"I am a comment",
  "ref":"3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Comment Posted"
}

```

##Get All Post Comments

### HTTP Request

The endpoint requires a GET request with comment uuid of the post.

```curl
curl -X GET \
  http://api.gclout.com:3000/comments/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```


> Sample Request

`URL: http://api.gclout.com:3000/comments/dcb7e418-3961-441a-a4d2-5bc6127370b1`


> The request returns JSON structured like this:

```json

{
    "comment": {
            "id": 2,
            "uuid": "2a7ce94c-d366-4879-baab-4450189a13da",
            "comment": "I am a comment",
            "created_at": "2018-11-26T19:24:23.000Z",
            "updated_at": "2018-11-26T19:24:23.000Z",
            "status": 1,
            "ref": "cea61750-96c9-4c6a-8be4-e72a63aa1a44",
            "user": "fb8b9078-d1ac-4d29-adaa-677388ba5b4c"
        },
        "user": [
            {
                "id": 2,
                "uuid": "fb8b9078-d1ac-4d29-adaa-677388ba5b4c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T10:58:46.000Z",
                "updated_at": "2018-11-14T10:58:46.000Z"
            }
        ]
}

```

##Delete Comment

### HTTP Request

The endpoint requires a DELETE request with comment uuid.

```curl
curl -X DELETE \
  http://api.gclout.com:3000/comments/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/comments/dcb7e418-3961-441a-a4d2-5bc6127370b1`


> The request returns JSON structured like this:

```json

{
    "Success": "Comment Deleted"
}

```


#Reactions

To manage all posts/articles reactions such as 'like' and 'unlike', it exposes all endpoints to perform basic CD (Create and Delete) on reactions


##Like Post/Article

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/reactions/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "post":"a20ebc3f-a2b6-40ec-b009-968336e83552"
}'

```

> Sample Request

`URL: http://api.gclout.com:3000/reactions/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


> The above command returns JSON structured like this:

```json

{
    "Success": "Post Liked"
}

```

##Get Post/Article Reactions

### HTTP Request

The endpoint requires a GET request with post/article uuid.


```curl
curl -X GET \
  http://api.gclout.com:3000/reactions/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 40b3c281-e8c6-4732-b306-8c399b2e5fb5' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/reactions/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


> The above command returns JSON structured like this:

```json

[
    {
        "reactions": 2
    }
]

```

##Unlike Post/Article

### HTTP Request

The endpoint requires a DELETE request.


```curl
curl -X DELETE \
  http://api.gclout.com:3000/reactions/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/reactions/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


> The above command returns JSON structured like this:

```json

{
    "Success": "Reaction Deleted"
}

```


#Views

To manage all posts/articles views. You can register a view with this endpoint, when a user views a post/article, you should register that view with this endpoint


##Register View

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/views/ \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563' \
  -d '{
  "post":"a20ebc3f-a2b6-40ec-b009-968336e83552"
}'

```
### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>post</td>
    <td>text</td>
    <td>uuid of the post</td>
    <td>yes</td>
  </tr>
  

</table>


> Sample Request

`URL: http://api.gclout.com:3000/views/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


```json
{
  "post":"a20ebc3f-a2b6-40ec-b009-968336e83552"
}
```

> The above command returns JSON structured like this:

```json

{
    "success": "view registered"
}

```

##Get Post/Article Views

### HTTP Request

The endpoint requires a GET request with post/article uuid.


```curl
curl -X GET \
  http://api.gclout.com:3000/views/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/views/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


> The above command returns JSON structured like this:

```json

[
    {
        "views": 1
    }
]
```

#Shares

To manage all posts/articles shares. You can register a share with this endpoint, when a user shares a post/article, you should register that share with this endpoint


##Register Share

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/shares/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```
### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th>
  </tr>
  <tr>
    <td>post</td>
    <td>text</td>
    <td>uuid of the post</td>
    <td>yes</td>
  </tr>
  

</table>


> Sample Request

`URL: http://api.gclout.com:3000/shares/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`

```json
{
  "post":"a20ebc3f-a2b6-40ec-b009-968336e83552"
}
```

> The above command returns JSON structured like this:

```json

{
    "Success": "Post Shared"
}

```

##Get Post/Article Shares

### HTTP Request

The endpoint requires a GET request with post/article uuid.


```curl
curl -X GET \
  http://api.gclout.com:3000/shares/a20ebc3f-a2b6-40ec-b009-968336e83552 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'token: jFJtTHHAQ85FMOQnSYOp1YYenUtMuusb6imq1XYHj7couOb0yVoZHD1DGj88r2JU4gIlf1QBVHkUaqXssmBJ6nm8myGxiUgkwHVp' \
  -H 'uuid: 0b586619-3f35-4efb-bcb7-387d02dc7563'

```

> Sample Request

`URL: http://api.gclout.com:3000/shares/3f6aeb13-a73c-4f91-9ea2-0e9f2dcc2d61`


> The above command returns JSON structured like this:

```json

[
    {
        "shares": 2
    }
]
```


#Polls
To manage all polls, it exposes all endpoints to perform basic CRUD on polls


##Create Poll

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/polls \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "opinion":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "sector":"Education"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>opinion</td>
    <td>text</td>
    <td>poll content content</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>sector</td>
    <td>text</td>
    <td>poll sector</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>expire_at</td>
    <td>datetime</td>
    <td>When this poll should expire accepted format: yyyy-mm-dd hh:mm:ss</td>
    <td>no</td>
    <td>3014-01-01 00:00:00</td>
  </tr>
  <tr>
    <td>response_limit</td>
    <td>integer</td>
    <td>How many people are allowed to respond to the poll</td>
    <td>no</td>
    <td>1000</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/polls`

```json
{
  "opinion":"sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
  "sector":"Education"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Poll Created"
}

```

##Respond To Poll

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/polls/response \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "poll":"c9391c31-cbcd-492c-a81b-6f85e1a8df36",
  "status":"1"
}'
```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>poll</td>
    <td>text</td>
    <td>poll uuid</td>
    <td>yes</td>
    <td>--<td>
  </tr>
  <tr>
    <td>status</td>
    <td>text</td>
    <td>status of the repsonse: 1 - true/agree/yes 2 - no/disagree/false 3 - undecided</td>
    <td>yes</td>
    <td>--<td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/polls/response`

```json
{
  "poll":"c9391c31-cbcd-492c-a81b-6f85e1a8df36"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "response submitted"
}

```

##Get All Polls

### HTTP Request

The endpoint requires a GET request.


```curl
curl -X GET \
  http://localhost:3000/polls \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: ExDBlixDlGVvDlewT9fpgB8HpyjT0pz1gFr9Gi2wkuPe0v5NqxnmpRHzTJASsjoz1YqcTOAWhXxXvqs5CSQhDjeNFv1LSVL5lJMY' \
  -H 'uuid: 2c2fe757-352b-4520-890c-f37d12008cae'
```

> Sample Request

`URL: http://api.gclout.com:3000/polls`


> The above command returns JSON structured like this:

```json

[
    {
        "polls": {
            "id": 1,
            "uuid": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
            "sector": "Education",
            "opinion": "sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "created_by": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "created_at": "2018-11-14T13:16:06.000Z",
            "updated_at": "2018-11-14T13:16:06.000Z",
            "expire_at": "2018-11-14T12:16:06.000Z",
            "status": 0,
            "response_limit": 1000
        },
        "responses": [
            {
                "id": 1,
                "poll": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
                "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "status": 1,
                "created_at": "2018-11-14T13:31:04.000Z"
            },
            {
                "id": 2,
                "poll": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
                "user": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "status": 1,
                "created_at": "2018-11-23T14:22:53.000Z"
            }
        ]
    },
    {
        "polls": {
            "id": 2,
            "uuid": "e54bf7b3-0c3a-42fa-8238-8af550c6d5cf",
            "sector": "Lagos",
            "opinion": "I am apollll",
            "created_by": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
            "created_at": "2018-11-23T14:48:10.000Z",
            "updated_at": "2018-11-23T14:48:10.000Z",
            "expire_at": "2018-11-23T11:25:20.000Z",
            "status": 0,
            "response_limit": 1000
        },
        "responses": []
    }
]

```

##Get All User Polls

### HTTP Request

The endpoint requires a GET request.


```curl
curl -X GET \
  'http://localhost:3000/polls?user=19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: bb564060-6d1f-41f7-8bb7-81ce66a568e1' \
  -H 'cache-control: no-cache' \
  -H 'token: ExDBlixDlGVvDlewT9fpgB8HpyjT0pz1gFr9Gi2wkuPe0v5NqxnmpRHzTJASsjoz1YqcTOAWhXxXvqs5CSQhDjeNFv1LSVL5lJMY' \
  -H 'uuid: 2c2fe757-352b-4520-890c-f37d12008cae'
```

> Sample Request

`URL: http://api.gclout.com:3000/polls?user=19993c36-8c26-4271-a85c-9fea498c8a8c`



> The above command returns JSON structured like this:

```json

[
    {
        "polls": {
            "id": 1,
            "uuid": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
            "sector": "Education",
            "opinion": "sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "created_by": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "created_at": "2018-11-14T13:16:06.000Z",
            "updated_at": "2018-11-14T13:16:06.000Z",
            "expire_at": "2018-11-14T12:16:06.000Z",
            "status": 0,
            "response_limit": 1000
        },
        "responses": [
            {
                "id": 1,
                "poll": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
                "user": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "status": 1,
                "created_at": "2018-11-14T13:31:04.000Z"
            },
            {
                "id": 2,
                "poll": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
                "user": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "status": 1,
                "created_at": "2018-11-23T14:22:53.000Z"
            }
        ]
    }
]

```

##Get Single Polls

### HTTP Request

The endpoint requires a GET request.


```curl
curl -X GET \
  http://localhost:3000/polls/c9391c31-cbcd-492c-a81b-6f85e1a8df36 \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: ExDBlixDlGVvDlewT9fpgB8HpyjT0pz1gFr9Gi2wkuPe0v5NqxnmpRHzTJASsjoz1YqcTOAWhXxXvqs5CSQhDjeNFv1LSVL5lJMY' \
  -H 'uuid: 2c2fe757-352b-4520-890c-f37d12008cae'
```

> Sample Request

`URL: http://api.gclout.com:3000/polls/c9391c31-cbcd-492c-a81b-6f85e1a8df36`



> The above command returns JSON structured like this:

```json

{
    "poll": [
        {
            "id": 1,
            "uuid": "c9391c31-cbcd-492c-a81b-6f85e1a8df36",
            "sector": "Education",
            "opinion": "sdfsd sdfsd fO a, a shfsdf sdfsdf sdfsd ydh222  ttt",
            "created_by": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "created_at": "2018-11-14T13:16:06.000Z",
            "updated_at": "2018-11-14T13:16:06.000Z",
            "expire_at": "2018-11-14T12:16:06.000Z",
            "status": 0,
            "response_limit": 1000
        }
    ],
    "responses": [
        [
            {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        ],
        [
            {
                "id": 7,
                "uuid": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "nationality_origin": "nig",
                "nationality_residence": "nig",
                "state": "stqa",
                "lga": "lfs",
                "firstName": "se",
                "lastName": "ses",
                "photo": "http://res.cloudinary.com/staybusy/image/upload/v1542666528/y7lvxdaw1mgijerqughh.png",
                "created_at": "2018-11-19T22:19:45.000Z",
                "updated_at": "2018-11-19T21:28:46.000Z"
            }
        ]
    ]
}
```

#Friends
To manage all friends, it exposes all endpoints to perform basic CRUD on friends


##Send Friend Request

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/friends/request \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>friend</td>
    <td>text</td>
    <td>user receiving the request</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/friends/request`

```json
{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Request Sent"
}

```

##Accept Friend Request

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/friends/accept \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: ExDBlixDlGVvDlewT9fpgB8HpyjT0pz1gFr9Gi2wkuPe0v5NqxnmpRHzTJASsjoz1YqcTOAWhXxXvqs5CSQhDjeNFv1LSVL5lJMY' \
  -H 'uuid: 2c2fe757-352b-4520-890c-f37d12008cae' \
  -d '{
  "friend":"19993c36-8c26-4271-a85c-9fea498c8a8c"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>friend</td>
    <td>text</td>
    <td>user who sent the request</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/friends/accept`

```json
{
  "friend":"19993c36-8c26-4271-a85c-9fea498c8a8c"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Request Accepted"
}

```

##Ignore Friend Request

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/friends/ignore \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>friend</td>
    <td>text</td>
    <td>user who sent the request</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/friends/ignore`

```json
{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Request Ignored"
}

```

##Block Friend Request

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/friends/block \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c' \
  -d '{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>friend</td>
    <td>text</td>
    <td>user who sent the request</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/friends/block`

```json
{
  "friend":"2c2fe757-352b-4520-890c-f37d12008cae"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Request Blocked"
}

```

##Get Single User Friends

### HTTP Request

The endpoint requires a GET request. Returns the user and profile object.


```curl
curl -X GET \
  http://api.gclout.com:3000/friends \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c'

```

> Sample Request

`URL: http://api.gclout.com:3000/friends`



> The above command returns JSON structured like this:

```json

{
    "friends": [
        {
            "user": [
                {
                    "id": 2,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "email": "xyluez@ymai.com",
                    "password": "d7580f69dd2acc3d6c828474b74a330bcf590684e5b9a61b070e79dd0373d26a",
                    "phone": "0816062784339",
                    "dob": "19/28/40",
                    "tosAgreement": 1,
                    "provider": "email",
                    "created_at": "2018-11-14T10:47:45.000Z",
                    "updated_at": "2018-11-14T10:47:45.000Z",
                    "status": 1
                }
            ],
            "profile": [
                {
                    "id": 3,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "nationality_origin": "Nigeria",
                    "nationality_residence": "Nigeria",
                    "state": "state",
                    "lga": "lga",
                    "firstName": "Seyi",
                    "lastName": "Oni",
                    "photo": "photo url",
                    "created_at": "2018-11-14T11:05:33.000Z",
                    "updated_at": "2018-11-14T11:05:33.000Z"
                }
            ]
        }
    ]
}

```


##Get User Pending Friends Requests

### HTTP Request

The endpoint requires a GET request. Returns the user and profile object.


```curl
curl -X GET \
  http://api.gclout.com:3000/friends/pending \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c'

```

> Sample Request

`URL: http://api.gclout.com:3000/friends/pending`



> The above command returns JSON structured like this:

```json

{
    "friends": [
        {
            "user": [
                {
                    "id": 2,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "email": "xyluez@ymai.com",
                    "password": "d7580f69dd2acc3d6c828474b74a330bcf590684e5b9a61b070e79dd0373d26a",
                    "phone": "0816062784339",
                    "dob": "19/28/40",
                    "tosAgreement": 1,
                    "provider": "email",
                    "created_at": "2018-11-14T10:47:45.000Z",
                    "updated_at": "2018-11-14T10:47:45.000Z",
                    "status": 0
                }
            ],
            "profile": [
                {
                    "id": 3,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "nationality_origin": "Nigeria",
                    "nationality_residence": "Nigeria",
                    "state": "state",
                    "lga": "lga",
                    "firstName": "Seyi",
                    "lastName": "Oni",
                    "photo": "photo url",
                    "created_at": "2018-11-14T11:05:33.000Z",
                    "updated_at": "2018-11-14T11:05:33.000Z"
                }
            ]
        }
    ]
}

```


##Get User Blocked Friends (Requests)

### HTTP Request

The endpoint requires a GET request. Returns the user and profile object.


```curl
curl -X GET \
  http://api.gclout.com:3000/friends/blocked \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c'

```

> Sample Request

`URL: http://api.gclout.com:3000/friends/blocked`



> The above command returns JSON structured like this:

```json

{
    "friends": [
        {
            "user": [
                {
                    "id": 2,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "email": "xyluez@ymai.com",
                    "password": "d7580f69dd2acc3d6c828474b74a330bcf590684e5b9a61b070e79dd0373d26a",
                    "phone": "0816062784339",
                    "dob": "19/28/40",
                    "tosAgreement": 1,
                    "provider": "email",
                    "created_at": "2018-11-14T10:47:45.000Z",
                    "updated_at": "2018-11-14T10:47:45.000Z",
                    "status": 3
                }
            ],
            "profile": [
                {
                    "id": 3,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "nationality_origin": "Nigeria",
                    "nationality_residence": "Nigeria",
                    "state": "state",
                    "lga": "lga",
                    "firstName": "Seyi",
                    "lastName": "Oni",
                    "photo": "photo url",
                    "created_at": "2018-11-14T11:05:33.000Z",
                    "updated_at": "2018-11-14T11:05:33.000Z"
                }
            ]
        }
    ]
}

```
##Get User Blocked Friends (Requests)

### HTTP Request

The endpoint requires a GET request. Returns the user and profile object.


```curl
curl -X GET \
  http://api.gclout.com:3000/friends/blocked \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: OaOeudrqxvl5vkoPosiexs11Fdy1cKJEpAWTYtaggHx5PLMc8ry2KZZg9gyzagjhZKrCjGNcV4VTCk62kadyyFKxZEaV0yFxoAmM' \
  -H 'uuid: 19993c36-8c26-4271-a85c-9fea498c8a8c'

```

> Sample Request

`URL: http://api.gclout.com:3000/friends/blocked`



> The above command returns JSON structured like this:

```json

{
    "friends": [
        {
            "user": [
                {
                    "id": 2,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "email": "xyluez@ymai.com",
                    "password": "d7580f69dd2acc3d6c828474b74a330bcf590684e5b9a61b070e79dd0373d26a",
                    "phone": "0816062784339",
                    "dob": "19/28/40",
                    "tosAgreement": 1,
                    "provider": "email",
                    "created_at": "2018-11-14T10:47:45.000Z",
                    "updated_at": "2018-11-14T10:47:45.000Z",
                    "status": 3
                }
            ],
            "profile": [
                {
                    "id": 3,
                    "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                    "nationality_origin": "Nigeria",
                    "nationality_residence": "Nigeria",
                    "state": "state",
                    "lga": "lga",
                    "firstName": "Seyi",
                    "lastName": "Oni",
                    "photo": "photo url",
                    "created_at": "2018-11-14T11:05:33.000Z",
                    "updated_at": "2018-11-14T11:05:33.000Z"
                }
            ]
        }
    ]
}

```

#Messages
To manage all messages, it exposes all endpoints to perform basic CRUD on messages


##Send Message

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/messages/ \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \
  -d '{
  "receiver":"19993c36-8c26-4271-a85c-9fea498c8a8c",
  "message":"I am a message 2333 sdsdf"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>receiver</td>
    <td>text</td>
    <td>uuid of the recevier</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>message</td>
    <td>text</td>
    <td>Content of the message</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/messages`

```json
{
  "receiver":"19993c36-8c26-4271-a85c-9fea498c8a8c",
  "message":"I am a message 2333 sdsdf"
}
```

> The above command returns JSON structured like this:

```json

{
    "Success": "Message sent"
}

```

##Reply Message

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/messages/ \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \
  -d '{
  "receiver":"19993c36-8c26-4271-a85c-9fea498c8a8c",
  "message":"I am a message 2333 sdsdf",
  "reply_to":"f00d7d2b-876d-4f75-8406-93b5d4c6ac7f"
}'

```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>receiver</td>
    <td>text</td>
    <td>uuid of the recevier</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>message</td>
    <td>text</td>
    <td>Content of the message</td>
    <td>yes</td>
    <td>--</td>
  </tr>
   <tr>
    <td>reply_to</td>
    <td>text</td>
    <td>uuid of the message being replied</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/messages`

```json

{
  "receiver":"19993c36-8c26-4271-a85c-9fea498c8a8c",
  "message":"I am a message 2333 sdsdf",
  "reply_to":"f00d7d2b-876d-4f75-8406-93b5d4c6ac7f"
}

```

> The above command returns JSON structured like this:

```json

{
    "Success": "Message sent"
}

```

##Get User Messages

### HTTP Request

The endpoint requires a GET request.


```curl
curl -X GET \
  http://api.gclout.com:3000/messages/ \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \

```

> Sample Request

`URL: http://api.gclout.com:3000/messages`



> The above command returns JSON structured like this:

```json

{
    "received": [
        {
            "message": {
                "id": 1,
                "uuid": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
                "sender": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "receiver": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "message": "I am a message",
                "reply_to": "null",
                "created_at": "2018-11-23T09:40:20.000Z",
                "updated_at": "2018-11-23T09:40:20.000Z",
                "status": 0
            },
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "message": {
                "id": 2,
                "uuid": "f2e0c0d4-a70e-42e7-80bb-9526ba07b449",
                "sender": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "receiver": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "message": "I am a message",
                "reply_to": "null",
                "created_at": "2018-11-23T09:41:18.000Z",
                "updated_at": "2018-11-23T09:41:18.000Z",
                "status": 0
            },
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "message": {
                "id": 3,
                "uuid": "580b4d7b-f82b-4f77-a3b2-0f64013e824a",
                "sender": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "receiver": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "message": "I am a message 2",
                "reply_to": "null",
                "created_at": "2018-11-23T09:51:45.000Z",
                "updated_at": "2018-11-23T09:51:45.000Z",
                "status": 0
            },
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "message": {
                "id": 4,
                "uuid": "badfad86-e290-4171-9af3-97e4056b06f6",
                "sender": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "receiver": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "message": "I am a message 2",
                "reply_to": "null",
                "created_at": "2018-11-23T09:55:11.000Z",
                "updated_at": "2018-11-23T09:55:11.000Z",
                "status": 0
            },
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        },
        {
            "user": {
                "id": 3,
                "uuid": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "nationality_origin": "Nigeria",
                "nationality_residence": "Nigeria",
                "state": "state",
                "lga": "lga",
                "firstName": "Seyi",
                "lastName": "Oni",
                "photo": "photo url",
                "created_at": "2018-11-14T11:05:33.000Z",
                "updated_at": "2018-11-14T11:05:33.000Z"
            }
        }
    ],
    "sent": [
        {
            "id": 9,
            "uuid": "d5ab2026-5cf4-4108-b447-4043353060bb",
            "sender": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
            "receiver": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "message": "I am a message 2",
            "reply_to": "null",
            "created_at": "2018-11-23T10:50:02.000Z",
            "updated_at": "2018-11-23T10:50:02.000Z",
            "status": 0
        }
    ]
}

```
##Get Single Message

### HTTP Request

The endpoint requires a GET request.


```curl
curl -X GET \
  http://api.gclout.com:3000/messages/f00d7d2b-876d-4f75-8406-93b5d4c6ac7f \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \

```

> Sample Request

`URL: http://api.gclout.com:3000/messages/{uuid}`



> The above command returns JSON structured like this:

```json

[
    {
        "message": {
            "id": 1,
            "uuid": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
            "sender": "19993c36-8c26-4271-a85c-9fea498c8a8c",
            "receiver": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
            "message": "I am a message",
            "reply_to": "null",
            "created_at": "2018-11-23T09:40:20.000Z",
            "updated_at": "2018-11-23T09:40:20.000Z",
            "status": 0
        },
        "replies": [
            {
                "id": 10,
                "uuid": "c79f0bb5-a95a-4c40-9ddb-8f35a01122ae",
                "sender": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "receiver": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "message": "I am a message 2",
                "reply_to": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
                "created_at": "2018-11-23T11:06:03.000Z",
                "updated_at": "2018-11-23T11:06:03.000Z",
                "status": 0
            },
            {
                "id": 11,
                "uuid": "786b6121-669b-4f08-b546-fcdcbd917f38",
                "sender": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "receiver": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "message": "I am a message 2333",
                "reply_to": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
                "created_at": "2018-11-23T11:07:06.000Z",
                "updated_at": "2018-11-23T11:07:06.000Z",
                "status": 0
            },
            {
                "id": 12,
                "uuid": "743ac99f-28e4-487e-b452-845a6821cc6e",
                "sender": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "receiver": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "message": "I am a message 2333 sdsdf",
                "reply_to": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
                "created_at": "2018-11-23T11:08:20.000Z",
                "updated_at": "2018-11-23T11:08:20.000Z",
                "status": 0
            },
            {
                "id": 13,
                "uuid": "d43b018c-5db1-47e1-bdbb-1d02ecef06c8",
                "sender": "e35037f7-2c04-48e2-bf45-c5000e2ca6f0",
                "receiver": "19993c36-8c26-4271-a85c-9fea498c8a8c",
                "message": "I am a message 2333 sdsdf",
                "reply_to": "f00d7d2b-876d-4f75-8406-93b5d4c6ac7f",
                "created_at": "2018-11-23T11:25:20.000Z",
                "updated_at": "2018-11-23T11:25:20.000Z",
                "status": 0
            }
        ]
    }
]

```

##Delete Message

### HTTP Request

The endpoint requires a DELETE request.


```curl
curl -X DELETE \
  http://api.gclout.com:3000/messages/d43b018c-5db1-47e1-bdbb-1d02ecef06c8 \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \

```

> Sample Request

`URL: http://api.gclout.com:3000/messages/{uuid}`



> The above command returns JSON structured like this:

```json

{
    "Success": "Message deleted"
}

```

#Executives
To manage all executives, it exposes all endpoints to perform basic CRUD on executives


##Send Upgrade Request

### HTTP Request

The endpoint requires a POST request.


```curl
curl -X POST \
  http://api.gclout.com:3000/executives \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -H 'token: 6HPmBSAyfzEhGnOR4rvTUtlzQ9s2CrmGTGfKbzn1oY3xht9ky13wkoTXIerBvtea3B27gADggyZSTUD5V56o9qf6iqRLDtRLc8Rw' \
  -H 'uuid: e35037f7-2c04-48e2-bf45-c5000e2ca6f0' \
  -d '{
  "party":"PDP",
  "about_you":"Telling you more about me",
  "about_party":"Telling you about party",
  "office":"president"
}'
```

### Query Parameters
<table>
  
  <tr>
    <th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><th>Default</th>
  </tr>
  <tr>
    <td>party</td>
    <td>string</td>
    <td>party</td>
    <td>yes</td>
    <td>--</td>
  </tr>
  <tr>
    <td>about_you</td>
    <td>text</td>
    <td>More about the user</td>
    <td>no</td>
    <td>--</td>
  </tr>
  <tr>
    <td>about_party</td>
    <td>text</td>
    <td>More about the user office / party</td>
    <td>no</td>
    <td>--</td>
  </tr>
   <tr>
    <td>office</td>
    <td>string</td>
    <td>office held by user</td>
    <td>yes</td>
    <td>--</td>
  </tr>

</table>

> Sample Request

`URL: http://api.gclout.com:3000/executives`

```json
{
  "party":"PDP",
  "about_you":"Telling you more about me",
  "about_party":"Telling you about party",
  "office":"president"
}
```

> The above command returns JSON structured like this:

```json

{
    "Success": "Upgrade Request Sent"
}