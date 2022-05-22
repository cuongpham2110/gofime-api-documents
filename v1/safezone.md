### /api/v1/devices/{device_id}/safezones/{safezone_id}

##### 1. `GET` /api/v1/devices/{device_id}/safezones/{safezone_id}

**Description:** Get information of specific safezone of specific device.

**Parameters:**

| Parameter name |  Type  |            Position             | Valid value                                           | Property |
| :------------: | :----: | :-----------------------------: | ----------------------------------------------------- | -------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                       | Required |
|   device_id    | String |              Path               |                                                       | Required |
|  safezone_id   | Number |              Path               | 1, 2, 3, 4, 5                                         | Required |
|     fields     | String |              Query              | device_id, safezone_id, center, radius, label, status | Optional |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device": {
		"device_id": "device_id",
		"safezone": {
			"safezone_id": "safezone_id",
			"center": {
				"longitude": "longitude",
				"latitude": "latitude"
			},
			"radius": 200,
			"label": "label"
		}
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

| Response parameters name | Description                    | Data Type    | Valid value   |
| ------------------------ | ------------------------------ | ------------ | ------------- |
| device_id                | Device ID                      | String       |               |
| safezone_id              | Safezone ID                    | Number       | 1, 2, 3, 4, 5 |
| center                   | Safezone circle center         | Object       |               |
| longitude                | Center longitude               | Float String |               |
| latitude                 | Center latitude                | Float String |               |
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

##### 2. `PATCH` /api/v1/devices/{device_id}/safezones/{safezone_id}

**Description:** Modify safezone property partially

**Parameters:**

| Parameter name |    Type     |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|   device_id    |   String    |              Path               | Required |
|  safezone_id   | Number      |              Path               | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description                    | Data Type    | Valid value   | Property |
| ------------------- | ------------------------------ | ------------ | ------------- | -------- |
| longitude           | Center longitude               | Float String |               | Optional |
| latitude            | Center latitude                | Float String |               | Optional |
| radius              | Safezone radius. Unit is meter | Number       |               | Optional |
| label               | Safezone label                 | String UTF-8 |               | Optional |

```json
{
	"device": {
		"safezone": {
			"center": {
				"longitude": "longitude",
				"latitude": "latitude"
			},
			"radius": 200,
			"label": "label"
		}
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

##### 3. `DELETE` /api/v1/devices/{device_id}/safezones/{safezone_id}

**Description:** Modify safezone property partially

**Parameters:**

| Parameter name |    Type     |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|   device_id    |   String    |              Path               | Required |
|      body      | JSON object |              Body               | Required |

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

##### 4.  `POST` `PUT` /api/v1/devices/{device_id}/safezones/{safezone_id}

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
