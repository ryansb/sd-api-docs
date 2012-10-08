Services
===
* [List](#list) - returns all configured services.
* [Regions Info](#regions-info) - returns info about monitoring node regions.

List
--
`GET /services/list`

Returns all configured services

**Request**

`https://api.serverdensity.com/VER/services/list?account=llama.serverdensity.com`

You can specify an optional `regionsInfo=true` parameter which will include details about each monitoring region within the output for this call, instead of making a separate call to the regions info method below.

**Response**

* `cT` - The last check time.
* `sT` - The slow threshold in ms, above which the request will be considered "slow".
* `uptime` - The raw check counts, including counts in each state.
* `uptimeStats` - Calculated uptime percentages based on the `uptime` counts.

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
                "cT": {
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
                "sT": 1500,
                "slow": false,
                "status": "up",
                "timeout": 10,
                "uptime": { 
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
                "uptimeStats": {
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

Regions Info
--
`GET /services/regionsInfo`

**Request**

`https://api.serverdensity.com/VER/services/regionsInfo?account=llama.serverdensity.com`

**Response**

```json
{
    "status": 1,
    "data": {
        "eu-west-1": {
            "name": "Ireland - Dublin (Amazon)",
            "location": {
                "city": "Dublin",
                "country": "Ireland",
                "lat": "53.347778",
                "long": "-6.259722"
            },
            "provider": "Amazon"
        },
        "eu-uk-1": {
            "name": "UK - London (Rackspace)",
            "location": {
                "city": "London",
                "country": "UK",
                "lat": "51.507222",
                "long": "-0.1275"
            },
            "provider": "Rackspace"
        },
        "ap-northeast-1": {
            "name": "Japan - Tokyo (Amazon)",
            "location": {
                "city": "Tokyo",
                "country": "Japan",
                "lat": "35.689506",
                "long": "139.6917"
            },
            "provider": "Amazon"
        },
        "ap-southeast-1": {
            "name": "Singapore (Amazon)",
            "location": {
                "city": "Singapore",
                "country": "Singapore",
                "lat": "1.283333",
                "long": "103.833333"
            },
            "provider": "Amazon"
        },
        "ap-aus-1": {
            "name": "Australia - Sydney (Servers Australia)",
            "location": {
                "city": "Sydney",
                "country": "Australia",
                "lat": "-33.859972",
                "long": "151.211111"
            },
            "provider": "Servers Australia"
        },
        "us-east-1": {
            "name": "USA - Virginia (Amazon)",
            "location": {
                "city": "Virginia",
                "country": "USA",
                "lat": "37.540972",
                "long": "-77.432889"
            },
            "provider": "Amazon"
        },
        "us-chi-1": {
            "name": "USA - Chicago (Rackspace)",
            "location": {
                "city": "Chicago",
                "country": "USA",
                "lat": "41.881944",
                "long": "-87.627778"
            },
            "provider": "Rackspace"
        },
        "us-west-1": {
            "name": "USA - Northern California (Amazon)",
            "location": {
                "city": "Northern California",
                "country": "USA",
                "lat": "38.555556",
                "long": "-121.468889"
            },
            "provider": "Amazon"
        },
        "sa-br-1": {
            "name": "Brazil - São Paulo (Amazon)",
            "location": {
                "city": "São Paulo",
                "country": "Brazil",
                "lat": "-23.55",
                "long": "-46.633333"
            },
            "provider": "Amazon"
        }
    }
}
```