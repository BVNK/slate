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

