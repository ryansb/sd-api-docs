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

`POST http://api.serverdensity.com/VERSION/users/add?account=llama.serverdensity.com&apiKey=KEYusername=david&firstName=David&lastName=Mytton&timezone=Europe%2FLondon&password=password&groupPermissions=2&groups=Rackspace%2CTest+1`


Add email
--
`POST /users/addEmail`

Adds a new email address for the authenticated user.

**Parameters**

All parameter values should be URL encoded.

* `email` *string*

**Request**

`POST http://api.serverdensity.com/VERSION/users/addEmail?account=llama.serverdensity.com&apiKey=KEYemail=hello@boxedice.com`


Add phone
--
`POST /users/addPhone`

Adds a new phone number for the authenticated user.

**Parameters**

* `phone` *int*
* `countryCode` *string*

**Request**

`POST http://api.serverdensity.com/VERSION/users/addPhone?account=llama.serverdensity.com&apiKey=KEYphone=123456789&countryCode=44`


Delete
--
`POST /users/delete`

Deletes the specified user from the account.

**Parameters**

* `userId` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/users/delete?account=llama.serverdensity.com&apiKey=KEY&userId=4ca70d15150ba0ce3c251001`


Delete email
--
`POST /users/deleteEmail`

Deletes the specified email address from the authenticated user.

**Parameters**

* `email` *- string*

**Request**

`POST http://api.serverdensity.com/VERSION/users/deleteEmail?account=llama.serverdensity.com&apiKey=KEYemail=hello@boxedice.com`

Delete phone
--
`POST /users/deletePhone`

**Parameters**

* `phone` *int*
* `countryCode` *string*

**Request**

`POST http://api.serverdensity.com/VERSION/users/deletePhone?account=llama.serverdensity.com&apiKey=KEYphone=123456789&countryCode=44`


Get by id
--
`GET /users/getById`

Returns the specified user.

**Parameters**

* `userId` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/users/getById?account=llama.serverdensity.com&apiKey=KEY&userId=4ca70d15150ba0ce3c251001`


List
--
`POST /users/list`

Lists all users.


**Request**

`GET http://api.serverdensity.com/VERSION/users/list?account=llama.serverdensity.com&apiKey=KEY `