Users
===

* [Add](#add) - adds a new user to the account.
* [Add email](#add-email) - adds a new email address for the authenticated user.
* [Add phone](#add-phone) - adds a new phone number for the authenticated user.
* [Delete](#delete) - deletes the specified user from the account.
* [Delete email](#delete-email) - deletes the specified email address from the authenticated user.
* [Delete phone](#delete-phone) - deletes the specified phone number from the authenticated user.
* [Get by id](#get-by-id) - returns the specified user.
* [List](#list) - lists all users


Add
--
`POST /users/add`

Adds a new user to the account.

**Parameters**

All parameter values should be URL encoded.

* `username` *string*
* `password` *string*
* `firstName` *string*
* `lastName` *string*
* `email` *string* (optional) 
* `apiEnabled` *integer* 1 = yes, 0 = no (optional, default = 0)
* `admin` *integer* 1 = yes, 0 = no (optional, default = 0)
* `timezone` *string* (optional, default = Europe/London)
* `groups` *string* (optional) Comma separated list of groups this user should belong to. If a specified group does not exist, it will be created.
* `groupPermissions` *integer* unset = access all groups, 2 = access only to specified groups, 3 = access to all but specified groups (optional, default = unset)

**Request**

```bash
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/add?account=llama.serverdensity.com" \
-d username=david \
-d password=hat \
-d firstName=David \
-d lastName=Mytton \
-d timezone=Europe%2FLondon \
-d groupPermissions=2 \
-d groups==Rackspace%2CTest+1
```

**Response**

```json
{
    "status": 1,
    "data": {
        "userId": {
            "$id": "503745f313bcb7fb00000000"
        },
        "userIdOld": 2
    }
}
```

Add email
--
`POST /users/addEmail`

Adds a new email address for the authenticated user.

**Parameters**

All parameter values should be URL encoded.

* `email` *string*

**Request**

```
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/addEmail?account=llama.serverdensity.com" \
-d email=hello%40serverdensity.com
```

**Response**

```json
{
    "status": 1
}
```

Add phone
--
`POST /users/addPhone`

Adds a new phone number for the authenticated user.

**Parameters**

* `phone` *int*
* `countryCode` *string*

**Request**

```
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/addPhone?account=llama.serverdensity.com" \
-d phone=12345668 \
-d countryCode=44
```

**Response**

```json
{
    "status": 1
}
```

Delete
--
`POST /users/delete`

Deletes the specified user from the account.

**Parameters**

* `userId` *string*

**Request**

```
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/delete?account=llama.serverdensity.com" \
-d userId=503745f313bcb7fb00000000
```

**Response**

```json
{
    "status": 1,
    "data": {
        "userDeleted": 1
    }
}
```


Delete email
--
`POST /users/deleteEmail`

Deletes the specified email address from the authenticated user.

**Parameters**

* `email` *- string*

**Request**

```
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/delete?account=llama.serverdensity.com" \
-d email=hello%40serverdensity.com
```

**Response**

```json
{
    "status": 1
}
```

Delete phone
--
`POST /users/deletePhone`

**Parameters**

* `phone` *int*
* `countryCode` *string*

**Request**

```
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/users/deletePhone?account=llama.serverdensity.com" \
-d phone=12345668 \
-d countryCode=44
```

**Response**

```json
{
    "status": 1
}
```

Get by ID
--
`GET /users/getById`

Returns the specified user.

**Parameters**

* `userId` *string*

**Request**

`GET http://api.serverdensity.com/VER/users/getById?account=llama.serverdensity.com&userId=4ca70d15150ba0ce3c251001`

**Response**

```json
{
    "status": 1,
    "data": {
        "user": {
            "fNm": "Admin",
            "lNm": "Admin",
            "uId": "50321f9113bcb7dd0f000004",
            "adm": true,
            "tz": "Europe/London",
            "iPDT": "",
            "emails": [
                {
                    "email": "hello@serverdensity.com"
                }
            ],
            "phones": [
                {
                    "countryCode": 44,
                    "phone": "12345668"
                }
            ]
        }
    }
}
```

List
--
`POST /users/list`

Lists all users.

**Request**

`GET http://api.serverdensity.com/1.4/users/list?account=llama.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "users": [
            {
                "userId": "50321f9113bcb7dd0f000004",
                "userIdOld": 1,
                "username": "admin",
                "firstName": "Admin",
                "lastName": "Admin",
                "admin": true,
                "groups": null
            }
        ]
    }
}
```