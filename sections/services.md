Services
===
* [List](#list) - returns all configured services.

List
--
`GET /services/list`

Returns all configured services

**Request**

`https://api.serverdensity.com/1.4/services/list?account=example.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "services": [
            {
                "_id": {
                    "$id": "4fdb5c2d1212ba720300010d"
                },
                "accId": 1,
                "avg_response_time": 240.21506309509,
                "cT": {  /* Last check time */
                    "sec": 1344494035,
                    "usec": 64000
                },
                "grp": "",
                "interval": 60,
                "nm": "SD - Blog",
                "notes": "",
                "regionStats": {
                    "Australia - Sydney (Servers Australia)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 615,
                        "lastCheck": {
                            "sec": 1344493728,
                            "usec": 441000
                        }
                    },
                    "Japan - Tokyo (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 490,
                        "lastCheck": {
                            "sec": 1344493790,
                            "usec": 980000
                        }
                    },
                    "Singapore (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 856,
                        "lastCheck": {
                            "sec": 1344493664,
                            "usec": 269000
                        }
                    },
                    "UK - London (Rackspace)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 186,
                        "lastCheck": {
                            "sec": 1344493601,
                            "usec": 64000
                        }
                    },
                    "Ireland - Dublin (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 247,
                        "lastCheck": {
                            "sec": 1344493539,
                            "usec": 747000
                        }
                    },
                    "Brazil - São Paulo (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 633,
                        "lastCheck": {
                            "sec": 1344493913,
                            "usec": 825000
                        }
                    },
                    "USA - Chicago (Rackspace)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 77,
                        "lastCheck": {
                            "sec": 1344493974,
                            "usec": 106000
                        }
                    },
                    "USA - Virginia (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 30,
                        "lastCheck": {
                            "sec": 1344493851,
                            "usec": 370000
                        }
                    },
                    "USA - Northern California (Amazon)": {
                        "status": "up",
                        "statusCode": 200,
                        "response_time": 240,
                        "lastCheck": {
                            "sec": 1344494035,
                            "usec": 82000
                        }
                    }
                },
                "response_time": 77,
                "sT": 1500, /* Slow threshold in ms, above which will consider "slow" */
                "slow": false,
                "status": "up",
                "timeout": 10,
                "uptime": {  /* Raw counts of number of checks */
                    "2012": {
                        "6": {
                            "count": 16640,
                            "slow": 71,
                            "up": 16640
                        },
                        "7": {
                            "count": 41511,
                            "slow": 566,
                            "up": 41507
                        },
                        "8": {
                            "count": 11307,
                            "slow": 115,
                            "up": 11307
                        }
                    }
                },
                "url": "http://blog.serverdensity.com",
                "verifySSL": false,
                "uptimeStats": { /* % stats */
                    "2012": {
                        "6": {
                            "uptime": 100,
                            "slow": 0.42668
                        },
                        "7": {
                            "uptime": 99.99036,
                            "slow": 1.36349
                        },
                        "8": {
                            "uptime": 100,
                            "slow": 1.01707
                        }
                    }
                }
            }
        ]
    }
}
```