### /api/v1/devices

##### 1. `GET` /api/v1/devices

**Description:** Get information of all devices.

**Parameters:**

| Parameter name | Data Type |            Position             | Valid value                                                  | Property |
| :------------: | :-------: | :-----------------------------: | ------------------------------------------------------------ | -------- |
|    API Key     |  String   | HTTP Authorization Basic Header |                                                              | Required |
|     fields     |  String   |              Query              | device_id, status, hardware, firmware, sim_phone_number, sos_phone_number, report_interval, config, status | Optional |
|      sort      |  String   |              Query              | **desc** (descending) or **asc** (ascending) by device_id    | Optional |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"devices": [
		{
			"device_id": "device_id",
			"nickname": "nickname",
			"status": "status",
			"hardware": "hardware",
			"firmware": "firmware",
			"sim_phone_number": "sim_phone_number",
			"sos_phone_number": "sos_phone_number",
			"report_interval": 180,
			"config": [C1, C2, C3, C4, C5, C6, C7],
			"safezones": "GET /api/v1/devices/device_id/safezones"
		},
		{
			"device_id": "device_id",
			"nickname": "nickname",
			"status": "status",
			"hardware": "hardware",
			"firmware": "firmware",
			"sim_phone_number": "sim_phone_number",
			"sos_phone_number": "sos_phone_number",
			"report_interval": 180,
			"config": [C1, C2, C3, C4, C5, C6, C7],
			"safezones": "GET /api/v1/devices/device_id/safezones"
		},
	],
	"status": {
		"code": 200,
		"name": "OK",
		"message": "Success"
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```

**Response parameters:**

| Response parameters name | Description                                                  | Data Type  | Valid value                                                  |
| ------------------------ | ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| device_id                | Device ID                                                    | String     |                                                              |
| nickname                 | Device nickname                                              | String     |                                                              |
| status                   | Device status                                                | String     | If device is connecting to server, status is **online**. Otherwise, status is **offline** |
| hardware                 | Device hardware type                                         | String     |                                                              |
| firmware                 | Current device firmware                                      | String     |                                                              |
| sim_phone_number         | Current SIM (Subscriber Identity Module) inside device       | String     |                                                              |
| sos_phone_number         | SOS number in case of warnings                               | String     |                                                              |
| report_interval          | Report data interval                                         | Number     | 20, 40, 60, 180, 300, 600, 1200, 1800, 3600, 7200, 10800     |
| config                   | Device configuration includes: <br>C1: Enable saving mode<br>C2: Enable send SMS to inform operation mode<br>C3: Enable send SMS to inform out of all safezone<br>C4: Enable send SMS to inform out of battery<br>C5: Enable send SMS in case of holding SOS button<br>C6: Stop tracking at night<br>C7: Disable manual power off | Bool Array | true, false for each element                                 |
| safezones                | Link to get all safezones information                        | Link       |                                                              |



> `Code`: **400** BAD_REQUEST

```json
{
	"status": {
		"code": 400,
		"name": "BAD_REQUEST",
		"message": "Invalid parameters"
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
		"message": "Client is unauthorized"
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
		"message": "Client is blocked and forbidden in all services"
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



------

##### 2. `POST` /api/v1/devices

**Description:** Add new devices into current user's device list.

**Parameters:**

| Parameter name |  Data Type  |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description     | Data Type | Valid value | Property |
| ------------------- | --------------- | --------- | ----------- | -------- |
| device_id           | Device ID       | String    |             | Required |
| passcode            | Device passcode | String    |             | Required |

```json
{
	"devices":[
		{
			"device_id": "device_id",
			"passcode": "passcode"
		},
		{
			"device_id": "device_id",
			"passcode": "passcode"
		}
	]
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
		"message": "Success"
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
		"message": "Invalid parameters"
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
		"message": "Client is unauthorized"
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
		"message": "Client is blocked and forbidden in all services"
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



------

##### 3.  `PUT` `PATCH` `DELETE` /api/v1/devices

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
		"message": "Method is not allowed"
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



#### :house: [GO BACK TO API V1 HOMEPAGE](README.md)

------

> Copyright (c) Gofime Ltd
