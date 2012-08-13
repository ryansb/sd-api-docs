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

* `deviceId` *string*- use the devices/list method to find the deviceId

**Request**

`GET http://api.serverdensity.com/VERSION/metrics/getLatest?account=llama.serverdensity.com&apiKey=KEY&deviceId=4c8ed3d1150ba02f1fb30f00`


Get range
--
`GET /metrics/getRange`

Returns the time series values for the specified metric between the specified date ranges. Specify either a deviceId or a serviceId to get the data.

**Parameters**

* `deviceId` *string*- use the `devices/list` method to find the deviceId.
* `serviceId` *string*- use the `services/list` method to find the deviceId.
* `metric` *string*.
* `rangeStart` *- string*UTC start time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.
* `rangeEnd` *- string*UTC end time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.

**Metrics**

* apacheStatus
* cpuStats
* diskUsage
* http (services only)
* iisStatus
* ioStats
* loadAvrg
* memPhys
* memSwap
* mongo
* mysql
* networkTraffic
* nginxStatus
* plugins
* processes
* rabbitmqConn
* rabbitmqQueues
* sqlServer

**Request**

`GET http://api.serverdensity.com/VERSION/metrics/getRange?account=llama.serverdensity.com&apiKey=KEY&deviceId=4c8ed3d1150ba02f1fb30f00&metric=loadAvrg&rangeStart=2010-11-25T10:00:00&rangeEnd=2010-11-25T10:15:00`


Postback
--
`POST /metrics/postback`

Post back metrics without needing the agent. 

**Parameters**

* `deviceId` *string* - use the `devices/list` method to find the deviceId
* `payload` *string* - A JSON payload containing the metrics.

**Payload**

When the agent reports back it sends a JSON payload containing the values for all the metrics from the server. You can send the same payload through the API containing all the metrics, or just some of them. This allows you to post data into Server Density without the agent e.g. from your own systems. The payload will be evaluated as if the agent had posted back, meaning any values will be processed for alerts and graphed like normal.

You can see what the agent is posting back by enabling debug mode. The payload will then be written to the agent log file for each check cycle.

**Agent key**

The payload must contain at least the agent key which is used to identify the device you are posting back to. Note this is not the same as the deviceId.

* `agentKey` - *string* - you can retrieve this by clicking the Key link from the Devices tab.

**Restrictions**

You cannot post back more often than every 60 seconds. You will receive an error if you try.

**Examples**

To post back the load average your payload would look like this:

```json
{ 	
	"agentKey" : "6d6ed3d1150ba02f1aa30c43",
 	"loadAvrg" : "0.12" 
}
```

To post back network traffic:

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

To post back a plugin called MongoDBCount:

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

**Request**

`POST http://api.serverdensity.com/VERSION/metrics/postback?account=llama.serverdensity.com&apiKey=KEY&deviceId=4c8ed3d1150ba02f1fb30f00&payload={"agentKey" : "6d6ed3d1150ba02f1aa30c43" ... }`