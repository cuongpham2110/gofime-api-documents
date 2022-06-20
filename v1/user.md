### /v1/user

#### 1. `GET` /v1/user

**:star: <ins>Description:</ins>** Get user information.

**:star: <ins>Request parameters:</ins>**

| Parameter name | Data Type |            Position             | Valid value                                               | Property |
| :------------: | :-------: | :-----------------------------: | --------------------------------------------------------- | -------- |
|    API Key     |  String   | HTTP Authorization Basic Header |                                                           | Required |
|     fields     |  String   |              Query              | account, name, phone, api, service	                   | Optional |



**:star: <ins>Response format by response code:</ins>**

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

| Response parameters name | Description                                                  | Data Type | Valid value                                                  |
| ------------------------ | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ |
| account                  | Account name                                                 | String    |                                                              |
| name                     | Name that user registered to service                         | String    |                                                              |
| phone                    | Phone that user registered to service                        | String    |                                                              |
| created_at               | Datetime that user create account. Format: DD/MM/YYYY        | String    |                                                              |
| api                      | API usage report                                             | Object    |                                                              |
| per_minute               | API summary in last minutes                                  | Number    |                                                              |
| per_day                  | API summary in current day                                   | Number    |                                                              |
| services                 | Service usage report                                         | Object    |                                                              |
| googlemap                | 3rd party Googlemap service report                           | Number    |                                                              |
| sms                      | Gofime SMS service report                                    | Number    |                                                              |




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
curl --location --request GET 'https://api.gofime.vn:5000/v1/user' \
--header 'Authorization: Bearer <b>your-api-key</b>'
</pre>

------
<br />

#### 2. `PATCH` /v1/user

**:star: <ins>Description:</ins>** Modify user information partially.

**:star: <ins>Request parameters:</ins>**

| Parameter name |  Data Type  |            Position             | Property |
| :------------: | :---------: | :-----------------------------: | -------- |
|    API Key     |   String    | HTTP Authorization Basic Header | Required |
|      body      | JSON object |              Body               | Required |

`body` with parameter content type: application/json

| Body parameter name | Description                                         | Data Type | Valid value                                                  | Property                                       |
| ------------------- | --------------------------------------------------- | --------- | ------------------------------------------------------------ | ---------------------------------------------- |
| name                | Name that user registered to service                | String UTF-8    |                                                              | Optional                                       |
| phone               | Phone that user registered to service               | String    |                                                              | Optional                                       |



```
{
	"info":{
		"name": "user_name",
		"phone": "user_phone"
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
curl --location --request PATCH 'https://api.gofime.vn:5000/v1/user' \
--header 'Authorization: Bearer <b>your-api-key</b>' \
--header 'Content-Type: application/json' \
--data-raw '{
	"info":{
		"name": "<b>your-name</b>",
		"phone": "<b>your-phone</b>"
	}
}'
</pre>


------
<br />

#### 3. `POST` `PUT` `DELETE` /v1/user

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
