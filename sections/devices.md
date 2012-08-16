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

```bash
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/devices/add?account=llama.serverdensity.com" \
-d name=Test+2 \
-d ip=10.0.0.2 \
-d location=Hat \
-d provider=Cheese \
-d notes=nope \
-d userId=4cd97209023d06b231000000
```

**Response**

```json
{
    "status": 1,
    "data": {
        "deviceId": "502ce03f13bcb7341e000000",
        "deviceIdOld": 7,
        "agentKey": "70be41f25c0f71a1482b660acf0ed915"
    }
}
```

Add aggregate
--
`POST /devices/addAggregate`

Adds a new aggregate device with the supplied device ids.

**Parameters**

All parameter values should be URL encoded.

* `name` *string*
* `deviceIds` *string* (optional) Comma separated list
* `group` *string* (optional) If the group doesn't exist, it will be created.

**Request**

```bash
curl -v -O /dev/stdout --user admin "http://api.serverdensity.com/VER/devices/addAggregate?account=llama.serverdensity.com" \
-d name=New+Aggregate \
-d deviceIds=4cd97209023d06b231000012,4cd97209023d06b231000013
```

**Response**
```json
{
    "status": 1,
    "data": {
        "name": "New Aggregate",
        "deviceId": "502ce15713bcb70a23000000"
    }
}
```

Add group
--
`POST /devices/addGroup`

Adds a new group with the specified name.

**Parameters**

All parameter values should be URL encoded.

* `name` *string*

**Request**

```bash
curl -v -O /dev/stdout --user admin "http://api.serverdensity.com/VER/devices/addGroup?account=llama.serverdensity.com" \
-d name=New+Group
```

**Response**

```json
{
    "status": 1,
    "data": {
        "name": "New Group"
    }
}
```

Delete
--
`POST /devices/delete`

Marks the specified device for deletion and pauses all alerts. Devices are not deleted immediately and the deletion can be undone from the web UI for 24 hours before permanent removal.

**Parameters**

* `deviceId` *string*

**Request**

```bash
curl -v -O /dev/stdout --user admin "http://api.serverdensity.com/VER/devices/delete?account=llama.serverdensity.com" \
-d deviceId=502ce15713bcb70a23000000
```

**Response**

```json
{
    "status": 1,
    "data": {
        "deviceDeleted": 1
    }
}
```

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

**Request**

```bash
curl -v -O /dev/stdout --user admin "http://api.serverdensity.com/VER/devices/editAggregate?account=llama.serverdensity.com" \
-d deviceId=502ce25a13bcb7ab23000000 \
-d name=Rename+Aggregate
```

**Response**

```json
{
    "status": 1,
    "data": {
        "name": "Rename Aggregate",
        "group": "",
        "deviceId": "502ce25a13bcb7ab23000000"
    }
}
```

Get by group
--
`GET /devices/getByGroup`

Returns all devices belonging to the specified group.

**Parameters**

* `group` *string*

**Request**

`http://api.serverdensity.com/VER/devices/getByGroup?account=llama.serverdensity.com&group=Group+1`

**Response**

```json
{
    "status": 1,
    "data": {
        "devices": [
            {
                "ip": "192.168.1.3",
                "name": "Server 3",
                "group": "Group 1",
                "agentKey": "086cb2c9dd7b3f57d1aaaf71c4170293",
                "device": {
                    "serverId": "502cd62413bcb7731a00000c",
                    "serverIdOld": 3
                }
            },
            {
                "ip": "192.168.1.4",
                "name": "Server 4",
                "hostName": "me.nothing.com",
                "group": "Group 1",
                "agentKey": "790d7a73bba58d2d03ae360f62ba807a",
                "device": {
                    "serverId": "502cd62413bcb7731a00000d",
                    "serverIdOld": 4
                }
            }
        ]
    }
}
```

Get by host name
--
`GET /devices/getByHostName`

Returns the device with the specified hostname. This is an optional field set in the web interface when editing device.

**Parameters**

* `hostName` *string*

**Request**

`http://api.serverdensity.com/VER/devices/getByHostName?account=llama.serverdensity.com&hostName=me.nothing.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "device": {
            "ip": "192.168.1.4",
            "name": "Server 4",
            "hostName": "me.nothing.com",
            "group": "Group 1",
            "agentKey": "790d7a73bba58d2d03ae360f62ba807a",
            "device": {
                "deviceId": "502cd62413bcb7731a00000d",
                "deviceIdOld": 4
            }
        }
    }
}
```

Get by id
--
`GET /devices/getById`

Returns the device with the specified ID.

**Parameters**

* `deviceId` *string*

**Request**

`http://api.serverdensity.com/VER/devices/getById?account=llama.serverdensity.com&deviceId=502cd62413bcb7731a00000d`

**Response**

```json
{
    "status": 1,
    "data": {
        "device": {
            "ip": "192.168.1.4",
            "name": "Server 4",
            "hostName": "me.nothing.com",
            "group": "Group 1",
            "agentKey": "790d7a73bba58d2d03ae360f62ba807a",
            "device": {
                "deviceId": "502cd62413bcb7731a00000d",
                "deviceIdOld": 4
            }
        }
    }
}
```

Get by name
--
`GET /devices/getByName`

Returns the device with the specified name.

**Parameters**

* `name` *string*

**Request**

`http://api.serverdensity.com/VER/devices/getByName?account=llama.serverdensity.com&name=Server+4`

**Response**

```json
{
    "status": 1,
    "data": {
        "device": {
            "ip": "192.168.1.4",
            "name": "Server 4",
            "group": "Group 1",
            "location": null,
            "provider": null,
            "notes": null,
            "agentKey": "790d7a73bba58d2d03ae360f62ba807a",
            "device": {
                "deviceId": "502cd62413bcb7731a00000d",
                "deviceIdOld": 4
            }
        }
    }
}
```

List
--
`GET /devices/list`

Returns a list of all devices. Optionally provide limit and/or skip values to perform paging. Use the `count` method to determine if you want to perform paging of devices.

**Parameters**

* `limit` *int* (optional)
* `skip` *int* (optional)

**Request**

`http://api.serverdensity.com/VER/devices/list?account=llama.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "devices": [
            {
                "name": "Aggregate of 4 and 5",
                "group": "",
                "location": "Aggregate",
                "provider": "Server Density",
                "agentKey": "5ffd4d6c8b800b292993c8d789f783ed",
                "os": "aggregate",
                "latestMetrics": "2012-08-16T11:14:51+00:00",
                "latestMetricsText": "59ms ago",
                "aggregateMembers": [
                    {
                        "name": "Server 4",
                        "deviceId": "502cd62413bcb7731a00000d"
                    },
                    {
                        "name": "Server 5",
                        "deviceId": "502cd62413bcb7731a00000e"
                    }
                ],
                "openAlerts": [],
                "deviceId": "502cd62413bcb7731a00000f",
                "deviceIdOld": 6
            },
            {
                "ip": "192.168.1.1",
                "name": "Server 1",
                "group": null,
                "agentKey": "1a0ca42d414d38f8061584c3b39074cb",
                "os": "windows",
                "latestMetrics": "2012-08-16T11:14:51+00:00",
                "latestMetricsText": "59ms ago",
                "openAlerts": [
                    {
                        "_id": {
                            "$id": "502cd62513bcb7731a00001c"
                        },
                        "accId": 1,
                        "uIds": [
                            1
                        ],
                        "tA": {
                            "sec": 1344988800,
                            "usec": 0
                        },
                        "lN": {
                            "sec": 1344988800,
                            "usec": 0
                        },
                        "sId": 1,
                        "aId": {
                            "$id": "502cd62513bcb7731a00001b"
                        },
                        "nTs": [
                            "email"
                        ],
                        "tV": 35,
                        "fix": 0,
                        "cT": "noData"
                    }
                ],
                "deviceId": "4cb4ab6d7addf98506010000",
                "deviceIdOld": 1
            }
        ]
    }
}
```

List groups
--
`GET /devices/listGroups`

Returns a list of all device groups.

**Request**

`http://api.serverdensity.com/VERSION/devices/listGroups?account=llama.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "groups": [
            "Group 1",
            "New Group"
        ]
    }
}
```

Count
--
`GET /devices/count`

Returns a count devices for the account.

**Request**

`http://api.serverdensity.com/VERSION/devices/count?account=llama.serverdensity.com`

```json
{
    "status": 1,
    "count": 9
}
```

Rename
--
`POST /devices/rename`

Renames the specified device with the new specified name.

**Parameters**

* `deviceId` *string*
* `newName` *string*

**Request**

```bash
curl -v -O /dev/stdout --user admin "http://api.serverdensity.com/VER/devices/rename?account=llama.serverdensity.com" \
-d deviceId=502cd62413bcb7731a00000e \
-d newName=Rename+Device
```

**Response**

```json
{
    "status": 1,
    "data": {
        "deviceRenamed": 1
    }
}
```