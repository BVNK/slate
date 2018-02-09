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

The sender and recipient accounts can be in any currency and will be automatically converted between them. This allows for the sender to send BTC and the recipient to 
receive USD or visa-versa.

For cryptocurrency payments, one account must be of `CurrencyType` that is a cryptocurrency. External cryptocurrency payments can also be made in this call 
by specifying the `RecipientDetails` as a wallet address.

### HTTP Request

`POST https://demo.bvnk.co/transaction/credit`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
SenderDetails | true | The sender account details. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance. This must be your account
RecipientDetails | true | The recipient account details. Follows format `senderAccountNumber@bankAccountNumber`. Bank can be left blank and will default to given instance. This can also be a wallet address, e.g. `"RecipientDetails":"mpVWwEnRacX3tHwSFxZUKv6D5mF3p9Dr21@"`.
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
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
            },
            "Receiver": {
                "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
            },
            "Receiver": {
                "AccountNumber": "e0e712e4-b5e2-4b03-a401-1c828e0f2726",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
            },
            "Receiver": {
                "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
                "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
                "Name": "bvnk,Alice"
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
                "Name": "bvnk,Alice"
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
  https://demo.bvnk.co/transaction/request \
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

    url := "https://demo.bvnk.co/transaction/request"

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
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/request")
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
  url: 'https://demo.bvnk.co/transaction/request',
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

url = "https://demo.bvnk.co/transaction/request"

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
  https://demo.bvnk.co/transaction/confirm \
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

    url := "https://demo.bvnk.co/transaction/confirm"

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
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/transaction/confirm")
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
  url: 'https://demo.bvnk.co/transaction/confirm',
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

url = "https://demo.bvnk.co/transaction/confirm"

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


