### /v1/devices/{device_id}/safezones

#### 1. `GET` /v1/devices/{device_id}/safezones

**:star: <ins>Description:</ins>** Get information of safezones of specific device

**:star: <ins>Request parameters:</ins>**

| Parameter name |  Type  |            Position             | Valid value                                           | Property |
| :------------: | :----: | :-----------------------------: | ----------------------------------------------------- | -------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                       | Required |
|   device_id    | String |              Path               |                                                       | Required |


**:star: <ins>Response format by response code:</ins>**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device": {
		"device_id": "device_id",
		"safezones": [
			{
				"safezone_id": 1,
				"center": {
					"longitude": 0.0,
					"latitude": 0.0
				},
				"radius": 200,
				"label": "label"
			},
			{
				"safezone_id": 2,
				"center": {
					"longitude": 0.0,
					"latitude": 0.0
				},
				"radius": 200,
				"label": "label"
			},
			{
				"safezone_id": 3,
				"center": {
					"longitude": 0.0,
					"latitude": 0.0
				},
				"radius": 200,
				"label": "label"
			},
			{
				"safezone_id": 4,
				"center": {
					"longitude": 0.0,
					"latitude": 0.0
				},
				"radius": 200,
				"label": "label"
			},
			{
				"safezone_id": 5,
				"center": {
					"longitude": 0.0,
					"latitude": 0.0
				},
				"radius": 200,
				"label": "label"
			}
		],
		"status": {
			"code": 200,
			"name": "OK",
			"message": "Success",
			"additional_message": ""
		},
		"doclink": "https://gofime.vn/developers/documentation"
	}
}
```

**Response parameters:**

| Response parameters name | Description                    | Data Type    | Valid value   |
| ------------------------ | ------------------------------ | ------------ | ------------- |
| device_id                | Device ID                      | String       |               |
| safezone_id              | Safezone ID                    | Number       | 1, 2, 3, 4, 5 |
| center                   | Safezone circle center         | Object       |               |
| longitude                | Center longitude               | Double  |               |
| latitude                 | Center latitude                | Double  |               |
| radius                   | Safezone radius. Unit is meter | Number       |               |
| label                    | Safezone label                 | String       |               |



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
<br />

#### 2.  `POST` `PUT` `PATCH` `DELETE` /v1/devices/{device_id}/safezones

**:star: <ins>Description:</ins>** These methods are not supported.

**:star: <ins>Request parameters:</ins>** None

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
	"doclink": "https://gofime.vn/developers/documentation"
}
```



#### :house: [GO BACK TO API V1 HOMEPAGE](README.md)

------

> Copyright (c) Gofime Ltd
