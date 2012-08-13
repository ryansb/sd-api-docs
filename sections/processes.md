Processes
===

* [Get by time](#get-by-time) - returns the processes for specific time for the specified server.
* [Get range](#get-range) - returns the timestamps for which process list snapshots exist.


Get by time
--
`GET /processes/getByTime`

Returns the processes for specific time for the specified server. Use the getRange method to find out the specific timestamp process list snapshots are available for, then use this getByTime method to return the actual process list.

**Parameters**

* `deviceId` *string*
* `time` *string* - UTC time for the process snapshot, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.

**Request**

`GET http://api.serverdensity.com/VERSION/processes/getByTime?account=llama.serverdensity.com&apiKey=KEY&deviceId=4c8ed3d1150ba02f1fb30f00&time=2010-11-25T10:15:00`


Get range
--
`GET /processes/getRange`

Returns the timestamps for which process list snapshots exist.

**Parameters**

* `deviceId` *string*
* `rangeStart` *string* - UTC start time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.
* `rangeEnd` *string* - UTC end time for the range, [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted without a timezone.

**Request**

`GET http://api.serverdensity.com/VERSION/processes/getRange?account=llama.serverdensity.com&apiKey=KEY&deviceId=4c8ed3d1150ba02f1fb30f00&rangeStart=2010-11-25T10:00:00&rangeEnd=2010-11-25T10:15:00`