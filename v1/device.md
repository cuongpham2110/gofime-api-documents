### /api/v1/devices/{device_id}

##### 1. `GET` /api/v1/devices/{device_id}

**Description:** Get information of specific devices in device list

**Parameters:**

| Parameter name | Data Type |            Position             | Valid value                                                  | Property |
| :------------: | :-------: | :-----------------------------: | ------------------------------------------------------------ | -------- |
|    API Key     |  String   | HTTP Authorization Basic Header |                                                              | Required |
|   device_id    |  String   |              Path               |                                                              | Required |
|     fields     |  String   |              Query              | device_id, status, hardware, firmware, sim_phone_number, sos_phone_number, report_interval, config, status | Optional |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device":{
        "device_id": "device_id",
        "status": "status",
        "hardware": "hardware",
        "firmware": "firmware",
        "sim_phone_number": "sim_phone_number",
        "sos_phone_number": "sos_phone_number",
        "report_interval": 180,
        "config": [C1, C2, C3, C4, C5, C6, C7],
        "safezones": "GET /api/v1/devices/device_id/safezones"
    },
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

##### 2. `PATCH` /api/v1/devices/{device_id}

**Description:** Modify specific device configuration.

**Parameters:**

| Parameter name |  Data Type  |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|   device_id    |   String    |              Path               | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description                                                  | Data Type  | Valid value                                              | Property |
| ------------------- | ------------------------------------------------------------ | ---------- | -------------------------------------------------------- | -------- |
| device_id           | Device ID                                                    | String     |                                                          | Required |
| sos_phone_number    | SOS phone number                                             | String     |                                                          | Optional |
| report_interval     | Report interval. Unit is second                              | Number     | 20, 40, 60, 180, 300, 600, 1200, 1800, 3600, 7200, 10800 | Optional |
| config              | Device configuration includes: <br/>C1: Enable saving mode<br/>C2: Enable send SMS to inform operation mode<br/>C3: Enable send SMS to inform out of all safezone<br/>C4: Enable send SMS to inform out of battery<br/>C5: Enable send SMS in case of holding SOS button<br/>C6: Stop tracking at night<br/>C7: Disable manual power off<br><br>Array should be size of 7 elements. If array size is different from 7, request may return code 400. Data type for C1 to C7 is bool. In JSON format, it is **true** for **false** | Bool Array |                                                          | Optional |

```json
{
	"device":{
        "device_id": "device_id",
        "sos_phone_number": "sos_phone_number",
        "report_interval": 180,
        "config": [C1, C2, C3, C4, C5, C6, C7]
    }
}
```



> **NOTE:**
>
> * This method is only valid when device status is **online**. If device status is **offline**, request may return code 460
> * This method is interacting with real device, therefore it will takes more times than other request
> * Other reason leading to failure in a transaction/request will make request return code 460



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



> `Code`: **460** TRANSACTION_FAILURE

```json
{
	"status": {
		"code": 460,
		"name": "TRANSACTION_FAILURE",
		"message": "Device is offline or Transaction failure"
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



------

##### 3. `DELETE` /api/v1/devices/{device_id}

**Description:** Delete devices in user's device list.

**Parameters:**

| Parameter name | Data Type |            Position             |
| :------------: | :-------: | :-----------------------------: |
|    API Key     |  String   | HTTP Authorization Basic Header |
|   device_id    |  String   |              Path               |



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

##### 4.  `POST` `PUT` /api/v1/devices/{device_id}

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