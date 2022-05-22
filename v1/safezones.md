### /api/v1/devices/{device_id}/safezones

##### 1. `GET` /api/v1/devices/{device_id}/safezones

**Description:** Get information of safezones of specific device

**Parameters:**

| Parameter name |  Type  |            Position             | Valid value                                           | Property |
| :------------: | :----: | :-----------------------------: | ----------------------------------------------------- | -------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                       | Required |
|   device_id    | String |              Path               |                                                       | Required |
|     fields     | String |              Query              | device_id, safezone_id, center, radius, label, status | Optional |



**Response:**

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

##### 2. `POST` /api/v1/devices/{device_id}/safezones

**Description:** Add new safezones into current device's safezone list or replace current safezone to new one. This method can be applied for multiple safezone.

**Parameters:**

| Parameter name |    Type     |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|   device_id    |   String    |              Path               | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description                    | Data Type    | Valid value   | Property |
| ------------------- | ------------------------------ | ------------ | ------------- | -------- |
| device_id           | Device ID                      | String       |               | Required |
| safezone_id         | Safezone ID                    | Number       | 1, 2, 3, 4, 5 | Required |
| longitude           | Center longitude               | Double  |               | Required |
| latitude            | Center latitude                | Double  |               | Required |
| radius              | Safezone radius. Unit is meter | Number       |               | Required |
| label               | Safezone label                 | String UTF-8 |               | Required |

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
                "safezone_id": 5,
                "center": {
                    "longitude": 0.0,
                    "latitude": 0.0
                },
                "radius": 200,
                "label": "label"
            }
        ]
	}
}
```



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"status": {
		"code": 200,
		"name": "OK",
		"message": "Success",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



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
		"code": 403,
		"name": "FORBIDDEN",
		"message": "Client is blocked and forbidden in all services",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



------

##### 3.  `PUT` `PATCH` `DELETE` /api/v1/devices/{device_id}/safezones

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
