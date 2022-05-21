### /api/v1/devices/{device_id}

##### 1. `GET` /api/v1/devices/{device_id}

**Description:** Get information of specific devices in device list

**Parameters:**

| Parameter name | Data Type |            Position             | Valid value                                                  | Property |
| :------------: | :-------: | :-----------------------------: | ------------------------------------------------------------ | -------- |
|    API Key     |  String   | HTTP Authorization Basic Header |                                                              | Required |
|   device_id    |  String   |              Path               |                                                              | Required |
|     fields     |  String   |              Query              | device_id, nickname, type, icon, color, status, hardware, firmware, sim_phone_number, sos_phone_number, report_interval, config, status | Optional |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```json
{
	"device": {
		"device_id": "device_id",
		"nickname": "nickname",
		"type": "type",
		"icon": "icon_code",
		"color": "color_code",
		"status": "status",
		"firmware": "firmware",
		"sim_phone_number": "sim_phone_number",
		"sos_phone_number": "sos_phone_number",
		"report_interval": 180,
		"config": ["C1", "C2", "C3", "C4", "C5", "C6", "C7"],
		"sim_account_balance": {
			"value": 0,
			"last_update_datetime": "YYYY-MM-DDTHH:mm:ss+07:00"
		},
		"battery": {
			"value": 0,
			"last_update_datetime": "YYYY-MM-DDTHH:mm:ss+07:00"
		},
		"safezones": "GET /api/v1/devices/device_id/safezones"
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

| Response parameters name | Description                                                  | Data Type  | Valid value                                                  |
| ------------------------ | ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| device_id                | Device ID                                                    | String     |                                                              |
| nickname                 | Device nickname                                              | String     |                                                              |
| type                 | Device type                                      	  | String    | Gofime
| icon                     | Icon of device. This is customized for each account          | String    | user, users, male, female, child, blind, deaf, wheelchair-alt, street-view, venus, mars, paw, motorcycle, bicycle, car, taxi, bus, truck, ship, rocket, plane, paper-plane, frown, meh, smile, bell, bookmark, flag, tags, sun, tint, futbol, star, heart, diamond, suitcase |
| color                    | Icon of device. This is customized for each account          | String    | red, green, yellowgreen, blue, violet, turquoise, teal, springgreen, slateblue, sienna, purple, orchid, brown, crimson, darkcyan, darkgreen, darkmagenta, darkseagreen, darkslategrey, deeppink, gold, indigo, black, lightseagreen, olivedrab, orange, palevioletred, salmon, skyblue, indianred |
| status                   | Device status                                                | String     | If device is connecting to server, status is **online**. Otherwise, status is **offline** |
| firmware                 | Current device firmware                                      | String     |                                                              |
| sim_phone_number         | Current SIM (Subscriber Identity Module) inside device       | String     |                                                              |
| sos_phone_number         | SOS number in case of warnings                               | String     |                                                              |
| report_interval          | Report data interval                                         | Number     | 20, 40, 60, 180, 300, 600, 1200, 1800, 3600, 7200, 10800     |
| config                   | Device configuration includes: <br>C1: Enable saving mode<br>C2: Enable send SMS to inform operation mode<br>C3: Enable send SMS to inform out of all safezone<br>C4: Enable send SMS to inform out of battery<br>C5: Enable send SMS in case of holding SOS button<br>C6: Stop tracking at night<br>C7: Disable manual power off | Bool Array | true, false for each element                                 |
| sim_account_balance | SIM account balance | Object |                                                              |
| sim_account_balance.value | SIM account balance value in VND | Number |                                                              |
| sim_account_balance.last_update_datetime | Last update datetime for SIM account balance. See [reference format](datetime.md)  | String |                                                              |
| battery | Device battery | Object |                                                              |
| battery.value | Device battery value in percentage (%) | Number |                                                              |
| battery.last_update_datetime | Last update datetime for device battery value in percentage (%). See [reference format](datetime.md)  | String |                                                              |
| safezones                | Link to get all safezones information                        | Link       |                                                              |



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
| nickname                 | Device nickname                                | String    |  | Optional |
| icon                | Icon of device. This is customized for each account | String    | user, users, male, female, child, blind, deaf, wheelchair-alt, street-view, venus, mars, paw, motorcycle, bicycle, car, taxi, bus, truck, ship, rocket, plane, paper-plane, frown, meh, smile, bell, bookmark, flag, tags, sun, tint, futbol, star, heart, diamond, suitcase | Optional                                       |
| color               | Icon of device. This is customized for each account | String    | red, green, yellowgreen, blue, violet, turquoise, teal, springgreen, slateblue, sienna, purple, orchid, brown, crimson, darkcyan, darkgreen, darkmagenta, darkseagreen, darkslategrey, deeppink, gold, indigo, black, lightseagreen, olivedrab, orange, palevioletred, salmon, skyblue, indianred | Optional                                       |
| sos_phone_number    | SOS phone number                                             | String     |                                                          | Required |
| report_interval     | Report interval. Unit is second                              | Number     | 20, 40, 60, 180, 300, 600, 1200, 1800, 3600, 7200, 10800 | Required |
| config              | Device configuration includes: <br/>C1: Enable saving mode<br/>C2: Enable send SMS to inform operation mode<br/>C3: Enable send SMS to inform out of all safezone<br/>C4: Enable send SMS to inform out of battery<br/>C5: Enable send SMS in case of holding SOS button<br/>C6: Stop tracking at night<br/>C7: Disable manual power off<br><br>Array should be size of 7 elements. If array size is different from 7, request may return code 400. Data type for C1 to C7 is bool. In JSON format, it is **true** for **false** | Bool Array |                                                          | Required |

```json
{
	"device": {
		"device_id": "device_id",
		"nickname": "nickname",
		"icon": "icon_code",
		"color": "color_code",
		"sos_phone_number": "sos_phone_number",
		"report_interval": 180,
		"config": ["C1", "C2", "C3", "C4", "C5", "C6", "C7"]
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



> `Code`: **460** TRANSACTION_FAILURE

```json
{
	"status": {
		"code": 460,
		"name": "TRANSACTION_FAILURE",
		"message": "Device is offline or Transaction failure",
		"additional_message": ""
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
		"message": "Method is not allowed",
		"additional_message": ""
	},
	"doclink": "https://gofime.vn/developers/documentation"
}
```



#### :house: [GO BACK TO API V1 HOMEPAGE](README.md)

------

> Copyright (c) Gofime Ltd
