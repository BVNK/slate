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
  https://demo.bvnk.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e \
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

    url := "https://demo.bvnk.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e"

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
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e")
  .header("x-auth-token", "09c3ced7-6aa7-4705-a069-c1d8bae5b7fa")
  .header("cache-control", "no-cache")
  .header("postman-token", "d870e814-a18f-aa53-917b-74bce13650d7")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e',
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

url = "https://demo.bvnk.co/account/merchant/7c9e7ec0-e18a-4a31-ac8b-8bb226afa06e"

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
  https://demo.bvnk.co/account/merchantSearch \
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

    url := "https://demo.bvnk.co/account/merchantSearch"

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
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/merchantSearch")
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
  url: 'https://demo.bvnk.co/account/merchantSearch',
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

url = "https://demo.bvnk.co/account/merchantSearch"

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


