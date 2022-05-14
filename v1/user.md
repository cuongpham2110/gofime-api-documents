### /api/v1/user

##### 1. `GET` /api/v1/user

**Description:** Get user information.

**Parameters:**

| Parameter name | Data Type |            Position             | Valid value                                               | Property |
| :------------: | :-------: | :-----------------------------: | --------------------------------------------------------- | -------- |
|    API Key     |  String   | HTTP Authorization Basic Header |                                                           | Required |
|     fields     |  String   |              Query              | account, name, phone, api, service, devices, status       | Optional |
|      sort      |  String   |              Query              | **desc** (descending) or **asc** (ascending) by device_id | Optional |



**Response:**

**Response content type:** application/json

> `Code`: **200** OK

```JSON
{
	"info": {
		"account": "account",
		"name": "user_name",
		"phone": "user_phone",
		"created_at": "DD/MM/YYYY",
		"api": {
			"per_minute": 0,
			"per_day": 0,
		},
		"service": {
			"googlemap": "0/0",
			"sms": "0/0"
		},
		"devices": [
			{
				"device_id": "device_id",
				"nickname": "nickname",
				"type: "type",
				"icon": "icon_code",
				"color": "color_code",
				"devlink": "GET /api/v1/devices/{device_id}"
			},
			{
				"device_id": "device_id",
				"nickname": "nickname",
				"type: "type",
				"icon": "icon_code",
				"color": "color_code",
				"devlink": "GET /api/v1/devices/{device_id}"
			}
		]
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

| Response parameters name | Description                                                  | Data Type | Valid value                                                  |
| ------------------------ | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ |
| account                  | Account name                                                 | String    |                                                              |
| name                     | Name that user registered to service                         | String    |                                                              |
| phone                    | Phone that user registered to service                        | String    |                                                              |
| created_at               | Datetime that user create account. See [reference format](datetime.md) | String    |                                                              |
| api                      | API usage report                                             | Object    |                                                              |
| per_minute               | API summary in last minutes                                  | Number    |                                                              |
| per_day                  | API summary in current day                                   | Number    |                                                              |
| services                 | Service usage report                                         | Object    |                                                              |
| googlemap                | 3rd party Googlemap service report                           | Number    |                                                              |
| sms                      | Gofime SMS service report                                    | Number    |                                                              |
| devices                  | General Information of all devices including device_id, icon and color. icon and color is customized in each user account | Object    |                                                              |
| device_id                | Device ID                                                    | String    |    
| nickname                 | Device nickname                                      	  | String    |
| type                 | Device type                                      	  | String    | Gofime
| icon                     | Icon of device. This is customized for each account          | String    | user, users, male, female, child, blind, deaf, wheelchair-alt, street-view, venus, mars, paw, motorcycle, bicycle, car, taxi, bus, truck, ship, rocket, plane, paper-plane, frown, meh, smile, bell, bookmark, flag, tags, sun, tint, futbol, star, heart, diamond, suitcase |
| color                    | Icon of device. This is customized for each account          | String    | red, green, yellowgreen, blue, violet, turquoise, teal, springgreen, slateblue, sienna, purple, orchid, brown, crimson, darkcyan, darkgreen, darkmagenta, darkseagreen, darkslategrey, deeppink, gold, indigo, black, lightseagreen, olivedrab, orange, palevioletred, salmon, skyblue, indianred |



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

##### 2. `PATCH` /api/v1/user

**Description:** Modify user information partially.

**Parameters:**

| Parameter name |  Data Type  |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description                                         | Data Type | Valid value                                                  | Property                                       |
| ------------------- | --------------------------------------------------- | --------- | ------------------------------------------------------------ | ---------------------------------------------- |
| name                | Name that user registered to service                | String    |                                                              | Optional                                       |
| phone               | Phone that user registered to service               | String    |                                                              | Optional                                       |
| device_id           | Device ID                                           | String    |                                                              | Required<br>( If modifying device properties ) |
| passcode            | Device passcode                                     | String    |                                                              | Required<br>( If modifying device properties ) |
| nickname                 | Device nickname                                | String    |
| icon                | Icon of device. This is customized for each account | String    | user, users, male, female, child, blind, deaf, wheelchair-alt, street-view, venus, mars, paw, motorcycle, bicycle, car, taxi, bus, truck, ship, rocket, plane, paper-plane, frown, meh, smile, bell, bookmark, flag, tags, sun, tint, futbol, star, heart, diamond, suitcase | Optional                                       |
| color               | Icon of device. This is customized for each account | String    | red, green, yellowgreen, blue, violet, turquoise, teal, springgreen, slateblue, sienna, purple, orchid, brown, crimson, darkcyan, darkgreen, darkmagenta, darkseagreen, darkslategrey, deeppink, gold, indigo, black, lightseagreen, olivedrab, orange, palevioletred, salmon, skyblue, indianred | Optional                                       |



```
{
	"info":{
		"name": "user_name",
		"phone": "user_phone",
		"devices": [
			{
				"id": "device_id",
				"passcode": "passcode",
				"nickname": "nickname",
				"icon": "icon_code",
				"color": "color_code",
			},
			{
				"id": "device_id",
				"passcode": "passcode",
				"nickname": "nickname",
				"icon": "icon_code",
				"color": "color_code",
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

##### 3. `POST` `PUT` `DELETE` /api/v1/user

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
