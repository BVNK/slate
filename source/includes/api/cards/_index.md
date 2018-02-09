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

