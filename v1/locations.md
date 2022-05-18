### /api/v1/devices/{device_id}/locations

##### 1. `GET` /api/v1/devices/{device_id}/locations

**Description:** Get information of locations of specific device

**Parameters:**

| Parameter name |  Type  |            Position             | Valid value                                                  | Property                    |
| :------------: | :----: | :-----------------------------: | ------------------------------------------------------------ | --------------------------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                              | Require                     |
|   device_id    | String |              Path               |                                                              | Require                     |
|      type      | String |              Query              | latest, history                                              | Require                     |
| from_datetime  | String |              Query              | See [reference format](datetime.md)                          | Required if type is history |
|  to_datetime   | String |              Query              | See [reference format](datetime.md)                          | Required if type is history |
|      page      | Number |              Query              | Specific page of results to return<br>Default: 1. Minimum: 1 | Optional                    |
|     limit      | Number |              Query              | Maximum number of records per page<br>Default: 100. Minimum: 1. Maximum 1000 | Optional                    |
|      sort      | String |              Query              | **desc** (descending) or **asc** (ascending) by datetime     | Optional                    |
|     fields     | String |              Query              | device_id, type, start_datetime, stop_datetime, size, datetime, longitude, latitude, velocity, battery, device_status, safezone_status, pagination, status | Optional                    |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device":{
		"device_id": "device_id",
        "locations": {
            "type": "type",
            "start_datetime": "01-08-2020 13:50:47",
            "stop_datetime": "04-08-2020 07:10:25",
            "size": 50,
            "records": [
                {
                    "datetime": "01-08-2020 13:51:13",
                    "longitude": "longitude",
                    "latitude": "latitude",
                    "velocity": "velocity",
                    "battery": "battery",
                    "device_status": ["S1", "S2", "S3", "S4", "S5"],
                    "safezone_status": {
                        "inside_safezone_id": [],
                        "outside_safezone_id": [],
                        "undefined_safezone_id": []
                    }
                },
                {
                    "datetime": "01-08-2020 13:51:13",
                    "longitude": "longitude",
                    "latitude": "latitude",
                    "velocity": "velocity",
                    "battery":"battery",
                    "device_status" : ["S1", "S2", "S3", "S4", "S5"],
                    "safezone_status":{
                        "inside_safezone_id":[],
                        "outside_safezone_id":[],
                        "undefined_safezone_id":[]
                    }
                },
            ]
        }	
	},
	"pagination":{
        "current_page_index":10,
	"count": 50,
        "limit": 100,
        "total_page": 10,
        "total_record": 950,
    },
	"status": {
		"code": 200,
		"name": "OK",
		"message": "Success",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```

**Response parameters:**

| Response parameters name | Description                                    | Data Type    | Valid value   |
| ------------------------ | ---------------------------------------------- | ------------ | ------------- |
| device_id                | Device ID                                      | String       |               |
| safezone_id              | Safezone ID.                                   | Number       | 1, 2, 3, 4, 5 |
| type                     | Locations mode. history or latest              | String       |               |
| start_datetime           | Equal to from_datetime                         | String       |               |
| stop_datetime            | Equal to to_datetime                           | String       |               |
| size                     | Total records in current page                  | Number       |               |
| datetime                 | datetime. See [reference format](datetime.md)  | String       |               |
| longitude                | Longitude                                      | Float String |               |
| latitude                 | Latitude                                       | Float String |               |
| velocity                 | Device velocity                                | Float String |               |
| battery                  | Device battery                                 | Number       |               |
| device_status            | Device status                                  | Bool Array   |               |
| S1                       | SOS warning                                    | Bool         |               |
| S2                       | Exceed allowed velocity                        | Bool         |               |
| S3                       | Out of all safezones warning                   | Bool         |               |
| S4                       | LBS warning                                    | Bool         |               |
| S5                       | Low battery warning                            | Bool         |               |
| safezone_status          | Safezone status                                | Object       |               |
| inside_safezone_id       | Safezone IDs that device is inside             | Number array |               |
| outside_safezone_id      | Safezone IDs that device is outside            | Number array |               |
| undefined_safezone_id    | Undefined safezone IDs                         | Number array |               |
| pagination               | Pagination                                     | Object       |               |
| current_page_index       | Current page index                             | Number       |               |
| count                    | Number of locations in curent page		    | Number       |               |
| limit                    | Equal to body request querry parameter `limit` | Number       |               |
| total_page               | Total pages                                    | Number       |               |
| total_record             | Total records                                  | Number       |               |



> `Code`: **400** BAD_REQUEST

```json
{
	"status": {
		"code": 400,
		"name": "BAD_REQUEST",
		"message": "Invalid parameters",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



> `Code`: **401** UNAUTHORIZED

```json
{
	"status": {
		"code": 401,
		"name": "UNAUTHORIZED",
		"message": "Client is unauthorized",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



> `Code`: **403** FORBIDDEN

```json
{
	"status": {
		"code": 401,
		"name": "UNAUTHORIZED",
		"message": "Client is blocked and forbidden in all services",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



------

##### 2.  `POST` `PUT` `PATCH` `DELETE` /api/v1/devices/{device_id}/locations

**Description:** These methods are not supported.

**Parameters:** None

**Response:**

**Response content type:** application/json

> `Code`: **405** METHOD_NOT_ALLOWED

```json
{
	"status": {
		"code": 405,
		"name": "METHOD_NOT_ALLOWED",
		"message": "Method is not allowed",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



#### :house: [GO BACK TO API V1 HOMEPAGE](README.md)

------

> Copyright (c) Gofime Ltd
