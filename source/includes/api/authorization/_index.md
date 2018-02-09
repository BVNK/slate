# Authorization

## Create Authorization

```shell
curl -X POST \
  https://demo.bvnk.co/auth/account \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: d9cec22a-f367-31ed-99bb-a725767cc5db' \
  -F UserIdentificationNumber=300000-0000-001 \
  -F Password=test1234
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

    url := "https://demo.bvnk.co/auth/account"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserIdentificationNumber\"\r\n\r\n300000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "260911ea-cd1a-41a0-048e-c17a4187347e")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/auth/account")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("cache-control", "no-cache")
  .header("postman-token", "757e3e20-ccd4-3a49-6ff1-5f3f645c5e55")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserIdentificationNumber\"\r\n\r\n300000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/auth/account',
  headers: 
   { 'postman-token': 'db7c8e74-30e5-980a-7034-19a904ea5122',
     'cache-control': 'no-cache',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { UserIdentificationNumber: '300000-0000-001',
     Password: 'test1234' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/auth/account"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserIdentificationNumber\"\r\n\r\n300000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'cache-control': "no-cache",
    'postman-token': "a336b6fb-f79a-fc4f-7b47-9cb876c9f52a"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> A successfull response looks like:

```json
{
    "response": "3069ecbc-bf37-421d-a66f-6b78d56fd86f"
}
```

> An unsuccessful response looks like:

```json
{
    "error": "Password must be at least 8 characters"
}
```

This endpoint creates an authorization user for the account user. A `uuid` is returned which will be the identifier for the user in subsequent auth requests. This is to avoid 
sending through the `AccountHolderIdentificationNumber` on all auth requests.

If an authorization user has already been created for the account user, the saved `uuid` will be returned.

### HTTP Request

`POST https://demo.bvnk.co/auth/account`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
UserIdentificationNumber | true | The matching value from the account user creation.
Password | true | The password set during account user creation. Minimum of 8 characters long.

## Log In

```shell
curl -X POST \
  https://demo.bvnk.co/auth/login \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 0d828327-c0f7-f4b4-2af5-45139ff6ec6f' \
  -F User=3069ecbc-bf37-421d-a66f-6b78d56fd86f \
  -F Password=test1234
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

    url := "https://demo.bvnk.co/auth/login"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"User\"\r\n\r\n3069ecbc-bf37-421d-a66f-6b78d56fd86f\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "3c009e3a-f538-ba4b-759a-f858b0ab7a20")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/auth/login")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("cache-control", "no-cache")
  .header("postman-token", "3015717e-61ed-b1a7-879a-a12ffc3b07ae")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"User\"\r\n\r\n3069ecbc-bf37-421d-a66f-6b78d56fd86f\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/auth/login',
  headers: 
   { 'postman-token': '333d7125-a982-ce12-a9e2-c995d4e38a6f',
     'cache-control': 'no-cache',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { User: '3069ecbc-bf37-421d-a66f-6b78d56fd86f',
     Password: 'test1234' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/auth/login"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"User\"\r\n\r\n3069ecbc-bf37-421d-a66f-6b78d56fd86f\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Password\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'cache-control': "no-cache",
    'postman-token': "7c2703b3-7bcb-5e94-59e6-971e36aede7d"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "6836d1f3-2321-45eb-9173-efeaa211a6d5"
}
```

> Error response:

```json
{
    "error": "Authentication credentials invalid"
}
```

This endpoint authorizes a user and returns an `auth token` to use in requests which require user level authorization. The `User` value is the `uuid` value received from the [create authorization](#create-authorization) step.

### HTTP Request

`POST https://demo.bvnk.co/auth/login<ID>`

### URL Parameters

Parameter | Required | Description
--------- | ---------- | -----------
User | true | The UUID value from create authorization
Password | true | The password set during user account creation

## Extend Auth Token

```shell
curl -X POST \
  https://demo.bvnk.co/auth \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 0e618af3-40b3-e570-d241-676f7be72f32' \
  -H 'x-auth-token: a0447b38-31ae-428a-ae19-76e6258b6371'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/auth"

    req, _ := http.NewRequest("POST", url, nil)

    req.Header.Add("x-auth-token", "a0447b38-31ae-428a-ae19-76e6258b6371")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "65b5984d-1673-8815-d7a8-3d9d0e2c0e22")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/auth")
  .header("x-auth-token", "a0447b38-31ae-428a-ae19-76e6258b6371")
  .header("cache-control", "no-cache")
  .header("postman-token", "613b45e3-9dce-8faf-5b5b-6ec9a7b2c709")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/auth',
  headers: 
   { 'postman-token': '0eb3f65f-36d9-b55b-b559-458d8e41d648',
     'cache-control': 'no-cache',
     'x-auth-token': 'a0447b38-31ae-428a-ae19-76e6258b6371' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/auth"

headers = {
    'x-auth-token': "a0447b38-31ae-428a-ae19-76e6258b6371",
    'cache-control': "no-cache",
    'postman-token': "5b0b842a-7000-d0dc-8505-cdf6cd50bf88"
    }

response = requests.request("POST", url, headers=headers)

print(response.text)
```

> Successfull response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Token invalid"
}
```

This endpoint extends a token. Default TTL is 60 minutes.

### HTTP Request

`POST https://demo.bvnk.co/auth`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

There are no parameters for this request, only the `X-Auth-Token` header is required.
