
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
        "AccountHolderName": "bvnk,Alice",
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
        "AccountHolderName": "bvnk,Alice",
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

## View All Beneficiaries

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
            "AccountHolderName": "bvnk,Alice",
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

