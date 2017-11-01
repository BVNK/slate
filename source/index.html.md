---
title: BVNK API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - go
  - java
  - javascript
  - python

toc_footers:
  - <a href='https://bvnk.co/contact' target='_blank'>Contact</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

> All calls result in either success `200` or failure `400`. On success, the response follows the following structure:

```json
{
    "response": ""
}
```

> On failure, the response follows the following structure:


```json
{
    "error": ""
}
```

Welcome to the BVNK API. We believe banking should be a concentration of elegant and effective functions rather than the complex, bloated and expensive system it is today.

Our API driven banking infrastructure can allow anyone to create new products, or to expand on their existing offering. We enable innovation through providing a platform.

Find out more about [BVNK on our website](https://bvnk.co).

# Defaults

System wide defaults are followed for consistency. 

In the case of the demo installation, no API key is required. For all custom deploys or the production deploy, API keys will be issued for developers to test against.
These API keys will need to be included on each and every request to the API using the header value `X-Api-Key` and `X-Api-Secret`.

## Basic Auth

Some requests are limited to admins of the installation. In these cases, the routes are secured through Basic Auth. Usernames and passwords will be issued to developers 
on request, and for private installations given to the relevant parties.

# User creation

> To create a new user:

```shell
curl -X POST \
  https://demo.bvnk.co/account/user \
  -F AccountHolderGivenName=Alice \
  -F AccountHolderFamilyName=Bankai \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=400000-0000-001 \
  -F AccountHolderContactNumber1=(558) 555-4234 \
  -F AccountHolderEmailAddress=alice@bankai.co \
  -F AccountHolderAddressLine1=Address 1 \
  -F AccountHolderAddressLine2=Address 2 \
  -F AccountHolderAddressLine3=Address 3 \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderPassword=test1234
```

```python
import http.client

conn = http.client.HTTPSConnection("demo.bvnk.co")

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nAlice\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nBankai\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-4234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'cache-control': "no-cache",
    'postman-token': "cfc5252b-b90b-60d3-a130-cc288ad268a1"
    }

conn.request("POST", "/account/user", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
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

    url := "https://demo.bvnk.co/account/user"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nAlice\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nBankai\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-4234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "fd5be903-4225-7c8a-cc31-71491f272bda")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/user")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("cache-control", "no-cache")
  .header("postman-token", "4941d91a-a549-c1a1-e4df-af5e531b8e7a")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nAlice\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nBankai\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-4234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\ntest1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account/user',
  headers: 
   { 'postman-token': 'c1e3f050-1d56-746d-4334-0c268f0c5c8b',
     'cache-control': 'no-cache',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { AccountHolderGivenName: 'Alice',
     AccountHolderFamilyName: 'Bankai',
     AccountHolderDateOfBirth: '1900-01-01',
     AccountHolderIdentificationNumber: '400000-0000-001',
     AccountHolderContactNumber1: '(558) 555-4234',
     AccountHolderEmailAddress: 'alice@bankai.co',
     AccountHolderAddressLine1: 'Address 1',
     AccountHolderAddressLine2: 'Address 2',
     AccountHolderAddressLine3: 'Address 3',
     AccountHolderPostalCode: '1234',
     AccountHolderPassword: 'test1234' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

Users act as account holders and need to be created as the first action. All accounts need to be linked to users, and Know Your Customer requirements centre around users. 

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Contact number already linked to another user"
}
```

### HTTP Request

`POST https://demo.bvnk.co/account/user`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
AccountHolderGivenName | true | Given or first name of account holder
AccountHolderFamilyName | true | Family name of account holder
AccountHolderDateOfBirth | true | Date of birth of account holder in the format dd-mm-yyyy
AccountHolderIdentificationNumber | true | Identification or passport number of account holder
AccountHolderContactNumber1 | true | Primary contact number for account holder
AccountHolderContactNumber2 | false | Secondary contact number for account holder
AccountHolderEmailAddress | true | Email address for account holder
AccountHolderAddressLine1 | true | First line of address for account holder
AccountHolderAddressLine2 | false | Second line of address for account holder
AccountHolderAddressLine3 | false | Third line of address for account holder
AccountHolderPostalCode | true | Postal code of address for account holder
AccountHolderPassword | true | Password for the users account

<aside class="notice">
The password sent through on this call will used along with the <code>AccountHolderIdentificationNumber</code> to generate authentication credentials.
</aside>

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

# Accounts

## Create Account

```shell
curl -X POST \
  https://demo.bvnk.co/account \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: df8385bd-a7af-0644-2a54-02253d811573' \
  -H 'x-auth-token: a0447b38-31ae-428a-ae19-76e6258b6371' \
  -F AccountType=cheque
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

    url := "https://demo.bvnk.co/account"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "a0447b38-31ae-428a-ae19-76e6258b6371")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "59a42cb7-279e-8e5d-53fb-51bc0c1fe356")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "a0447b38-31ae-428a-ae19-76e6258b6371")
  .header("cache-control", "no-cache")
  .header("postman-token", "88117413-a397-0583-627b-98678011b533")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account',
  headers: 
   { 'postman-token': 'b4abae43-21d1-67c5-b928-028dbdcacdb8',
     'cache-control': 'no-cache',
     'x-auth-token': 'a0447b38-31ae-428a-ae19-76e6258b6371',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { AccountType: 'cheque' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "a0447b38-31ae-428a-ae19-76e6258b6371",
    'cache-control': "no-cache",
    'postman-token': "44742542-d68e-2d3c-b2cf-5cdab22fd557"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "9e7d08ef-5377-4ebc-a606-186dbe07020e"
}
```

> Error response:

```json
{
    "error": "Account type not valid, must be one of savings, cheque, merchant, money-market, cd, ira, rcp, credit, mortgage, loan"
}
```

This endpoint is used to create an account against an existing user. As the user has already been registered, only the account type is required for this call.

### HTTP Request

`POST https://demo.bvnk.co/account`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountType | false | Account type, one of savings, cheque, merchant, money-market, cd, ira, rcp, credit, mortgage, loan. Default cheque.

## Get All Account By ID

```shell
curl -X GET \
  https://demo.bvnk.co/account/000000-0000-001 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 97cb1918-d4c2-51d9-c105-edd0e1b81a4c' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/account/000000-0000-001"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "a215a2c3-85af-2c09-7626-a64fe9f224cb")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/000000-0000-001")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "616dbcd8-cd43-2774-d3ed-96c7d8cfa2e7")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/000000-0000-001',
  headers: 
   { 'postman-token': 'ef32670c-55a6-21ca-e2be-2ff8cd27b022',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/000000-0000-001"

headers = {
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "24facbd1-9605-75ee-ca4b-510230bc3292"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        "50d60fcb-e579-4432-bf36-d0167e381376",
        "c1b338ce-8869-4615-bb33-10efc7c338e5",
        "a913711e-9477-4cdf-a5aa-e312a710e9be",
		...
	]
}
```

> Error response:

```json
{
    "error": "Account not found"
}
```

This endpoint returns a JSON array of all account numbers linked to a given user through their identification number. 

### HTTP Request

`GET https://demo.bvnk.co/account/{ID number}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

This request requires no parameters.

## Get Account Holder

```shell
curl -X GET \
  https://demo.bvnk.co/accountHolder/ \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 72a0650b-4fe2-9932-f26f-a2f092f9fec0' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/accountHolder/"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "0c190ce9-506b-4607-b898-ec96edd58b34")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/accountHolder/")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "206807d9-28cc-a40a-5f30-3e96f8425052")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/accountHolder/',
  headers: 
   { 'postman-token': '36ab9a2e-dcd5-b83f-c890-f1e78695e9fe',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/accountHolder/"

headers = {
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "38ae7044-a0c3-8bd1-5557-77b3e2ca7a40"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "GivenName": "Alice",
        "FamilyName": "Bankai",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "300000-0000-001",
        "ContactNumber1": "558555-1234",
        "ContactNumber2": "",
        "EmailAddress": "alice@bankai.co",
        "AddressLine1": "Address 1",
        "AddressLine2": "Address 2",
        "AddressLine3": "Address 3",
        "PostalCode": "1234"
    }
}
```

> Error response:

```json
{
    "error": "Could not retrieve account details"
}
```

This endpoint returns the details of the current user.

### HTTP Request

`GET https://demo.bvnk.co/accountHolder/`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

This request requires no parameters.

## Get All Accounts

```shell
curl -X GET \
  https://demo.bvnk.co/account \
  -H 'cache-control: no-cache' \
  -H 'postman-token: fee216a0-ab05-9344-b688-2354c0f615df' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/account"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "76cfe032-6c2c-faa4-3ade-d19efdf0095f")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "f684bff8-3acd-ce9c-5f51-e511b89651e1")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account',
  headers: 
   { 'postman-token': '9a020860-4e1d-f5cb-696e-e70e21827fde',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account"

headers = {
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "7a622071-b9b9-2bce-45a0-a894a0c2c59f"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "Bankai,Alice",
            "AccountBalance": "3507.61865234375",
            "Overdraft": "0",
            "AvailableBalance": "3507.61865234375",
            "Type": "",
            "Timestamp": 0
        },
        {
            "AccountNumber": "c04b7d77-d736-4bf4-952e-b3c35b073179",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "Test Merchant Ltd",
            "AccountBalance": "0",
            "Overdraft": "0",
            "AvailableBalance": "0",
            "Type": "",
            "Timestamp": 0
        },
		...
	]
}
```

> Error response:

```json
{
    "error": "Could not retrieve account listing"
}
```

### HTTP Request

`GET https://demo.bvnk.co/account/`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

This request requires no parameters.

## Get Account By Account Number

```shell
curl -X GET \
  https://demo.bvnk.co/accountByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: b192e455-192d-c66a-360a-24ce519a3a45' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/accountByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "3897be5a-22e9-beb8-181d-0a6c2c74b0ef")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/accountByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "55419403-25d1-6214-1c4a-42f2bb4870c9")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/accountByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726',
  headers: 
   { 'postman-token': '4796f3fc-1afc-7ef1-4ee6-a1442ab38181',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/accountByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726"

headers = {
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "245cbc92-278c-9ee3-3df9-4f4e47a23a99"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
        "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
        "AccountHolderName": "Bankai,Alice",
        "AccountBalance": "0",
        "Overdraft": "0",
        "AvailableBalance": "0",
        "Type": "cheque",
        "Timestamp": 0
    }
}
```

> Error response:

```json
{
    "error": "User not authorized on this account"
}
```

This endpoint returns account information for a single account. This information is non-public as it includes balance details, and only the account holder may query their own account.

### HTTP Request

`GET https://demo.bvnk.co/account/{account number}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountNumber | true | The account number to get information against. This must be an account number linked to the user.

## Get Account Holder By Account Number

```shell
curl -X GET \
  https://demo.bvnk.co/accountHolderByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: cf4dfd83-6ce1-26ce-90b8-f20763ea14a0' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/accountHolderByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "8090499a-a980-2fea-a5cb-f915c3980311")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/accountHolderByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "781e4fc1-c1ca-7a03-4b2a-ecdfbfe78ff6")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/accountHolderByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726',
  headers: 
   { 'postman-token': '750e54d1-8180-f07b-e122-d630eb65a3e2',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/accountHolderByNumber/e0e712e4-b5e2-4b03-a401-1c828e0f2726"

headers = {
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "b52f4a80-3b52-cfef-6ce5-2e0bac123157"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
        "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
        "AccountHolderName": "Bankai,Alice",
        "AccountBalance": "0",
        "Overdraft": "0",
        "AvailableBalance": "0",
        "Type": "cheque",
        "Timestamp": 0
    }
}
```

> Error response:

```json
{
    "error": "Account not found"
}
```

This endpoint returns account details for a given account number with sensitive details removed. Use case: you receive a payment from an unknown source, you use this route to see who the sender is. This route is public, anyone can query for anyone's account number here.

### HTTP Request

`GET https://demo.bvnk.co/accountHolderByNumber/{account number}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountNumber | true | The account number to get information against. This does not have to be an account number linked to the user.

## Add Push Token To User

```shell
curl -X POST \
  https://demo.bvnk.co/accountPushToken \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: f100c048-f95f-9e70-18da-2eb7b84ba993' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939' \
  -F PushToken=test-push-token \
  -F Platform=ios
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

    url := "https://demo.bvnk.co/accountPushToken"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "e5d7def4-4690-9578-da6f-48e1f5e1666e")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/accountPushToken")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "09ec05ba-d60a-2a59-06b8-3c4a4f6867b5")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/accountPushToken',
  headers: 
   { 'postman-token': '6f2eed35-da87-c40d-d7f4-8ac5b482280d',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { PushToken: 'test-push-token', Platform: 'ios' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/accountPushToken"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "f38f63ff-0cab-01f4-91ab-113057e1a79f"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Platform invalid"
}
```

This endpoint adds a push token to an account. This token will be used to send push notifications for any activity on any account the user has. Currently supported platforms are iOS, Android, Windows and BlackBerry.

<aside class="notice">
On custom deploys or where another mobile application is being used, please <a href="https://bvnk.co/contact" target="_blank">contact us</a> to configure the push notification service.
</aside>

### HTTP Request

`POST https://demo.bvnk.co/accountPushToken`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PushToken | true | The push token for the device
Platform | true | The device type, e.g. ios, android, windows, blackberry, other

## Remove Push Token From User

```shell
curl -X DELETE \
  https://demo.bvnk.co/accountPushToken \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: b26ee081-ddf8-b422-9975-98bc089d1948' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939' \
  -F PushToken=test-push-token \
  -F Platform=ios
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

    url := "https://demo.bvnk.co/accountPushToken"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("DELETE", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "53593915-4b03-4acb-8bf0-c0581dcc36b8")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.delete("https://demo.bvnk.co/accountPushToken")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "c47c614e-dae0-adb4-55e6-c2409a0e4190")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'DELETE',
  url: 'https://demo.bvnk.co/accountPushToken',
  headers: 
   { 'postman-token': '50171080-85e7-566e-52e1-7395c5647e62',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { PushToken: 'test-push-token', Platform: 'ios' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/accountPushToken"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"PushToken\"\r\n\r\ntest-push-token\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Platform\"\r\n\r\nios\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "d611505a-b26d-f5dc-ad7e-e853c58b1b0a"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Platform invalid"
}
```

This endpoint removes a push token from a user account.

### HTTP Request

`DEL https://demo.bvnk.co/accountPushToken`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PushToken | true | The push token for the device
Platform | true | The device type, e.g. ios, android, windows, blackberry, other

## Search For An Account

```shell
curl -X POST \
  https://demo.bvnk.co/account/search \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 5ab072e8-1c95-ac5a-2523-d57f9e5e6ea8' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939' \
  -F Search=000000-0000-009
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

    url := "https://demo.bvnk.co/account/search"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\n000000-0000-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "3ca9067f-0a8e-661a-704a-b25194d410d8")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/search")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "2e9143e7-4bf6-3da2-0dc1-8529666d7443")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\n000000-0000-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account/search',
  headers: 
   { 'postman-token': '4c98b2ed-b1f3-7505-e1fb-58197ad5405f',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { Search: '000000-0000-009' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/search"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\n000000-0000-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "15ba3ed6-941a-5e31-de7f-a237659d5e44"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "GivenName": "Test",
            "FamilyName": "User1",
            "Accounts": [
                {
                    "AccountNumber": "c4bf0336-64f9-4ada-a683-ee1c78ec75af",
                    "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                    "Type": "savings"
                }
            ]
        }
    ]
}
```

> Error response:

```json
{
    "error": "Please provide a search term of at least 4 characters."
}
```

This endpoint performs a fuzzy match search for accounts on ID number, given name and family name, and an exact match search on email address. 

### HTTP Request

`POST https://demo.bvnk.co/account/search`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
Search | true | Term to search for. Must be at least 4 characters in length.

# Transactions

## Credit Transfer

```shell
curl -X POST \
  https://demo.bvnk.co/transaction/credit \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: f7befd14-cd7b-52be-b7f4-f500fde4c55e' \
  -H 'x-auth-token: 870b08c5-b45b-4e7b-95ac-779cad191939' \
  -F SenderDetails=e0e712e4-b5e2-4b03-a401-1c828e0f2726@ \
  -F RecipientDetails=9bd356cd-1c54-498d-b6b5-26a8d0a17940@ \
  -F Amount=20 \
  -F Lat=11.0 \
  -F Lon=12.0 \
  -F 'Desc=Test desc'
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

    url := "https://demo.bvnk.co/transaction/credit"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "775c69ac-4a95-7ec6-69a6-f5be3a2651b7")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/credit")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "870b08c5-b45b-4e7b-95ac-779cad191939")
  .header("cache-control", "no-cache")
  .header("postman-token", "d19e7517-64fc-4ed4-796c-02138a67b5e9")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/transaction/credit',
  headers: 
   { 'postman-token': 'f1f35f94-3486-2c89-2adb-3d4b1f2458a8',
     'cache-control': 'no-cache',
     'x-auth-token': '870b08c5-b45b-4e7b-95ac-779cad191939',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { SenderDetails: 'e0e712e4-b5e2-4b03-a401-1c828e0f2726@',
     RecipientDetails: '9bd356cd-1c54-498d-b6b5-26a8d0a17940@',
     Amount: '20',
     Lat: '11.0',
     Lon: '12.0',
     Desc: 'Test desc' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/credit"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "870b08c5-b45b-4e7b-95ac-779cad191939",
    'cache-control': "no-cache",
    'postman-token': "b96a191b-7635-6214-fd92-0f63875a8ee5"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "490923"
}
```

> Error response:

```json
{
    "error": "Insufficient funds available"
}
```

This endpoint does a credit transfer from one account to another. Both accounts must exist on the system, and the sender account must be an account that is yours.

### HTTP Request

`POST https://demo.bvnk.co/transaction/credit`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
SenderDetails | true | The sender account details. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance. This must be your account
RecipientDetails | true | The recipient account details. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance
Amount | true | Amount to transfer
Lat | false | Latitude of transaction
Lon | false | Longitude of transaction
Desc | false | Description of transaction, emojis welcome 🎉💵⚡️

## Deposit

```shell
curl -X POST \
  https://demo.bvnk.co/transaction/deposit \
  -H 'authorization: Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 0ccd12db-6487-a26d-e8ac-95ce566789da' \
  -F AccountDetails=e0e712e4-b5e2-4b03-a401-1c828e0f2726@ \
  -F Amount=120 \
  -F Lat=10. \
  -F Lon=10. \
  -F 'Desc=🍊'
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

    url := "https://demo.bvnk.co/transaction/deposit"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n120\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "d4b50549-9f26-1d5b-b59e-39f8f96dfa2b")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/deposit")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
  .header("cache-control", "no-cache")
  .header("postman-token", "5e83779e-fab9-f5b9-6441-e0f0ac7706bd")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n120\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/transaction/deposit',
  headers: 
   { 'postman-token': '319b6653-5828-03eb-7405-6ca22a36eda4',
     'cache-control': 'no-cache',
     authorization: 'Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { AccountDetails: 'e0e712e4-b5e2-4b03-a401-1c828e0f2726@',
     Amount: '120',
     Lat: '10.',
     Lon: '10.',
     Desc: '🍊' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/deposit"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n120\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'authorization': "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV",
    'cache-control': "no-cache",
    'postman-token': "15afb644-a65f-cf85-7d2a-ff9fd15e52ad"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successfull response:

```json
{
    "response": "490922"
}
```

> Error response:

```json
{
    "error": "Basic Auth incorrect. Access denied."
}
```

This endpoint initiates a deposit against an account. Basic Auth is required for this route, as it is an admin route. Any account can be loaded with any amount. Please see [basic auth](#basic-auth) section for more.

The response is the `id` number of the transaction.

### HTTP Request

`POST https://demo.bvnk.co/transaction/deposit`

### Headers

`Authorization: Basic {basic auth}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountDetails | true | Account to be loaded. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance
Amount | true | Amount to be loaded
Lat | false | Latitude of transaction
Lon | false | Longitude of transaction
Desc | false | Description of transaction

## Withdrawal

```shell
curl -X POST \
  https://demo.bvnk.co/transaction/withdrawal \
  -H 'authorization: Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 438c0de4-54f6-d0ff-dc08-b83450021391' \
  -F AccountDetails=e0e712e4-b5e2-4b03-a401-1c828e0f2726@ \
  -F Amount=8 \
  -F Lat=10. \
  -F Lon=10. \
  -F 'Desc=🍊'
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

    url := "https://demo.bvnk.co/transaction/withdrawal"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n8\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "b4b7b006-71de-91d5-3479-bb407a73bf43")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/withdrawal")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
  .header("cache-control", "no-cache")
  .header("postman-token", "e8fd4718-79e5-3aa0-398d-90009d7f6d6d")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n8\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/transaction/withdrawal',
  headers: 
   { 'postman-token': '4814f39e-8beb-e819-93b2-739c5f62be26',
     'cache-control': 'no-cache',
     authorization: 'Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { AccountDetails: 'e0e712e4-b5e2-4b03-a401-1c828e0f2726@',
     Amount: '8',
     Lat: '10.',
     Lon: '10.',
     Desc: '🍊' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/withdrawal"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountDetails\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n8\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n10.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\n🍊\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'authorization': "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV",
    'cache-control': "no-cache",
    'postman-token': "622432f1-6906-6e6f-1d41-f5cafd5c09d7"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successfull response: 

```json
{
    "response": "490925"
}
```

> Error response:

```json
{
    "error": "Amount must be present"
}
```

This endpoint initiates a withdrawal against an account. Basic Auth is required for this route, as it is an admin route. Any account can be unloaded with any amount up to the available balance in the account. Please see [basic auth](#basic-auth) section for more.

The response is the `id` number of the transaction.

### HTTP Request

`POST https://demo.bvnk.co/transaction/withdrawal`

### Headers

`Authorization: Basic {basic auth}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountDetails | true | Account to be unloaded. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance
Amount | true | Amount to be unloaded
Lat | false | Latitude of transaction
Lon | false | Longitude of transaction
Desc | false | Description of transaction

## Transaction Listing

```shell
curl -X GET \
  https://demo.bvnk.co/transaction/list/10/0 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: e179488a-ef39-4c04-724d-55697acb79f7' \
  -H 'x-auth-accountnumber: e0e712e4-b5e2-4b03-a401-1c828e0f2726' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/transaction/list/10/0"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("x-auth-accountnumber", "e0e712e4-b5e2-4b03-a401-1c828e0f2726")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "31287002-0a01-6dd6-2ad3-a2b6ebf4639c")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/transaction/list/10/0")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("x-auth-accountnumber", "e0e712e4-b5e2-4b03-a401-1c828e0f2726")
  .header("cache-control", "no-cache")
  .header("postman-token", "447d54e2-f8cf-be47-b872-b13512dbe67e")
  .asString();
```

```python
import requests

url = "https://demo.bvnk.co/transaction/list/10/0"

headers = {
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'x-auth-accountnumber': "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
    'cache-control': "no-cache",
    'postman-token': "344bc0c3-18a9-0bcb-106a-14c392c4ddaf"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "ID": 490925,
            "PainType": 1002,
            "Sender": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Receiver": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Amount": "-8",
            "Fee": "0.0007999999797903001",
            "Geo": [
                10,
                10
            ],
            "Desc": "????",
            "Status": "approved",
            "Timestamp": 1505652044
        },
        {
            "ID": 490924,
            "PainType": 1000,
            "Sender": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "120",
            "Fee": "0.012000000104308128",
            "Geo": [
                10,
                10
            ],
            "Desc": "",
            "Status": "approved",
            "Timestamp": 1505651801
        },
        {
            "ID": 490923,
            "PainType": 1,
            "Sender": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Receiver": {
                "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "-20",
            "Fee": "0.0020000000949949026",
            "Geo": [
                11,
                12
            ],
            "Desc": "Test desc",
            "Status": "approved",
            "Timestamp": 1505650285
        },
        {
            "ID": 490922,
            "PainType": 1000,
            "Sender": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "120",
            "Fee": "0.012000000104308128",
            "Geo": [
                10,
                10
            ],
            "Desc": "????",
            "Status": "approved",
            "Timestamp": 1505650282
        }
    ]
}
```

> Error response:

```json
{
    "error": "Cannot retrieve more than 100 results per request"
}
```

This endpoint retrieves a given number of transactions against an account in a paginated manner. The account is determined through the additional header `X-Auth-AccountNumber`. This must be an account you own.

### HTTP Request

`GET https://demo.bvnk.co/transaction/list/{perPage}/{pageNum}`

### Headers

`X-Auth-Token: {auth token}`
`X-Auth-AccountNumber: {account number}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PerPage | true | The number of records to receive per request. This cannot exceed 100.
PageNum | true | The page number for records to receive. To receive the first page, set this value to 0.

## Transaction Listing After Timestamp

```shell
curl -X GET \
  https://demo.bvnk.co/transaction/list/10/0/1491139308 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 08fc8393-0e96-6492-a812-06371937e759' \
  -H 'x-auth-accountnumber: e0e712e4-b5e2-4b03-a401-1c828e0f2726' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/transaction/list/10/0/1491139308"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("x-auth-accountnumber", "e0e712e4-b5e2-4b03-a401-1c828e0f2726")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "b00e27c6-7f6d-44db-3d4d-239aef796b02")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/transaction/list/10/0/1491139308")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("x-auth-accountnumber", "e0e712e4-b5e2-4b03-a401-1c828e0f2726")
  .header("cache-control", "no-cache")
  .header("postman-token", "e8385cf5-fbc0-c9eb-763f-04258aa5a021")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/transaction/list/10/0/1491139308',
  headers: 
   { 'postman-token': '265135d6-e780-0ffa-4013-1c8446e9a584',
     'cache-control': 'no-cache',
     'x-auth-accountnumber': 'e0e712e4-b5e2-4b03-a401-1c828e0f2726',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/list/10/0/1491139308"

headers = {
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'x-auth-accountnumber': "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
    'cache-control': "no-cache",
    'postman-token': "ac72f7d1-fb13-8b5d-5d2d-7567e13dcd1d"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "ID": 490926,
            "PainType": 1003,
            "Sender": {
                "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "4",
            "Fee": "0.00039999998989515007",
            "Geo": [
                0,
                0
            ],
            "Desc": "????",
            "Status": "requested",
            "Timestamp": 1505653122
        },
        {
            "ID": 490925,
            "PainType": 1002,
            "Sender": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Receiver": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Amount": "-8",
            "Fee": "0.0007999999797903001",
            "Geo": [
                10,
                10
            ],
            "Desc": "????",
            "Status": "approved",
            "Timestamp": 1505652044
        },
        {
            "ID": 490924,
            "PainType": 1000,
            "Sender": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "120",
            "Fee": "0.012000000104308128",
            "Geo": [
                10,
                10
            ],
            "Desc": "",
            "Status": "approved",
            "Timestamp": 1505651801
        },
        {
            "ID": 490923,
            "PainType": 1,
            "Sender": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Receiver": {
                "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "-20",
            "Fee": "0.0020000000949949026",
            "Geo": [
                11,
                12
            ],
            "Desc": "Test desc",
            "Status": "approved",
            "Timestamp": 1505650285
        },
        {
            "ID": 490922,
            "PainType": 1000,
            "Sender": {
                "AccountNumber": "0",
                "BankNumber": "0",
                "Name": ""
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "Bankai,Alice"
            },
            "Amount": "120",
            "Fee": "0.012000000104308128",
            "Geo": [
                10,
                10
            ],
            "Desc": "????",
            "Status": "approved",
            "Timestamp": 1505650282
        }
    ]
}
```

> Error response:

```json
{
    "error": "Sender invalid"
}
```

This endpoint retrieves a given number of transactions against an account in a paginated manner after a given unix timestamp. The account is determined through the additional header `X-Auth-AccountNumber`. This must be an account you own.

### HTTP Request

`GET https://demo.bvnk.co/transaction/list/{perPage}/{pageNum}/{timestamp}`

### Headers

`X-Auth-Token: {auth token}`
`X-Auth-AccountNumber: {account number}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PerPage | true | The number of records to receive per request. This cannot exceed 100.
PageNum | true | The page number for records to receive. To receive the first page, set this value to 0.
Timestamp | true | The time after which to check for transactions. This is a unix timestamp.


## Split Transaction

```shell
curl -X POST \
  https://demo.bvnk.co/transaction/split/request \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 9f614d89-9d45-ae63-00ce-37c9494855fe' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F TransactionNumber=490925 \
  -F AccountNumbers=9bd356cd-1c54-498d-b6b5-26a8d0a17940@
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

    url := "https://demo.bvnk.co/transaction/split/request"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490925\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumbers\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "15b4352a-dc24-3882-883a-01bb6a83afab")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/split/request")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "f8186c1d-e112-a181-8acd-bf7d708a76df")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490925\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumbers\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/transaction/split/request',
  headers: 
   { 'postman-token': '6a312456-67d0-7b42-9caa-3f408c620429',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { TransactionNumber: '490925',
     AccountNumbers: '9bd356cd-1c54-498d-b6b5-26a8d0a17940@' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/split/request"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490925\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumbers\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "95f2e21a-a390-004f-8cf8-cc3b8b82b3a2"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "Transaction successfully split"
}
```

> Error response:

```json
{
    "error": "Account 9bd356cd-1c54-498d-b6b5-26a8d0a17940-incorrect not found"
}
```

This endpoint splits a transaction between N number of accounts evenly. This transaction must be one in which you are the sender. 
The accounts are sent through in `accountNumber@bankNumber,accountNumber@bankNumber,...` format. 
If the transaction is worth 50, and there are 4 accounts in this request (making 5 total) each transaction request will be 10.

The recipient of the split request will receive a notification. They can then check the transaction and confirm it using the route [confirm split transaction](#confirm-split-transaction). The transaction will then be approved and balances will be updated.

### HTTP Request

`POST https://demo.bvnk.co/transaction/split/request`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | --------
TransactionNumber | true | Transaction number to split. This is the transaction ID of the given transaction. You must be the sender of this transaction.
AccountNumbers | true | A list of accounts to split the transaction against. Must be in format `accountNumber1@bankNumber,accountNumber2@bankNumber,...`


## Confirm Split Transaction

```shell
curl -X POST \
  https://demo.bvnk.co/transaction/split/confirm \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 99042a84-91c0-8bb6-3161-81f2919c79ea' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F TransactionNumber=490928
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

    url := "https://demo.bvnk.co/transaction/split/confirm"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490928\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "a10f5345-9885-30d6-d4a7-7258e9b479e4")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/split/confirm")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "7e108299-d369-d7ef-922f-5a7dbd29d225")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490928\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/transaction/split/confirm',
  headers: 
   { 'postman-token': '6e967d76-5fbc-88b5-c0dc-3d7466b9adf5',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { TransactionNumber: '490928' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/transaction/split/confirm"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n490928\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "ae155a2c-31d7-b514-62cd-ff17b9747d79"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "This transaction can no longer be confirmed"
}
```

This endpoint confirms a split transaction request. This will change the transaction status from "requested" to "approved" and the sender and recipient's balances will be updated accordingly.

### HTTP Request

`POST https://demo.bvnk.co/transaction/split/confirm`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
TransactionNumber | true | Transaction number to confirm. This is the transaction ID of the given transaction. You must be the sender of this transaction.

## Request Transaction

```shell
curl -X POST \
  https://debug.bankai.co/transaction/request \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: dac70b98-9c6d-e7e2-a33f-4ac2e5b86f36' \
  -H 'x-auth-token: 01b9798e-81b0-4286-a0d6-c000f607b98f' \
  -F TransactionAmount=100 \
  -F RequestorAccountNumber=1753e6ca-87d5-424a-bb2e-ba5ec00efe6f@ \
  -F RequesteeAccountNumber=3168113d-04fe-467f-b9b8-cdd758a98d00 \
  -F 'Description=Requesting payment 4' \
  -F Lat=0 \
  -F Lon=0
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

    url := "https://debug.bankai.co/transaction/request"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionAmount\"\r\n\r\n100\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequestorAccountNumber\"\r\n\r\n1753e6ca-87d5-424a-bb2e-ba5ec00efe6f@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequesteeAccountNumber\"\r\n\r\n3168113d-04fe-467f-b9b8-cdd758a98d00\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Description\"\r\n\r\nRequesting payment 4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "01b9798e-81b0-4286-a0d6-c000f607b98f")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "ce2dc7bb-d1fa-6984-a614-2ea952926701")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://debug.bankai.co/transaction/request")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "01b9798e-81b0-4286-a0d6-c000f607b98f")
  .header("cache-control", "no-cache")
  .header("postman-token", "419b0b74-f97a-3d14-4083-32bc7169825c")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionAmount\"\r\n\r\n100\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequestorAccountNumber\"\r\n\r\n1753e6ca-87d5-424a-bb2e-ba5ec00efe6f@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequesteeAccountNumber\"\r\n\r\n3168113d-04fe-467f-b9b8-cdd758a98d00\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Description\"\r\n\r\nRequesting payment 4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://debug.bankai.co/transaction/request',
  headers: 
   { 'postman-token': '91d13e5c-cdd4-4055-b6d3-da6fcb485222',
     'cache-control': 'no-cache',
     'x-auth-token': '01b9798e-81b0-4286-a0d6-c000f607b98f',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { TransactionAmount: '100',
     RequestorAccountNumber: '1753e6ca-87d5-424a-bb2e-ba5ec00efe6f@',
     RequesteeAccountNumber: '3168113d-04fe-467f-b9b8-cdd758a98d00',
     Description: 'Requesting payment 4',
     Lat: '0',
     Lon: '0' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://debug.bankai.co/transaction/request"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionAmount\"\r\n\r\n100\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequestorAccountNumber\"\r\n\r\n1753e6ca-87d5-424a-bb2e-ba5ec00efe6f@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RequesteeAccountNumber\"\r\n\r\n3168113d-04fe-467f-b9b8-cdd758a98d00\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Description\"\r\n\r\nRequesting payment 4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "01b9798e-81b0-4286-a0d6-c000f607b98f",
    'cache-control': "no-cache",
    'postman-token': "3860af4c-178d-687e-ff1b-b121017026af"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "Transaction successfully requested"
}
```

> Error response:

```json
{
    "error": "Recipient account number not found"
}
```

This endpoint requests a transaction from another account. 


### HTTP Request

`POST https://demo.bvnk.co/transaction/request`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
TransactionAmount | true | The amount to request
RequestorAccountNumber | true | The recipient of the requested transaction. This account should be owned by the authenticated user
RequesteeAccountNumber | true | The sender of the requested transaction
Description | false | Description for the transaction
Lat | false | Latitude of transaction
Lon | false | Longitude of transaction

## Confirm Transaction

```shell
curl -X POST \
  https://debug.bankai.co/transaction/confirm \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 86037339-7ba8-b9f8-25b6-a8a97d683227' \
  -H 'x-auth-token: 01b9798e-81b0-4286-a0d6-c000f607b98f' \
  -F TransactionNumber=2156
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

    url := "https://debug.bankai.co/transaction/confirm"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n2156\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "01b9798e-81b0-4286-a0d6-c000f607b98f")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "98c613fb-6450-4267-ec93-0121bc122bf3")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://debug.bankai.co/transaction/confirm")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "01b9798e-81b0-4286-a0d6-c000f607b98f")
  .header("cache-control", "no-cache")
  .header("postman-token", "04ec963b-2322-c733-db63-b1657b910eac")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n2156\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://debug.bankai.co/transaction/confirm',
  headers: 
   { 'postman-token': 'f29ebcb7-cad2-fd1f-c57e-420868887614',
     'cache-control': 'no-cache',
     'x-auth-token': '01b9798e-81b0-4286-a0d6-c000f607b98f',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { TransactionNumber: '2156' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://debug.bankai.co/transaction/confirm"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"TransactionNumber\"\r\n\r\n2156\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "01b9798e-81b0-4286-a0d6-c000f607b98f",
    'cache-control': "no-cache",
    'postman-token': "98f401be-1b7b-7f80-0c22-41aca17e0fee"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "Transaction approved"
}
```

> Error response:

```json
{
    "error": "Insufficient funds available"
}
```

This endpoint confirms a requested transaction. The authorized user must be the sender of the transaction (the requestee).
The transaction number can be received from a "Get transactions" call.


### HTTP Request

`POST https://demo.bvnk.co/transaction/confirm`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
TransactionNumber | true | The transaction number to approve

# Cards

Card issuance and charging depend on the deployment environment and who BVNK is integrated with in that territory. On the demo instance, we generate PANs per card and save them locally.

In live production environments, we don't issue cards ourselves and we currently do not store any PANs.

## Card Issuance

```shell
curl -X POST \
  https://demo.bvnk.co/card \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: b882bda7-0051-7aea-c3fc-788dc349da4a' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F AccountNumber=e0e712e4-b5e2-4b03-a401-1c828e0f2726@
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

    url := "https://demo.bvnk.co/card"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumber\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "63fa3d4a-3184-1dbd-8fa6-efc2fb12b3d4")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/card")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "cf59707c-e0d3-832f-902d-75b951ec64eb")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumber\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/card',
  headers: 
   { 'postman-token': '7d0de99b-b56a-8d48-f00a-8c5b271c3e43',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { AccountNumber: 'e0e712e4-b5e2-4b03-a401-1c828e0f2726@' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/card"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountNumber\"\r\n\r\ne0e712e4-b5e2-4b03-a401-1c828e0f2726@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "1d2354d9-eab5-ef91-87ab-d7aba26b80ec"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "MaskedPAN": "2398-47XX-XXXX-3872",
        "DailyLimit": "250",
        "MonthlyLimit": "2500",
        "State": "initiated",
        "PIN": "9427",
        "Salt": ""
    }
}
```

> Error response:

```json
{
    "error": "Could not create card"
}
```

This endpoint generates a new card against a given account number you control. Card PINs are stored encrypted in the database and can only be seen clear text on card issuance or when requested using 2FA.

### HTTP Request

`POST https://demo.bvnk.co/card`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountNumber | true | Account number for card to be linked against. Must be in format `accountNumber@bankNumber` where `bankNumber` can be left blank to default to current instance.

## Charge A Card

```shell
curl -X POST \
  https://demo.bvnk.co/card/charge \
  -H 'authorization: Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 85482d0b-38c4-eb2e-9d91-1c44a9f1077e' \
  -F SenderDetails=2398-47XX-XXXX-3872 \
  -F RecipientDetails=9bd356cd-1c54-498d-b6b5-26a8d0a17940@ \
  -F Amount=20 \
  -F Lat=11.0 \
  -F Lon=12.0 \
  -F 'Desc=Test desc'
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

    url := "https://demo.bvnk.co/card/charge"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\n2398-47XX-XXXX-3872\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "61a804a7-bdae-494b-a8ad-3564db5f60db")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/card/charge")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("authorization", "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV")
  .header("cache-control", "no-cache")
  .header("postman-token", "95514901-2f7b-7a16-4ec7-31345e408146")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\n2398-47XX-XXXX-3872\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/card/charge',
  headers: 
   { 'postman-token': 'afb71910-e441-9efd-d9f1-50a5ac6179d6',
     'cache-control': 'no-cache',
     authorization: 'Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { SenderDetails: '2398-47XX-XXXX-3872',
     RecipientDetails: '9bd356cd-1c54-498d-b6b5-26a8d0a17940@',
     Amount: '20',
     Lat: '11.0',
     Lon: '12.0',
     Desc: 'Test desc' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/card/charge"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"SenderDetails\"\r\n\r\n2398-47XX-XXXX-3872\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"RecipientDetails\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940@\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n20\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Desc\"\r\n\r\nTest desc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'authorization': "Basic ZGVtb0J6QSs2Zz09OldTblJpRmFQMHduM2w4M1k5V0I1QTFJS25FN0Jlb3dV",
    'cache-control': "no-cache",
    'postman-token': "96e8dbac-05e5-c5e3-8411-16da90f519c7"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "490932"
}
```

> Error response:

```json
{
    "error": "Account not found"
}
```

This endpoint issues a charge against a card which follows the same route as credit transaction. The card must be linked to an account you control.

### HTTP Request

`POST https://demo.bvnk.co/card/charge`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
SenderDetails | true | The sender card details. This is a masked PAN, e.g. `2398-47XX-XXXX-3872`. This card must be linked to your account
RecipientDetails | true | The recipient account details. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance
Amount | true | Amount to transfer
Lat | false | Latitude of transaction
Lon | false | Longitude of transaction
Desc | false | Description of transaction, emojis welcome 🎉💵⚡️

# Beneficiaries

## Add Beneficiary

```shell
curl -X POST \
  https://demo.bvnk.co/account/beneficiary \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 89f8a27e-f87f-4ed8-c958-bf86b196a1d3' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F BeneficiaryAccountNumber=9bd356cd-1c54-498d-b6b5-26a8d0a17940 \
  -F BeneficiaryBankNumber= \
  -F 'BeneficiaryNickname=Jacky Jacks'
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

    url := "https://demo.bvnk.co/account/beneficiary"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJacky Jacks\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "6178acd9-7318-7e51-abbb-438d0ca6d20d")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/beneficiary")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "f1f78664-f85c-21cf-0006-2a08a92c3a64")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJacky Jacks\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account/beneficiary',
  headers: 
   { 'postman-token': '5e74e8ad-10d7-f3f3-94e8-dc0a66632735',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { BeneficiaryAccountNumber: '9bd356cd-1c54-498d-b6b5-26a8d0a17940',
     BeneficiaryBankNumber: '',
     BeneficiaryNickname: 'Jacky Jacks' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/beneficiary"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJacky Jacks\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "b23bbdb6-d9ad-0f70-1c26-0eee9f380420"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Could not add beneficiary: Beneficiary account not found"
}
```

This endpoint adds a beneficiary to the users beneficiaries list. A nickname can be added for ease of recognition, especially when one user has multiple accounts.

### HTTP Request

`POST https://demo.bvnk.co/account/beneficiary`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
BeneficiaryAccountNumber | true | The beneficiary account number.
BeneficiaryBankNumber | false | The beneficary bank number.
BeneficiaryNickname | false | A nickname for the beneficiary

## View Beneficiary

```shell
curl -X GET \
  https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0 \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 5f9e88fd-629e-dedd-338b-c942d7f6c0b9' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F BeneficiaryAccountNumber=85c2b5cb-9820-4e8d-aa24-9e977bbb87b6 \
  -F BeneficiaryBankNumber= \
  -F BeneficiaryNickname=
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

    url := "https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("GET", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "7a941cea-7880-268b-3db6-b24509be2169")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "bc9a90eb-dce2-8909-c16e-8c5ea45e3310")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0',
  headers: 
   { 'postman-token': 'e9e215f3-5594-02c4-15e7-834b6aabf1b3',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { BeneficiaryAccountNumber: '85c2b5cb-9820-4e8d-aa24-9e977bbb87b6',
     BeneficiaryBankNumber: '',
     BeneficiaryNickname: '' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "fa497d35-c87b-898b-e3fb-4ce0e02d36e4"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
        "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
        "AccountHolderName": "Bankai,Alice",
        "AccountHolderNickname": "Jacky Jacks"
    }
}
```

> Error response:

```json
{
    "error": "An error occurred retrieving the beneficiary"
}
```

This endpoint retrieves all details of a given beneficiary linked to your account.

### HTTP Request

`GET https://demo.bvnk.co/account/beneficiary/{beneficiaryAccountNumber}/{beneficiaryBankNumber}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
BeneficiaryAccountNumber | true | The beneficiary account number.
BeneficiaryBankNumber | false | The beneficary bank number.

## Update A Beneficiary

```shell
curl -X PUT \
  https://demo.bvnk.co/account/beneficiary \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 55c53f63-f958-9fa5-284f-f62fed29d6f1' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F BeneficiaryAccountNumber=9bd356cd-1c54-498d-b6b5-26a8d0a17940 \
  -F BeneficiaryBankNumber= \
  -F 'BeneficiaryNickname=Jimmy Joe'
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

    url := "https://demo.bvnk.co/account/beneficiary"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJimmy Joe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("PUT", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "bea7cfca-820f-e043-a0b7-951619e9a2d5")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.put("https://demo.bvnk.co/account/beneficiary")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "4ed8598a-a406-14a5-fc51-61f4244f4b2a")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJimmy Joe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://demo.bvnk.co/account/beneficiary',
  headers: 
   { 'postman-token': 'b38279b5-7c74-638c-4188-7682742d93e7',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { BeneficiaryAccountNumber: '9bd356cd-1c54-498d-b6b5-26a8d0a17940',
     BeneficiaryBankNumber: '',
     BeneficiaryNickname: 'Jimmy Joe' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/beneficiary"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n9bd356cd-1c54-498d-b6b5-26a8d0a17940\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\nJimmy Joe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "1b70503b-2f95-b009-7627-985aef33a3fb"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
        "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
        "AccountHolderName": "Bankai,Alice",
        "AccountHolderNickname": "Jimmy Joe"
    }
}
```

> Error response:

```json
{
    "error": "An error occurred retrieving the beneficiary"
}
```

This endpoint allows a user to update a beneficiary. The only field that can currently be updated is the nickname. The endpoint responds with the updated record.

### HTTP Request

`PUT https://demo.bvnk.co/account/beneficiary`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
BeneficiaryAccountNumber | true | The beneficiary account number.
BeneficiaryBankNumber | false | The beneficary bank number.
BeneficiaryNickname | false | A nickname for the beneficiary

# View All Beneficiaries

```shell
curl -X GET \
  https://demo.bvnk.co/account/beneficiary/all/0/10 \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 120cf053-ed0e-2863-bb45-3337767a3346' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://demo.bvnk.co/account/beneficiary/all/0/10"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "fcfe929b-18c0-1f95-bd83-feb85a8c78b2")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/beneficiary/all/0/10")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "25db8f61-3555-ce62-2bf3-7dc62d1a37a7")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/beneficiary/all/0/10',
  headers: 
   { 'postman-token': '927aff57-24bd-0a28-6f48-4c80c0cd072b',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/beneficiary/all/0/10"

headers = {
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "7509357f-16b7-80d2-abf1-ebaa3ce9251b"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "Bankai,Alice",
            "AccountHolderNickname": "Jimmy Joe"
        }
    ]
}
```

> Error response:

```json
{
    "error": "An error occurred retrieving the list of beneficiaries"
}
```

This endpoint returns a list of all beneficiaries in paginated form. 

### HTTP Request

`GET https://demo.bvnk.co/account/beneficiary/all/{pageNum}/{perPage}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
PageNum | true | The page number for records to receive. To receive the first page, set this value to 0.
PerPage | true | The number of records to receive per request. This cannot exceed 100.

## Remove A Beneficiary

```shell
curl -X DELETE \
  https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0 \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 2c11fbdd-8a34-c658-ce27-eae4e2282674' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F BeneficiaryAccountNumber=85c2b5cb-9820-4e8d-aa24-9e977bbb87b6 \
  -F BeneficiaryBankNumber= \
  -F BeneficiaryNickname=
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

    url := "https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("DELETE", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "b75a1769-e84f-811e-18c0-d922ae9972c5")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.delete("https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("cache-control", "no-cache")
  .header("postman-token", "b845c621-6f9c-3604-0324-3bd193d448cc")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'DELETE',
  url: 'https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0',
  headers: 
   { 'postman-token': '44ed6e2e-4005-a2b2-d7be-084255aeeeb8',
     'cache-control': 'no-cache',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { BeneficiaryAccountNumber: '85c2b5cb-9820-4e8d-aa24-9e977bbb87b6',
     BeneficiaryBankNumber: '',
     BeneficiaryNickname: '' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/beneficiary/9bd356cd-1c54-498d-b6b5-26a8d0a17940/0"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryAccountNumber\"\r\n\r\n85c2b5cb-9820-4e8d-aa24-9e977bbb87b6\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryBankNumber\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"BeneficiaryNickname\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'cache-control': "no-cache",
    'postman-token': "9b708e73-8785-adeb-275c-3cb1bc8c48c6"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "An error occurred removing the beneficiary"
}
```

This endpoint removes a given beneficiary from your list of beneficiaries.

### HTTP Request

`DEL https://demo.bvnk.co/beneficiary/{beneficiaryAccountNumber}/{beneficiaryBankNumber}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
BeneficiaryAccountNumber | true | The account number of the beneficiary to remove.
BeneficiaryBankNumber | true | The bank number of the benficiary to remove.

# KYC

## Upload KYC Documents

```shell
curl -X POST \
  https://demo.bvnk.co/account/kyc \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 169c8a0d-150b-a65e-36dd-ff8757813e9b' \
  -H 'x-auth-token: 6c2eb753-0ae3-4176-9d3d-d8f723671e78' \
  -F 'Document=@[object Object]' \
  -F DocumentType=IDProof
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

    url := "https://demo.bvnk.co/account/kyc"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Document\"; filename=\"[object Object]\"\r\nContent-Type: false\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DocumentType\"\r\n\r\nIDProof\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "95e0d31b-3799-3690-89da-4d1c71370e3d")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/kyc")
  .header("x-auth-token", "6c2eb753-0ae3-4176-9d3d-d8f723671e78")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("cache-control", "no-cache")
  .header("postman-token", "aa696750-9f71-6110-8c04-f7b58cc0eafe")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Document\"; filename=\"[object Object]\"\r\nContent-Type: false\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DocumentType\"\r\n\r\nIDProof\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var fs = require("fs");
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account/kyc',
  headers: 
   { 'postman-token': 'c36ddb70-1b54-8c9e-c943-263b6e5ce398',
     'cache-control': 'no-cache',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW',
     'x-auth-token': '6c2eb753-0ae3-4176-9d3d-d8f723671e78' },
  formData: 
   { Document: 
      { value: 'fs.createReadStream("[object Object]")',
        options: { filename: {}, contentType: null } },
     DocumentType: 'IDProof' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/kyc"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Document\"; filename=\"[object Object]\"\r\nContent-Type: false\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DocumentType\"\r\n\r\nIDProof\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'x-auth-token': "6c2eb753-0ae3-4176-9d3d-d8f723671e78",
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'cache-control': "no-cache",
    'postman-token': "4f78737e-5de2-29a4-c2ca-869681c755c3"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Document must be a supported type"
}
```

This endpoint is used to upload Know-Your-Customer (KYC) documentation. There are several supported types of documention.

### HTTP Request

`POST https://demo.bvnk.co/account/kyc`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
Document | true | The file you wish to upload.
DocumentType | true | The type of document, must be one of IDProof or ResidentialProof. Any number of documents can be uploaded to support these two types.

# Merchants

## Merchant Account Create

```shell
curl -X POST \
  https://demo.bvnk.co/account/merchant \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: f10a243b-9a68-11e9-45d4-db02f7819610' \
  -H 'x-auth-token: fcb7ae8b-f88f-45fd-8e57-d273a1a014bc' \
  -F 'MerchantName=Test Merchant Ltd' \
  -F 'MerchantDescription=Supplying the best test since 2016' \
  -F MerchantContactGivenName=John \
  -F MerchantContactFamilyName=Test \
  -F 'MerchantAddressLine1=Office 1' \
  -F 'MerchantAddressLine2=Office Road' \
  -F 'MerchantAddressLine3=Office County' \
  -F MerchantCountry=UK \
  -F 'MerchantPostalCode=E14 5EW' \
  -F MerchantBusinessSector=Commerce \
  -F MerchantWebsite=testwebsite.com \
  -F MerchantContactPhone=0800-test-phone \
  -F MerchantContactFax=0800-test-fax \
  -F 'MerchantContactEmail=john@testwebsite,com' \
  -F MerchantLogo= \
  -F AccountType=merchant
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

    url := "https://demo.bvnk.co/account/merchant"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2016\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\nmerchant\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "f40c77b5-d4bc-187b-e832-e37ffe26934b")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/merchant")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc")
  .header("cache-control", "no-cache")
  .header("postman-token", "70918fa6-4515-2c01-e705-c5b06adbb72a")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2016\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\nmerchant\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account/merchant',
  headers: 
   { 'postman-token': 'f047420b-e6fa-f1a6-47ed-f60f6ac6677f',
     'cache-control': 'no-cache',
     'x-auth-token': 'fcb7ae8b-f88f-45fd-8e57-d273a1a014bc',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { MerchantName: 'Test Merchant Ltd',
     MerchantDescription: 'Supplying the best test since 2016',
     MerchantContactGivenName: 'John',
     MerchantContactFamilyName: 'Test',
     MerchantAddressLine1: 'Office 1',
     MerchantAddressLine2: 'Office Road',
     MerchantAddressLine3: 'Office County',
     MerchantCountry: 'UK',
     MerchantPostalCode: 'E14 5EW',
     MerchantBusinessSector: 'Commerce',
     MerchantWebsite: 'testwebsite.com',
     MerchantContactPhone: '0800-test-phone',
     MerchantContactFax: '0800-test-fax',
     MerchantContactEmail: 'john@testwebsite,com',
     MerchantLogo: '',
     AccountType: 'merchant' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/merchant"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2016\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\nmerchant\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc",
    'cache-control': "no-cache",
    'postman-token': "b28272b7-621b-0f7a-37f4-809c64804d68"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": "cfa74e69-5b5c-4c87-a0f6-4182165d2463"
}
```

> Error response:

```json
{
    "error": "Account type not valid for a merchant, must be one of merchant, credit, mortgage, loan"
}
```

This endpoint creates a merchant account. The response is the account number for the new merchant account.

### HTTP Request

`POST https://demo.bvnk.co/account/merchant`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
MerchantName | true | Name of the merchant.
MerchantDescription | true | Description of the merchant
MerchantContactGivenName | true | Given name of merchant contact
MerchantContactFamilyName | true | Family name of merchant contact
MerchantAddressLine1 | true | First line of address of merchant
MerchantAddressLine2 | false | Second line of address of merchant
MerchantAddressLine3 | false | Third line of address of merchant
MerchantCountry | true | Country of merchant
MerchantPostalCode | true | Postal code of merchant
MerchantBusinessSector | false | Business sector of merchant
MerchantWebsite | false | Website of merchant
MerchantContactPhone | true | Contact number of merchant 
MerchantContactFax | false | Fax number of merchant 
MerchantContactEmail | true | Email of merchant 
AccountType | true | Type of merchant account. Must be one of merchant, credit, mortgage, loan" 

## Update Merchant

```shell
curl -X PUT \
  https://demo.bvnk.co/account/merchant \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: fb0b61fa-793a-dad6-104d-06e7ead7f6f5' \
  -H 'x-auth-token: fcb7ae8b-f88f-45fd-8e57-d273a1a014bc' \
  -F 'MerchantName=Test Merchant Ltd' \
  -F 'MerchantDescription=Supplying the best test since 2017' \
  -F MerchantContactGivenName=John \
  -F MerchantContactFamilyName=Test \
  -F 'MerchantAddressLine1=Office 1' \
  -F 'MerchantAddressLine2=Office Road' \
  -F 'MerchantAddressLine3=Office County' \
  -F MerchantCountry=UK \
  -F 'MerchantPostalCode=E14 5EW' \
  -F MerchantBusinessSector=Commerce \
  -F MerchantWebsite=testwebsite.com \
  -F MerchantContactPhone=0800-test-phone \
  -F MerchantContactFax=0800-test-fax \
  -F 'MerchantContactEmail=john@testwebsite,com' \
  -F MerchantLogo= \
  -F MerchantID=a66644fe-2a69-4f6b-935d-0d573e9f19fc
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

    url := "https://demo.bvnk.co/account/merchant"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantID\"\r\n\r\na66644fe-2a69-4f6b-935d-0d573e9f19fc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("PUT", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "f75159da-ebbc-84a6-585c-f96b406c88a8")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.put("https://demo.bvnk.co/account/merchant")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc")
  .header("cache-control", "no-cache")
  .header("postman-token", "24383c59-db94-7cb3-3cf7-7854dd54cbd8")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantID\"\r\n\r\na66644fe-2a69-4f6b-935d-0d573e9f19fc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://demo.bvnk.co/account/merchant',
  headers: 
   { 'postman-token': '910fe9e5-aaba-174e-4d96-e1d131f09477',
     'cache-control': 'no-cache',
     'x-auth-token': 'fcb7ae8b-f88f-45fd-8e57-d273a1a014bc',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: 
   { MerchantName: 'Test Merchant Ltd',
     MerchantDescription: 'Supplying the best test since 2017',
     MerchantContactGivenName: 'John',
     MerchantContactFamilyName: 'Test',
     MerchantAddressLine1: 'Office 1',
     MerchantAddressLine2: 'Office Road',
     MerchantAddressLine3: 'Office County',
     MerchantCountry: 'UK',
     MerchantPostalCode: 'E14 5EW',
     MerchantBusinessSector: 'Commerce',
     MerchantWebsite: 'testwebsite.com',
     MerchantContactPhone: '0800-test-phone',
     MerchantContactFax: '0800-test-fax',
     MerchantContactEmail: 'john@testwebsite,com',
     MerchantLogo: '',
     MerchantID: 'a66644fe-2a69-4f6b-935d-0d573e9f19fc' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/merchant"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantName\"\r\n\r\nTest Merchant Ltd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantDescription\"\r\n\r\nSupplying the best test since 2017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFamilyName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine1\"\r\n\r\nOffice 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine2\"\r\n\r\nOffice Road\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantAddressLine3\"\r\n\r\nOffice County\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantCountry\"\r\n\r\nUK\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantPostalCode\"\r\n\r\nE14 5EW\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantBusinessSector\"\r\n\r\nCommerce\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantWebsite\"\r\n\r\ntestwebsite.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactPhone\"\r\n\r\n0800-test-phone\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactFax\"\r\n\r\n0800-test-fax\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantContactEmail\"\r\n\r\njohn@testwebsite,com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"MerchantID\"\r\n\r\na66644fe-2a69-4f6b-935d-0d573e9f19fc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "fcb7ae8b-f88f-45fd-8e57-d273a1a014bc",
    'cache-control': "no-cache",
    'postman-token': "a60515aa-51f1-5681-e1f3-9fa1bf88a24a"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": ""
}
```

> Error response:

```json
{
    "error": "Could not update merchant"
}
```

This route updates a given merchant with the new details. Only changed fields need to be included. `merchantID` field is the only mandatory field.

### HTTP Request

`PUT https://demo.bvnk.co/account/merchant`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
MerchantName | false | Name of the merchant.
MerchantDescription | false | Description of the merchant
MerchantContactGivenName | false | Given name of merchant contact
MerchantContactFamilyName | false | Family name of merchant contact
MerchantAddressLine1 | false | First line of address of merchant
MerchantAddressLine2 | false | Second line of address of merchant
MerchantAddressLine3 | false | Third line of address of merchant
MerchantCountry | false | Country of merchant
MerchantPostalCode | false | Postal code of merchant
MerchantBusinessSector | false | Business sector of merchant
MerchantWebsite | false | Website of merchant
MerchantContactPhone | false | Contact number of merchant 
MerchantContactFax | false | Fax number of merchant 
MerchantContactEmail | false | Email of merchant 
MerchantID | true | The account number of the merchant

## View Merchant

```shell
curl -X GET \
  https://debug.bankai.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 52b971e7-ced0-02ce-08ec-b84782b72b5c' \
  -H 'x-auth-token: 09c3ced7-6aa7-4705-a069-c1d8bae5b7fa'
```

```go
package main

import (
    "fmt"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "https://debug.bankai.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e"

    req, _ := http.NewRequest("GET", url, nil)

    req.Header.Add("x-auth-token", "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "a6d165b9-9769-d2e4-2f84-4c4488decccd")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://debug.bankai.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e")
  .header("x-auth-token", "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa")
  .header("cache-control", "no-cache")
  .header("postman-token", "d870e814-a18f-aa53-917b-74bce13650d7")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://debug.bankai.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e',
  headers: 
   { 'postman-token': '48c62e5c-5f7d-b6d2-0add-d274ccfeef56',
     'cache-control': 'no-cache',
     'x-auth-token': '09c3ced7-6aa7-4705-a069-c1d8bae5b7fa' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://debug.bankai.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e"

headers = {
    'x-auth-token': "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa",
    'cache-control': "no-cache",
    'postman-token': "956096a4-d80f-c7b9-2dbd-8ae127cd7f48"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "ID": "7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e",
        "Name": "Test Merchant Ltd",
        "Description": "Supplying the best test since 2017",
        "ContactGivenName": "John",
        "ContactFamilyName": "Test",
        "AddressLine1": "Office 1",
        "AddressLine2": "Office Road",
        "AddressLine3": "Office County",
        "Country": "UK",
        "PostalCode": "E14 5EW",
        "BusinessSector": "Commerce",
        "Website": "testwebsite.com",
        "ContactPhone": "0800-test-phone",
        "ContactFax": "0800-test-fax",
        "ContactEmail": "john@testwebsite,com",
        "Logo": "",
        "IdentificationNumber": "",
        "Timestamp": 1505657292
    }
}
```

> Error response:

```json
{
    "error": "Could not retrieve merchant from given Merchant ID. No merchant found"
}
```

This endpoint retrieves details on a given merchant.

### HTTP Request

`GET https://demo.bvnk.co/account/merchant/{merchantID}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
MerchantID | true | The account number of the merchant

## Search For A Merchant

```shell
curl -X POST \
  https://debug.bankai.co/account/merchantSearch \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 3e9d6fa1-cf74-d219-33bd-448400636db6' \
  -H 'x-auth-token: 09c3ced7-6aa7-4705-a069-c1d8bae5b7fa' \
  -F Search=merch
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

    url := "https://debug.bankai.co/account/merchantSearch"

    payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\nmerch\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
    req.Header.Add("x-auth-token", "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa")
    req.Header.Add("cache-control", "no-cache")
    req.Header.Add("postman-token", "b040dfa1-c95e-13a8-3e7b-952fb7ab7419")

    res, _ := http.DefaultClient.Do(req)

    defer res.Body.Close()
    body, _ := ioutil.ReadAll(res.Body)

    fmt.Println(res)
    fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://debug.bankai.co/account/merchantSearch")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("x-auth-token", "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa")
  .header("cache-control", "no-cache")
  .header("postman-token", "010d8222-db29-ef7e-9c63-727e00920faf")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\nmerch\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://debug.bankai.co/account/merchantSearch',
  headers: 
   { 'postman-token': '0d20580a-a8c7-0de8-5ef5-6c4395ba88ae',
     'cache-control': 'no-cache',
     'x-auth-token': '09c3ced7-6aa7-4705-a069-c1d8bae5b7fa',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { Search: 'merch' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://debug.bankai.co/account/merchantSearch"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Search\"\r\n\r\nmerch\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-auth-token': "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa",
    'cache-control': "no-cache",
    'postman-token': "eadae3bb-47ab-1c47-44b5-57bfc8f6fc12"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "ID": "f0bc5426-67c0-4427-a36b-587d7ff8c5a7",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "f03645dc-e898-4e64-bb38-095fd2209b9c",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "e0838741-a950-41e3-9138-842c3e884ef2",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "1050d88b-a3d2-4d88-888c-3d5a765682a4",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "80ecf96f-4824-4d19-a3c6-b7dbe33d0445",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "be721742-80bd-4a6b-b79b-9b9e269b465c",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
        {
            "ID": "fac60d6f-ce80-4f2c-8c51-4a4cb4d33976",
            "Name": "Test Merchant Ltd",
            "Description": "Supplying the best test since 2015",
            "ContactGivenName": "",
            "ContactFamilyName": "",
            "AddressLine1": "",
            "AddressLine2": "",
            "AddressLine3": "",
            "Country": "",
            "PostalCode": "",
            "BusinessSector": "",
            "Website": "",
            "ContactPhone": "",
            "ContactFax": "",
            "ContactEmail": "",
            "Logo": "",
            "IdentificationNumber": "",
            "Timestamp": 0
        },
    ]
}
```

> Error response:

```json
{
    "error": "An error occurred searching for the merchant"
}
```

This endpoint performs a fuzzy match search for merchants on merchant name and merchant description, and an exact search on merchantID.


### HTTP Request

`POST https://demo.bvnk.co/account/merchantSearch`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
Search | true | Term to search for. Must be at least 4 characters in length.

# Integrations

BVNK integrates with numerous providers, and is extensible depending on the deploy and requirements.

When integrations are requested, we will guide clients through the process of linking their BVNK deploy to the various third parties.

## SMS

We currently offer integrations with the following providers:

- Nexmo
- MessageBird
- TotalSend

## USSD

We currently offer integrations with the following providers:

- TotalSend

## Chat applications

We currently offer integrations with the following chat applications:

- Facebook Messenger

# Contact

For more information please reach out to us on [BVNK](https://bvnk.co/contact)
