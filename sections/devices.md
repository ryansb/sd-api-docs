Devices
===

* [Add](#add) - adds a new device with a default "no data received" alert.
* [Add aggregate](#add-aggregate) - adds a new aggegate device.
* [Add group](#add-group) - adds a new group with the specified name.
* [Delete](#delete) - marks the specified device for deletion and pauses all alerts.
* [Edit aggregate](#edit-aggregate) - edits the stored details about the aggregate device.
* [Get by group](#get-by-group) - returns all devices belonging to the specified group.
* [Get by host name](#get-by-host-name) - returns the device with the specified hostname. 
* [Get by id](#get-by-id) - returns the device with the specified ID.
* [Get by ip](#get-by-ip) - returns the device with the specified IP address.
* [Get by name](#get-by-name) - returns the device with the specified name.
* [List](#list) - returns a list of all devices.
* [List groups](#list-groups) - returns a list of all device groups.
* [Count](#count) - returns a count devices for the account.
* [Rename](#rename) - renames the specified device with the new specified name.


Add
--
`POST /devices/add`

Adds a new device with a default "no data received" alert.

**Parameters**

All parameter values should be URL encoded.

* `name` *string*
* `ip` *string* (optional) 
* `group` *string* (optional) If the group doesn't exist, it will be created.
* `location` *string* (optional) 
* `provider` *string* (optional) 
* `notes` *string* (optional) 
* `userId` *string* (optional) If specified the default alerts (no data received) will be added for this userId, otherwise will be the authenticated user.

**Request**

`POST http://api.serverdensity.com/VERSION/devices/add?account=llama.serverdensity.com&name=Test+2&ip=10.0.0.2&location=Hat&provider=Cheese&notes=nope&userId=4cd97209023d06b231000000`


Add aggregate
--
`POST /devices/addAggregate`

Adds a new aggregate device with the supplied device ids.

**Parameters**

All parameter values should be URL encoded.

* `name` *string*
* `deviceIds` *string* (optional) Comma separated list
* `group` *string* (optional) If the group doesn't exist, it will be created.
* `showDashboard` *int* (optional) Display on the dashboard.

**Request**

`POST http://api.serverdensity.com/VERSION/devices/addAggregate?account=llama.serverdensity.com&name=New%20Aggregate&deviceIds=4cd97209023d06b231000012,4cd98361417638365271&group=Groupname&showDashboard=1`


Add group
--
`POST /devices/addGroup`

Adds a new group with the specified name.

**Parameters**

All parameter values should be URL encoded.

* `name` *string*

**Request**

`POST http://api.serverdensity.com/VERSION/devices/addGroup?account=llama.serverdensity.com&name=Test+2`


Delete
--
`POST /devices/delete`

Marks the specified device for deletion and pauses all alerts. Devices are not deleted immediately and the deletion can be undone from the web UI for 24 hours before permanent removal.

**Parameters**

* `deviceId` *string*

**Request**

`POST http://api.serverdensity.com/VERSION/devices/delete?account=llama.serverdensity.com&deviceId=4ca70d15150ba0ce3c251001`


Edit aggregate
--
`POST /devices/editAggregate`

Edits an exist aggregate device to the supplied parameters.

**Parameters**

All parameter values should be URL encoded.

* `deviceId` *string*
* `name` *string* (optional)
* `deviceIds` *string* (optional) Comma separated list.
* `group` *string* (optional) If the group doesn't exist, it will be created.
* `showDashboard` *int* (optional) Display on the dashboard.

**Request**

`POST http://api.serverdensity.com/VERSION/devices/editAggregate?account=llama.serverdensity.com&deviceid=4cd729879282342834&name=NewName&deviceIds=4cd97209023d06b231000012,4cd98361417638100001&group=Groupname&showDashboard=1`


Get by group
--
`GET /devices/getByGroup`

Returns all devices belonging to the specified group.

**Parameters**

* `group` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/devices/getByGroup?account=llama.serverdensity.com&group=Hats`


Get by host name
--
`GET /devices/getByHostName`

Returns the device with the specified hostname. This is an optional field set in the web interface when editing device.

**Parameters**

* `hostName` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/devices/getByHostName?account=llama.serverdensity.com&hostName=hats.example.com`


Get by id
--
`GET /devices/getById`

Returns the device with the specified ID.

**Parameters**

* `deviceId` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/devices/getById?account=llama.serverdensity.com&deviceId=4ca70d15150ba0ce3c251001`


Get by name
--
`GET /devices/getByName`

Returns the device with the specified name.

**Parameters**

* `name` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/devices/getByName?account=llama.serverdensity.com&name=Hats`


List
--
`GET /devices/list`

Returns a list of all devices. Optionally provide limit and/or skip values to perform paging. Use the `count` method to determine if you want to perform paging of devices.

**Parameters**

* `limit` *int* (optional)
* `skip` *int* (optional)

**Request**

`GET http://api.serverdensity.com/VERSION/devices/list?account=llama.serverdensity.com`


List groups
--
`GET /devices/listGroups`

Returns a list of all device groups.


**Request**

`GET http://api.serverdensity.com/VERSION/devices/listGroups?account=llama.serverdensity.com`


Count
--
`GET /devices/count`

Returns a count devices for the account.


**Request**

`GET http://api.serverdensity.com/VERSION/devices/count?account=llama.serverdensity.com`


Rename
--
`GET /devices/rename`

Renames the specified device with the new specified name.

**Parameters**

* `deviceId` *string*
* `newName` *string*

**Request**

`GET http://api.serverdensity.com/VERSION/devices/rename?account=llama.serverdensity.com&deviceId=4ca70d15150ba0ce3c251001&newName=Cheese`