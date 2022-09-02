# Şarj Ağı Brand API
This page contains server endpoints opened to developers as part of the Şarj Ağı partnership.
To obtain an access token, please contact us via our website.

> `Important Note :` all {StationObject} returns the following station object.

```sh
{
    "loc":{
        "type":"Point",
        "coordinates":[
            latitude [Float],
            longitude [Float]
        ]
    },
    "_id":unique id [ObjectID],
    "title":title  [String],
    "address":address  [String],
    "note":notes  [String],
    "usage_hours":usage hours [String],
    "parking_slots":parking slot,
    "tariff_information":tariff information [String],
    "nearby_places":nearby places [String],
    "sockets":[
        CHAdeMO [String] ,
        CCS/SAE [String],
        TYPE2 [String]
    ],
    "type":only AC DC [String],
    "like":like count [String],
    "station_owner":station owner [String],
    "station_code":station code [String],
    "updatedAt": updated date [Date]
}
```
---
## All Stations
Returns all current station datas stored on our server. 
There is no output limitation, so use it carefully. It may cause performance problems in the interface.

```sh
GET https://sarjagi.com/api/brand/station/all?token=YOUR_ACCESS_TOKEN
```

#### Request Information
> Method : GET
Response Format : JSON

#### Response Objects
```sh
[
    {StationObject}
    ...
]
```

-----

## Nearby Stations
Returns the stations closest to the specified location.

```sh
lg = longitude [Float]
lt = latiude [Float]
distance = radius in meters [Int]

GET  https://sarjagi.com/api/brand/station/near?lg=32.661659&lt=40.467954&distance=1000&token=YOUR_ACCESS_TOKEN
```

#### Request Information
> Method : GET
Response Format : JSON

#### Response Objects
```sh
[
    {StationObject}
    ...
]
```
-----

## On-Road Stations
Returns the data of the nearest stations on the route.

```sh
POST https://sarjagi.com/api/brand/station/onroad?token=YOUR_ACCESS_TOKEN

PARAMETERS
{
    "locationIn" : [ //start location
        latiude [Float],
        longitude [Float]
    ],
    "locationOut" : [ //end location
        latiude [Float],
        longitude [Float]
    ]
}
```
#### Request Information
> Method : POST
Content-Type : application/json
Response Format : JSON

#### Response Objects
```sh
[
    {StationObject}
    ...
]
```

-----
## Get Station Detail
Returns station detail by object _id.
```sh
id = station id [ObjectID]

GET  https://sarjagi.com/api/brand/station/detail?id=62ea24bfd7f741b0c2997598&token=YOUR_ACCESS_TOKEN
```

#### Request Information
> Method : GET
Response Format : JSON

#### Response Objects
```sh
{StationObject}
```
