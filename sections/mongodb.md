MongoDB
===

* [Get master](#get-master) - returns the current master for the specified replica set name.
* [Get replica set](#get-replica-set) - lists all replica sets and their members across the whole account.


Get master
--
`GET /mongo/getMaster`

Returns the current master for the specified replica set name.

**Parameters**

* `replSetName` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/mongo/getMaster?account=llama.serverdensity.com&apiKey=KEY&replSetName=rs1`


Get replica set
--
`GET /mongo/getReplicaSet`

Lists all replica sets and their members across the whole account.


**Request**

`GET http://api.serverdensity.com/VERSION/mongo/getReplicaSet?account=llama.serverdensity.com&apiKey=KEY`