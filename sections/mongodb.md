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

`GET http://api.serverdensity.com/VER/mongo/getMaster?account=llama.serverdensity.com&replSetName=rs1`

**Response**

```json
{
    "status": 1,
    "data": {
        "mongoMasterReplicaSets": {
            "rs1": [
                {
                    "serverId": "4f870a371212ba5719000068",
                    "serverIdOld": 320,
                    "name": "sdapp-md1a.wdc.sl",
                    "mongoReplMyId": 0,
                    "mongoReplMyState": 1,
                    "mongoReplMyStateName": "Primary"
                }
            ]
        }
    }
}
```

Get replica set
--
`GET /mongo/getReplicaSet`

Lists all replica sets and their members across the whole account.

**Request**

`GET http://api.serverdensity.com/VER/mongo/getReplicaSet?account=llama.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "mongoReplicaSets": {
            "sdapp1": [
                {
                    "serverId": "4f870a371212ba5719000068",
                    "serverIdOld": 320,
                    "name": "sdapp-md1a.wdc.sl",
                    "mongoReplMyId": 0,
                    "mongoReplMyState": 1,
                    "mongoReplMyStateName": "Primary"
                },
                {
                    "serverId": "4f870d18d4bb3d4158000027",
                    "serverIdOld": 321,
                    "name": "sdapp-md1b.wdc.sl",
                    "mongoReplMyId": 1,
                    "mongoReplMyState": 2,
                    "mongoReplMyStateName": "Secondary"
                },
                {
                    "serverId": "4f873c81b5907f2d0a00002f",
                    "serverIdOld": 340,
                    "name": "sdapp-md1c.sjc.sl",
                    "mongoReplMyId": 2,
                    "mongoReplMyState": 2,
                    "mongoReplMyStateName": "Secondary"
                }
            ],
            "sdapp2": [
                {
                    "serverId": "4f870e0cb5907fd108000005",
                    "serverIdOld": 322,
                    "name": "sdapp-md2a.wdc.sl",
                    "mongoReplMyId": 0,
                    "mongoReplMyState": 1,
                    "mongoReplMyStateName": "Primary"
                },
                {
                    "serverId": "4f87179ab5907f561c00001f",
                    "serverIdOld": 326,
                    "name": "sdapp-md2b.wdc.sl",
                    "mongoReplMyId": 1,
                    "mongoReplMyState": 2,
                    "mongoReplMyStateName": "Secondary"
                },
                {
                    "serverId": "4f873e3d9665c1db5d000211",
                    "serverIdOld": 341,
                    "name": "sdapp-md2c.sjc.sl",
                    "mongoReplMyId": 2,
                    "mongoReplMyState": 2,
                    "mongoReplMyStateName": "Secondary"
                }
            ]
        }
    }
}
```