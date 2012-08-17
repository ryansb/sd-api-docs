Metrics
===

* [Get latest](#get-latest) - returns the lastest values for all or a specific subset of metrics for the specified server.
* [Get range](#get-range) - returns the time series values for the specified metric between the specified date ranges.
* [List](#list) - returns a list of available metrics for the specified OS.
* [Postback](#postback) - post back metrics without needing the agent. 


Get latest
--
`GET /metrics/getLatest`

Returns the latest values for all metrics for the specified server.

**Parameters**

* `deviceId` *string* use the `devices/list` method to find the deviceId

**Request**

`http://api.serverdensity.com/VER/metrics/getLatest?account=llama.serverdensity.com&deviceId=4c8ed3d1150ba02f1fb30f00`

**Response**

```json
{
    "status": 1,
    "data": {
        "latestMetrics": {
            "lastUpdated": "2012-08-17T09:36:10+00:00",
            "metrics": {
                "mongodb": {
                    "name": "MongoDB",
                    "metrics": {
                        "mongoAvailableConnections": {
                            "name": "Available Connections",
                            "formatDecimals": 0,
                            "value": 2310
                        },
                        "mongoCommandOps": {
                            "name": "Commands",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 3821.4567
                        },
                        "mongoCurrentConnections": {
                            "name": "Current Connections",
                            "formatDecimals": 0,
                            "value": 5552
                        },
                        "mongoDeleteOps": {
                            "name": "Deletes",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 1933.652
                        },
                        "mongoGetmoreOps": {
                            "name": "Getmores",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 7312.6655
                        },
                        "mongoAccesses": {
                            "name": "Index Accesses",
                            "formatDecimals": 0,
                            "value": 4339
                        },
                        "mongoHits": {
                            "name": "Index Hits",
                            "formatDecimals": 0,
                            "value": 1308.9924
                        },
                        "mongoMissRatio": {
                            "name": "Index Miss Ratio",
                            "formatDecimals": 2,
                            "value": 8102.7958
                        },
                        "mongoMisses": {
                            "name": "Index Misses",
                            "formatDecimals": 0,
                            "value": 6379.4077
                        },
                        "mongoInsertOps": {
                            "name": "Inserts",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 1177.289
                        },
                        "mongoReplOptime": {
                            "name": "Last optime",
                            "units": "s",
                            "formatDecimals": 0,
                            "value": 47
                        },
                        "mongoMappedMem": {
                            "name": "Mapped Memory",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 9098
                        },
                        "mongoMsgAsserts": {
                            "name": "Message Asserts",
                            "formatDecimals": 0,
                            "value": 8854.4195
                        },
                        "mongoQueryOps": {
                            "name": "Queries",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 6967.1346
                        },
                        "mongoRamHeadroom": {
                            "name": "RAM Headroom",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": -652
                        },
                        "mongoRegularAsserts": {
                            "name": "Regular Asserts",
                            "formatDecimals": 0,
                            "value": 3593.6502
                        },
                        "mongoUpdateOps": {
                            "name": "Updates",
                            "units": "/s",
                            "formatDecimals": 2,
                            "value": 9716.9346
                        },
                        "mongoUserAsserts": {
                            "name": "User Asserts",
                            "formatDecimals": 0,
                            "value": 4129.4406
                        },
                        "mongoVirtualMem": {
                            "name": "Virtual Memory",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 9888
                        },
                        "mongoWarningAsserts": {
                            "name": "Warning Asserts",
                            "formatDecimals": 0,
                            "value": 9014.3892
                        }
                    }
                },
                "plugins": {
                    "name": "Plugins",
                    "metrics": {
                        "Plugin1": {
                            "details": {
                                "name": "Plugin 1",
                                "formatDecimals": 4,
                                "pNm": "Plugin1"
                            },
                            "values": {
                                "hats": 1,
                                "cats": 5,
                                "rats": 3
                            }
                        },
                        "Plugin2": {
                            "details": {
                                "name": "Plugin 2",
                                "formatDecimals": 4,
                                "pNm": "Plugin2"
                            },
                            "values": {
                                "snap": 8,
                                "crackle": 6,
                                "pop": 2
                            }
                        }
                    }
                },
                "system": {
                    "name": "System",
                    "metrics": {
                        "loadAvrg": {
                            "name": "CPU utilisation",
                            "units": "%",
                            "formatDecimals": 0,
                            "value": 10.1
                        },
                        "diskUsage": {
                            "name": "Disk usage",
                            "units": "%",
                            "formatDecimals": 0,
                            "mt": "Mount",
                            "fs": "Filesystem",
                            "us": "Used %",
                            "values": [
                                {
                                    "fs": "root",
                                    "us": 87,
                                    "av": 20,
                                    "cp": "96%",
                                    "mt": "C:"
                                },
                                {
                                    "fs": "swap",
                                    "us": 9,
                                    "av": 82,
                                    "cp": "88%",
                                    "mt": "/proc/swap"
                                }
                            ]
                        },
                        "networkTraffic": {
                            "name": "Network tx/rx",
                            "formatDecimals": 0,
                            "if": "Interface",
                            "rx": "Received",
                            "tx": "Transferred",
                            "txMByteS": "MB/s Transferred",
                            "rxMByteS": "MB/s Received",
                            "txMBitS": "Mb/s Transferred",
                            "rxMBitS": "Mb/s Received",
                            "values": [
                                {
                                    "if": "eth0",
                                    "rx": 8.1,
                                    "tx": 7.1,
                                    "txMBitS": 10.1,
                                    "rxMBitS": 4.5,
                                    "txMByteS": 10.4,
                                    "rxMByteS": 8.1
                                },
                                {
                                    "if": "eth1",
                                    "rx": 5.5,
                                    "tx": 1.1,
                                    "txMBitS": 3.1,
                                    "rxMBitS": 7.8,
                                    "txMByteS": 5.8,
                                    "rxMByteS": 8.4
                                },
                                {
                                    "if": "eth2",
                                    "rx": 7.5,
                                    "tx": 4.2,
                                    "txMBitS": 1.3,
                                    "rxMBitS": 3.9,
                                    "txMByteS": 2.1,
                                    "rxMByteS": 9.2
                                }
                            ]
                        },
                        "memSwapUsed": {
                            "name": "Page file used",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 3
                        },
                        "memSwapFree": {
                            "name": "Page file: free",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 3
                        },
                        "memCached": {
                            "name": "Physical memory: cached",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 1
                        },
                        "memPhysFree": {
                            "name": "Physical memory: free",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 8
                        },
                        "memPhysUsed": {
                            "name": "Physical memory: used",
                            "units": "MB",
                            "formatDecimals": 0,
                            "value": 6
                        },
                        "processes": {
                            "name": "Process count",
                            "formatDecimals": 0,
                            "value": 8
                        }
                    }
                }
            },
            "device": {
                "ip": "192.168.1.1",
                "name": "Server 1",
                "deviceId": "4cb4ab6d7addf98506010000",
                "deviceIdOld": 1
            }
        }
    }
}
```

Get range
--
`GET /metrics/getRange`

Returns the time series values for the specified metric between the specified date ranges. Specify either a deviceId or a serviceId to get the data.

**Parameters**

* `deviceId` *string* use the `devices/list` method to find the deviceId.
* `serviceId` *string* use the `services/list` method to find the deviceId.
* `metric` *string*.
* `rangeStart` *string* UTC start time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.
* `rangeEnd` *string* UTC end time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.

**Metrics**

* `apacheStatus`
* `cpuStats`
* `diskUsage`
* `http` (services only)
* `iisStatus`
* `ioStats`
* `loadAvrg`
* `memPhys`
* `memSwap`
* `mongo`
* `mysql`
* `networkTraffic`
* `nginxStatus`
* `plugins`
* `processes`
* `rabbitmqConn`
* `rabbitmqQueues`
* `sqlServer`

**Request**

`GET http://api.serverdensity.com/VER/metrics/getRange?account=llama.serverdensity.com&deviceId=4cb4ab6d7addf98506010000&metric=loadAvrg&rangeStart=2012-08-17T09:00:00&rangeEnd=2012-08-17T09:10:00`

**Response**

```json
{
    "status": 1,
    "data": {
        "metrics": {
            "v": {
                "label": "CPU Utilisation",
                "units": "",
                "data": [
                    [
                        "2012-08-17T09:00:00+00:00",
                        5
                    ],
                    [
                        "2012-08-17T09:01:00+00:00",
                        5.1
                    ],
                    [
                        "2012-08-17T09:02:00+00:00",
                        5.2
                    ],
                    [
                        "2012-08-17T09:03:00+00:00",
                        5.3
                    ],
                    [
                        "2012-08-17T09:04:00+00:00",
                        5.4
                    ],
                    [
                        "2012-08-17T09:05:00+00:00",
                        5.5
                    ],
                    [
                        "2012-08-17T09:06:00+00:00",
                        5.6
                    ],
                    [
                        "2012-08-17T09:07:00+00:00",
                        5.7
                    ],
                    [
                        "2012-08-17T09:08:00+00:00",
                        5.8
                    ],
                    [
                        "2012-08-17T09:09:00+00:00",
                        5.9
                    ],
                    [
                        "2012-08-17T09:10:00+00:00",
                        5.1
                    ]
                ]
            }
        }
    }
}
```


Postback
--
`POST /metrics/postback`

Post back metrics without needing the agent. 

**Parameters**

* `deviceId` *string* use the `devices/list` method to find the deviceId
* `payload` *string* A JSON payload containing the metrics.

**Payload**

When the agent reports back it sends a JSON payload containing the values for all the metrics from the server. You can send the same payload through the API containing all the metrics, or just some of them. This allows you to post data into Server Density without the agent e.g. from your own systems. The payload will be evaluated as if the agent had posted back, meaning any values will be processed for alerts and graphed like normal.

You can see what the agent is posting back by enabling debug mode. The payload will then be written to the agent log file for each check cycle.

**Agent key**

The payload must contain at least the agent key which is used to identify the device you are posting back to. Note this is not the same as the deviceId.

* `agentKey` - *string* - you can retrieve this by clicking the Key link from the Devices tab.

**Restrictions**

You cannot post back more often than every 60 seconds. You will receive an error if you try.

**Example 1 - Load Average**

To post back the load average your payload would look like this:

```json
{ 	
	"agentKey" : "6d6ed3d1150ba02f1aa30c43",
 	"loadAvrg" : "0.12" 
}
```

Request:

```bash
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/metrics/postback?account=llama.serverdensity.com&deviceId=4cb4ab6d7addf98506010000" \
-d payload=%7B%22agentKey%22%3A%226d6ed3d1150ba02f1aa30c43%22%2C%20%22loadAvrg%22%20%3A%20%220.12%22%7D
```
Response:

```json
{
    "status": 1,
    "data": {
        "postback": 1
    }
}
```

**Example 2 - Network Taffic**

```json
{
 	"agentKey" : "6d6ed3d1150ba02f1aa30c43",
	"networkTraffic" :	
	{
		"eth0" :
		{
			"trans_bytes": "53648231",
			"recv_bytes": "15692765"
		}
   	}
}
```

Request:

```bash
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/metrics/postback?account=llama.serverdensity.com&deviceId=4cb4ab6d7addf98506010000" \
-d payload=%7B%0A%20%09%22agentKey%22%20%3A%20%226d6ed3d1150ba02f1aa30c43%22%2C%0A%09%22networkTraffic%22%20%3A%09%0A%09%7B%0A%09%09%22eth0%22%20%3A%0A%09%09%7B%0A%09%09%09%22trans_bytes%22%3A%20%2253648231%22%2C%0A%09%09%09%22recv_bytes%22%3A%20%2215692765%22%0A%09%09%7D%0A%20%20%20%09%7D%0A%7D
```

Response:

```json
{
    "status": 1,
    "data": {
        "postback": 1
    }
}
```

**Eample 3 - `MongoDBCount` plugin**

```json
{
 	"agentKey" : "6d6ed3d1150ba02f1aa30c43",
	"plugins" :
		{
			"MongoDBCount" :
			{
				"users": 25,
				"chairs": 132
			}
		}
}
```

Request:

```bash
curl -v -O /dev/stdout --user USER "http://api.serverdensity.com/VER/metrics/postback?account=llama.serverdensity.com&deviceId=4cb4ab6d7addf98506010000" \
-d payload=%7B%0A%20%09%22agentKey%22%20%3A%20%226d6ed3d1150ba02f1aa30c43%22%2C%0A%09%22plugins%22%20%3A%0A%09%09%7B%0A%09%09%09%22MongoDBCount%22%20%3A%0A%09%09%09%7B%0A%09%09%09%09%22users%22%3A%2025%2C%0A%09%09%09%09%22chairs%22%3A%20132%0A%09%09%09%7D%0A%09%09%7D%0A%7D
```

Response:

```json
{
    "status": 1,
    "data": {
        "postback": 1
    }
}
```