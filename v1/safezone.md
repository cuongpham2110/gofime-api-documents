### /v1/devices/{device_id}/safezones/{safezone_id}

#### 1. `GET` /v1/devices/{device_id}/safezones/{safezone_id}

**:star: <ins>Description:</ins>** Get information of specific safezone of specific device.

**:star: <ins>Request parameters:</ins>**

| Parameter name |  Type  |            Position             | Valid value                                           | Property |
| :------------: | :----: | :-----------------------------: | ----------------------------------------------------- | -------- |
|    API Key     | String | HTTP Authorization Basic Header |                                                       | Required |
|   device_id    | String |              Path               |                                                       | Required |
|  safezone_id   | Number |              Path               | 1, 2, 3, 4, 5                                         | Required |


**:star: <ins>Response format by response code:</ins>**

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
**:star: <ins>cURL example:</ins>**
<pre>
curl --location --request GET 'https://api.gofime.vn:5000/v1/devices/<b>your-device-id</b>/safezones/<b>your-safezone-id</b>' \
--header 'Authorization: Bearer <b>your-api-key</b>'
</pre>


------
<br />

#### 2. `PATCH` /v1/devices/{device_id}/safezones/{safezone_id}

**:star: <ins>Description:</ins>** Modify safezone property partially

**:star: <ins>Request parameters:</ins>**

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



**:star: <ins>Response format by response code:</ins>**

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
**:star: <ins>cURL example:</ins>**
<pre>
curl --location --request GET 'https://api.gofime.vn:5000/v1/devices/<b>your-device-id</b>/safezones/<b>your-safezone-id</b>' \
--header 'Authorization: Bearer <b>your-api-key</b>' \
--header 'Content-Type: application/json' \
--data-raw '{
	"device": {
		"safezone": {
			"center": {
				"longitude": "<b>your-safezone-longitude</b>",
				"latitude": "<b>your-safezone-latitude</b>"
			},
			"radius": <b>your-safezone-radius</b>,
			"label": "<b>your-safezone-label</b>"
		}
	}
}'
</pre>


------
<br />

#### 3. `DELETE` /v1/devices/{device_id}/safezones/{safezone_id}

**:star: <ins>Description:</ins>** Modify safezone property partially

**:star: <ins>Response parameters:</ins>**

| Parameter name |    Type     |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|   device_id    |   String    |              Path               | Required |
|  safezone_id   | Number      |              Path               | Required |
|      body      | JSON object |              Body               | Required |

**:star: <ins>Response format by response code:</ins>**

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
**:star: <ins>cURL example:</ins>**
<pre>
curl --location --request DELETE 'https://api.gofime.vn:5000/v1/devices/<b>your-device-id</b>/safezones/<b>your-safezone-id</b>' \
--header 'Authorization: Bearer <b>your-api-key</b>'
</pre>


------
<br />

#### 4.  `POST` `PUT` /v1/devices/{device_id}/safezones/{safezone_id}

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
