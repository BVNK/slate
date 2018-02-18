# Notifications

## Get All

```shell
curl -X GET \
  https://demo.bvnk.co/notifications/all/0/10/ \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 242f94e9-d28d-3fa9-2541-2274c3edc4a9' \
  -H 'X-Auth-Token: 54c026c8-e38e-4119-898b-11134d1c7809'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/notifications/all/0/10/"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "619e8800-ceb5-b7e5-a1b3-a5c122deb62f")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/notifications/all/0/10/',
  headers:
   { 'Postman-Token': '2d2020f2-b7e8-1899-a907-cf42763d7a53',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': '54c026c8-e38e-4119-898b-11134d1c7809' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/notifications/all/0/10/"

headers = {
    'X-Auth-Token': "54c026c8-e38e-4119-898b-11134d1c7809",
    'Cache-Control': "no-cache",
    'Postman-Token': "b845b0a8-fb3a-402a-351a-b9e5c6e882dc"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/notifications/all/0/10/")
  .header("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "536eb88a-2e5d-d624-9ab9-cc1719113f60")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "ID": 1,
            "UserID": "190001010000112",
            "Type": "transactions",
            "Message": "You have received a payment of 100 ZAR.",
            "Status": "unread",
            "Timestamp": "2018-02-17 15:35:36"
        },
        {
            "ID": 2,
            "UserID": "190001010000112",
            "Type": "transactions",
            "Message": "Deposit received!",
            "Status": "read",
            "Timestamp": "2018-02-17 15:35:21"
        },
        ...
    ]
}
```

> Error response:

```json
{
    "error": "Could not get notifications"
}
```

This endpoint returns a list of all notifications for the current user.

### HTTP Request

`GET https://demo.bvnk.co/notifications/all/{perPage}/{pageNum}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PerPage | true | The number of records to receive per request. This cannot exceed 100.
PageNum | true | The page number for records to receive. To receive the first page, set this value to 0.

## Get All By Status

```shell
curl -X GET \
  https://demo.bvnk.co/notifications/all/2/1/read \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 41b03043-5218-ea0a-ed55-5c451d769846' \
  -H 'X-Auth-Token: 54c026c8-e38e-4119-898b-11134d1c7809'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/notifications/all/2/1/read"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "29f910bb-1050-3cf7-4bab-295fae273d17")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/notifications/all/2/1/read',
  headers:
   { 'Postman-Token': '32f719c7-52f7-c258-650c-822c36322222',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': '54c026c8-e38e-4119-898b-11134d1c7809' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/notifications/all/2/1/read"

headers = {
    'X-Auth-Token': "54c026c8-e38e-4119-898b-11134d1c7809",
    'Cache-Control': "no-cache",
    'Postman-Token': "2dd7087a-0754-9805-5b59-4e61f308bf30"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/notifications/all/2/1/read")
  .header("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "9970cc8a-17ee-4e1b-435f-d7975d7bbee2")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "ID": 3,
            "UserID": "190001010000112",
            "Type": "transactions",
            "Message": "Deposit received!",
            "Status": "read",
            "Timestamp": "2018-02-17 15:36:42"
        },
        {
            "ID": 5,
            "UserID": "190001010000112",
            "Type": "transactions",
            "Message": "Payment sent!",
            "Status": "read",
            "Timestamp": "2018-02-17 15:36:42"
        }
    ]
}
```

> Error response:

```json
{
    "error": "Could not get notifications"
}
```

This endpoint returns a list of all notifications for the current user by notification status. Notification status can be "read" or "unread".

### HTTP Request

`GET https://demo.bvnk.co/notifications/all/{perPage}/{pageNum}/{status}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PerPage | true | The number of records to receive per request. This cannot exceed 100.
PageNum | true | The page number for records to receive. To receive the first page, set this value to 0.
Status | true | The notification status to retrieve. This must be either "read" or "unread".

## Get Single

```shell
curl -X GET \
  https://demo.bvnk.co/notifications/2 \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 5bcde913-0a3b-23a4-004c-12fc2649fda5' \
  -H 'X-Auth-Token: 54c026c8-e38e-4119-898b-11134d1c7809'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/notifications/2"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "b399898e-6cdb-b252-70e7-33a6682b2374")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/notifications/2',
  headers:
   { 'Postman-Token': '5755c499-88fd-bc90-4a8e-687dbe4af39d',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': '54c026c8-e38e-4119-898b-11134d1c7809' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/notifications/2"

headers = {
    'X-Auth-Token': "54c026c8-e38e-4119-898b-11134d1c7809",
    'Cache-Control': "no-cache",
    'Postman-Token': "d523e160-fb74-358b-e9e5-400ae9da1fff"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/notifications/2")
  .header("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "e1726a3d-3cbd-0657-a0b4-e3cd1fce4551")
  .asString();
```

> Successful response:

```json
{
    "response": {
        "ID": 2,
        "UserID": "190001010000112",
        "Type": "transactions",
        "Message": "Deposit received!",
        "Status": "read",
        "Timestamp": "2018-02-17 15:35:21"
    }
}
```

> Error response:

```json
{
    "error": "Could not get notification"
}
```

This endpoint returns a single notification by notification ID.

### HTTP Request

`GET https://demo.bvnk.co/notifications/{notificationID}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
NotificationID | true | The ID of the notification to retrieve. This ID must map to the ID received in `GET /notifications`.

## Update Status All

```shell
curl -X PUT \
  https://demo.bvnk.co/notifications/all \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 7048647a-e951-b96a-74e8-487cc4fc33e1' \
  -H 'X-Auth-Token: 54c026c8-e38e-4119-898b-11134d1c7809' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F Status=read
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/notifications/all"

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("PUT", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
	req.Header.Add("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "b6fddc5d-0ed4-a201-40d0-d61d7ae79a9c")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://demo.bvnk.co/notifications/all',
  headers:
   { 'Postman-Token': '65878abd-34a5-0c50-096c-b34d8ae70be5',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': '54c026c8-e38e-4119-898b-11134d1c7809',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { Status: 'read' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/notifications/all"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'X-Auth-Token': "54c026c8-e38e-4119-898b-11134d1c7809",
    'Cache-Control': "no-cache",
    'Postman-Token': "7ecd59a6-1e22-438c-988b-1de7b0d75af7"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.put("https://demo.bvnk.co/notifications/all")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "b4ba883f-f711-5fe3-ea50-e608767c6f11")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

> Successful response:

```json
{
    "response": "Successfully marked all notifications as read"
}
```

> Error response:

```json
{
    "error": "Could not update notifications status"
}
```

This endpoint updates all notifications status. Status must be either "read" or "unread".

### HTTP Request

`PUT https://demo.bvnk.co/notifications/all`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
Status | true | The notification status to update notifications to. This must be either "read" or "unread".

## Update Status Single

```shell
curl -X PUT \
  https://demo.bvnk.co/notifications/2 \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 6bf8b434-6613-1288-bc99-208f2651d8dd' \
  -H 'X-Auth-Token: 54c026c8-e38e-4119-898b-11134d1c7809' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F Status=unread
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/notifications/2"

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nunread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("PUT", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
	req.Header.Add("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "e4326eab-fd5e-f91c-9dec-20cffc366c9b")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://demo.bvnk.co/notifications/2',
  headers:
   { 'Postman-Token': '2c5f27e5-5774-aa79-ab53-5d0072d56f69',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': '54c026c8-e38e-4119-898b-11134d1c7809',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { Status: 'unread' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/notifications/2"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nunread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'X-Auth-Token': "54c026c8-e38e-4119-898b-11134d1c7809",
    'Cache-Control': "no-cache",
    'Postman-Token': "490bf872-80e0-1220-9486-0709ff7d7a98"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.put("https://demo.bvnk.co/notifications/2")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("X-Auth-Token", "54c026c8-e38e-4119-898b-11134d1c7809")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "e20d6c0e-0ed0-72fd-7bde-c89f0fd46023")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Status\"\r\n\r\nunread\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

> Successful response:

```json
{
    "response": "Successfully marked notification 2 as read"
}
```

> Error response:

```json
{
    "error": "Could not update notification status"
}
```

This endpoint updates the status of a given notification by notification ID.

### HTTP Request

`PUT https://demo.bvnk.co/notifications/{notificationID}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
NotificationID | true | The ID of the notification to retrieve. This ID must map to the ID received in `GET /notifications`.
Status | true | The notification status to update notification to. This must be either "read" or "unread".
