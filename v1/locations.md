### /v1/devices/{device_id}/locations

#### 1. `GET` /v1/devices/{device_id}/locations

**:star: <ins>Description:</ins>** Get information of locations of specific device. There are 2 type: history locations and latest locations.

**:star: <ins>Request parameters:</ins>**

| Parameter name |  Type  |            Position             | Valid value                                                  | Property                    |
| :------------: | :----: | :-----------------------------: | ------------------------------------------------------------ | --------------------------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                              | Require                     |
|   device_id    | String |              Path               |                                                              | Require                     |
|      type      | String |              Query              | latest, history                                              | Require                     |
| from_datetime  | String |              Query              | See [reference format](datetime.md)                          | Required if type is history |
|  to_datetime   | String |              Query              | See [reference format](datetime.md)                          | Required if type is history |
|      page      | Number |              Query              | Specific page of results to return<br>Default: 1. Minimum: 1 | Optional                    |
|     limit      | Number |              Query              | Maximum number of records per page<br>Default: 50. Minimum: 1. Maximum 100 | Optional                    |
|      sort      | String |              Query              | **desc** (descending) or **asc** (ascending) by datetime     | Optional                    |


**:star: <ins>Response format by response code:</ins>**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device": {
		"device_id": "device_id",
		"locations": {
			"type": "type",
			"start_datetime": "YYYY-MM-DDTHH:mm:ss+07:00",
			"stop_datetime": "YYYY-MM-DDTHH:mm:ss+07:00",
			"records": [{
					"datetime": "YYYY-MM-DDTHH:mm:ss+07:00",
					"longitude": 0.0,
					"latitude": 0.0,
					"velocity": 0.0,
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
					"battery": 0,
					"device_status": ["S1", "S2", "S3", "S4", "S5"],
					"safezone_status": {
						"inside_safezone_id": [],
						"outside_safezone_id": [],
						"undefined_safezone_id": []
					}
				}
			]
		}
	},
	"pagination": {
		"current_page_index": 10,
		"count_in_page": 50,
		"limit": 100,
		"total_page": 10,
		"total_record": 950
	},
	"status": {
		"code": 200,
		"name": "OK",
		"message": "Success",
		"additional_message": ""
	},
	"doclink": "https://github.com/Chipstack/gofime-api-documents"
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
| longitude                | Longitude                                      | Double       |               |
| latitude                 | Latitude                                       | Double       |               |
| velocity                 | Device velocity. Unit km/h                                | Double       |               |
| battery                  | Device battery. Unit %                                 | Number       |               |
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
| current_page_index       | Current page index                             | Number. Count from 1       |               |
| count_in_page                    | Number of locations in curent page		    | Number       |               |
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
	"doclink": "https://github.com/Chipstack/gofime-api-documents"
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
	"doclink": "https://github.com/Chipstack/gofime-api-documents"
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
	"doclink": "https://github.com/Chipstack/gofime-api-documents"
}
```
**:star: <ins>cURL example:</ins>**
> `Get latest location`
<pre>
curl --location --request GET 'https://api.gofime.vn/v1/devices/<b>your-device-id</b>/locations?type=latest' \
--header 'Authorization: Bearer <b>your-api-key</b>'
</pre>

> `Get history locations`
<pre>

curl --location --request GET 'https://api.gofime.vn/v1/devices/<b>your-device-id</b>/locations?type=history&from_datetime=<b>your-start-datetime</b>&to_datetime=<b>your-end-datetime</b>' \
--header 'Authorization: Bearer <b>your-api-key</b>'

curl --location --request GET 'https://api.gofime.vn/v1/devices/<b>your-device-id</b>/locations?type=history&from_datetime=<b>your-start-datetime</b>&to_datetime=<b>your-end-datetime</b>&limit=<b>your-record-limit-in-a-page</b>&page=<b>your-page-index</b>&sort=<b>your-sort-type</b>' \
--header 'Authorization: Bearer <b>your-api-key</b>'
</pre>


------
<br />

#### 2.  `POST` `PUT` `PATCH` `DELETE` /v1/devices/{device_id}/locations

**:star: <ins>Description:</ins>** These methods are not supported.

**:star: <ins>Response parameters:</ins>** None

**:star: <ins>Response format by response code:</ins>**

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
	"doclink": "https://github.com/Chipstack/gofime-api-documents"
}
```



#### :house: [GO BACK TO API V1 HOMEPAGE](README.md)

------

> Copyright (c) Chipstack Ltd
