# Exchange

## Get countries

```shell
curl -X GET \
  https://demo.bvnk.co/countries \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 0b2361d5-8847-1332-34d6-8e064df61c44' \
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/countries"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "8873f14e-bd7a-030c-4402-6d1f7c2819d3")

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
  url: 'https://demo.bvnk.co/countries',
  headers:
   { 'Postman-Token': '5c74b03f-c58c-23de-83f3-8bbb90a174c4',
     'Cache-Control': 'no-cache'} };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/countries"

headers = {
    'Cache-Control': "no-cache",
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/countries")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "a7d7840f-ad30-654e-5019-50c491f25d75")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "Name": "Afghanistan",
            "ISO2": "AF",
            "ISO3": "AFG",
            "ISONum": "004"
        },
        {
            "Name": "ALA Aland Islands",
            "ISO2": "AX",
            "ISO3": "ALA",
            "ISONum": "248"
        },
    ...
}
```

> Error response:

```json
{
    "error": "Countries could not be retrieved"
}
```

This endpoint returns a list of countries. One of these countries *must* be used when creating a new user. 

### HTTP Request

`GET https://demo.bvnk.co/countries`

### Headers

This request requires no headers.

### URL Parameters

This request takes no parameters.

## Get currencies

```shell
curl -X GET \
  https://demo.bvnk.co/currencies \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 777af451-3b5c-3250-95d4-a48a94af7404' \
  -H 'X-Auth-Token: d382f67c-5bcc-4d3d-b3a9-9a0253114d33'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/currencies"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "d382f67c-5bcc-4d3d-b3a9-9a0253114d33")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "1b31660b-cc65-1cdc-ed91-7bb7482a4c69")

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
  url: 'https://demo.bvnk.co/currencies',
  headers:
   { 'Postman-Token': 'fb18d8ae-ceca-651e-c669-bec629a40b9e',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'd382f67c-5bcc-4d3d-b3a9-9a0253114d33' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/currencies"

headers = {
    'X-Auth-Token': "d382f67c-5bcc-4d3d-b3a9-9a0253114d33",
    'Cache-Control': "no-cache",
    'Postman-Token': "e3063cd0-5ddf-c7ec-8a4a-e8a1eea594b0"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java 
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/currencies")
  .header("X-Auth-Token", "d382f67c-5bcc-4d3d-b3a9-9a0253114d33")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "9ce05e22-78c6-45c2-b9a7-1309c4886302")
  .asString();
```

> Successful response:

```json
{
    "response": {
        "bct": {
            "Name": "Bitcoin Test",
            "Code": "bct",
            "Type": "crypto",
            "UnitsPerCoin": 100000000,
            "Timestamp": ""
        },
        "btc": {
            "Name": "Bitcoin",
            "Code": "btc",
            "Type": "crypto",
            "UnitsPerCoin": 100000000,
            "Timestamp": ""
        },
        "gbp": {
            "Name": "British Pounds",
            "Code": "gbp",
            "Type": "fiat",
            "UnitsPerCoin": 100,
            "Timestamp": ""
        },
        "usd": {
            "Name": "United States Dollar",
            "Code": "usd",
            "Type": "fiat",
            "UnitsPerCoin": 100,
            "Timestamp": ""
        },
        "zar": {
            "Name": "South African Rand",
            "Code": "zar",
            "Type": "fiat",
            "UnitsPerCoin": 100,
            "Timestamp": ""
        }
    }
}
```

> Error response:

```json
{
    "error": "Token invalid"
}
```

This endpoint returns a list of currencies available on the deploy. The user must be logged in.

### HTTP Request

`GET https://demo.bvnk.co/currencies`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

This request takes no parameters.

## Get quote

```shell
curl -X GET \
  https://demo.bvnk.co/exchange/quote/btc/zar/1 \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 769a5f45-3b56-e0fc-43db-2b1c9b47b6b8' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/exchange/quote/btc/zar/1"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "edf6f1a0-20d4-3ca9-33af-850a005fb746")

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
  url: 'https://demo.bvnk.co/exchange/quote/btc/zar/1',
  headers:
   { 'Postman-Token': '11bd6b7a-01bc-a8c4-27d2-56e2c3dd9346',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/exchange/quote/btc/zar/1"

headers = {
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "bac9b10c-9df6-3cd9-4449-89de28a96013"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/exchange/quote/btc/zar/1")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "d0608718-1821-a391-2382-aaa105035fac")
  .asString();
```

> Successful response:

```json
{
    "response": {
        "SourceCurrency": "BTC",
        "DestinationCurrency": "ZAR",
        "SourceAmount": "2",
        "DestinationAmount": "223245.637648",
        "ConversionRate": "111622.818824"
    }
}
```

> Error response:

```json
{
    "error": "Destination currency NA is invalid"
}
```

This route returns a quote for the given currency pair and amount.

### HTTP Request

`GET https://demo.bvnk.co/exchange/quote/{sourceCurrency}/{destinationCurrency}/{amount}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
SourceCurrency | true | The source currency to convert from. This currency must be supported by the deploy, retrieved from `GET /currencies`.
DestinationCurrency | true | The destination currency to convert to. This currency must be supported by the deploy, retrieved from `GET /currencies`.
Amount | true | The amount to convert.

## Get rates

```shell
curl -X GET \
  https://demo.bvnk.co/exchange/rates/btc/zar/hour \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 874ce447-2a99-e848-1e61-829cee013b8d' \
  -H 'X-Auth-Token: d382f67c-5bcc-4d3d-b3a9-9a0253114d33'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/exchange/rates/btc/zar/hour"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("X-Auth-Token", "d382f67c-5bcc-4d3d-b3a9-9a0253114d33")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "ea4a2a13-e561-e198-5c82-58d4b8c6f694")

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
  url: 'https://demo.bvnk.co/exchange/rates/btc/zar/hour',
  headers:
   { 'Postman-Token': '420b140b-2473-f317-bef0-f5907791e184',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'd382f67c-5bcc-4d3d-b3a9-9a0253114d33' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/exchange/rates/btc/zar/hour"

headers = {
    'X-Auth-Token': "d382f67c-5bcc-4d3d-b3a9-9a0253114d33",
    'Cache-Control': "no-cache",
    'Postman-Token': "714b0b8c-f946-ad74-5859-66a1a9f0cfaa"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/exchange/rates/btc/zar/hour")
  .header("X-Auth-Token", "d382f67c-5bcc-4d3d-b3a9-9a0253114d33")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "6b44ae48-388b-d6d4-c2d7-2ab0b17081cc")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "SourceCurrency": "BTC",
            "DestinationCurrency": "ZAR",
            "SourceAmount": "1",
            "DestinationAmount": "12840.95984863280423557421875",
            "ConversionRate": "12840.9598486328042356",
            "Timestamp": "2018-02-13 05:35:36"
        },
        {
            "SourceCurrency": "BTC",
            "DestinationCurrency": "ZAR",
            "SourceAmount": "1",
            "DestinationAmount": "12537.90984206437235657421875",
            "ConversionRate": "12537.9098420643723566",
            "Timestamp": "2018-02-13 06:35:36"
        },
        ...
    ]
}
```

> Error response:

```json
{
    "error": "Could not retrieve rates"
}
```

This route returns market rate data for a given user for two currency pairs. The market rate period is passed 
through the URL, and a total of fifty data points are returned.

### HTTP Request

`GET https://demo.bvnk.co/exchange/rates/{sourceCurrency}/{destinationCurrency}/{period}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
SourceCurrency | true | The source currency to convert from. This currency must be supported by the deploy, retrieved from `GET /currencies`.
DestinationCurrency | true | The destination currency to convert to. This currency must be supported by the deploy, retrieved from `GET /currencies`.
Period | false | The period to get rates for. Currently supported values: `minute`, `15minute`, `hour`, `4hour`, `day`, `week`, `month`. Default: `hour`.

## Register customer

```shell
curl -X POST \
  https://demo.bvnk.co/exchange/customer \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 8a150947-6b5f-24f7-512b-662074f258ca' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F CardToken=tok_visa
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

	url := "https://demo.bvnk.co/exchange/customer"

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CardToken\"\r\n\r\ntok_visa\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "869b655f-1df8-cd6a-2bc1-2bb94888414c")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/exchange/customer',
  headers:
   { 'Postman-Token': '1d254da4-6873-50eb-273c-b0315cae210c',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117',
     'Content-Type': 'application/json',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { CardToken: 'tok_visa' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/exchange/customer"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CardToken\"\r\n\r\ntok_visa\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "6ac13232-1bd0-98ea-18d5-35ddff04fb01"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/exchange/customer")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "de609277-55f5-822e-6039-86abee25103e")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CardToken\"\r\n\r\ntok_visa\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
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
    "error": "Invalid token provided"
}
```

This route registers a user account as an exchange customer. This is a prerequisite for any transactions on the exchange. 

### HTTP Request

`POST /exchange/customer`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
CardToken | true | The tokenized PAN of the card to register against the user. This token is retrieved from the integration when adding a card, either through mobile SDKs or web pages.

## Purchase request

```shell
curl -X POST \
  https://demo.bvnk.co/exchange/request \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 424eb496-3e45-12b3-7f10-cb53b5e547ec' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F Currency=bct \
  -F Amount=0.001 \
  -F Lat=11.0 \
  -F Lon=12.0
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

	url := "https://demo.bvnk.co/exchange/request"

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Currency\"\r\n\r\nbct\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n0.001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "3a8f7ec9-3d05-9720-8900-c512ea4f0be7")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/exchange/request',
  headers:
   { 'Postman-Token': '4646621c-eb8d-fc11-bb9c-decbeb752d42',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117',
     'Content-Type': 'application/json',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { Currency: 'bct', Amount: '0.001', Lat: '11.0', Lon: '12.0' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/exchange/request"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Currency\"\r\n\r\nbct\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n0.001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "1096e90b-d86d-bc3f-33b5-a119edac4e00"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/exchange/request")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "e6de947d-18cb-5c20-3a2a-8c9a44ea01d8")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Currency\"\r\n\r\nbct\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Amount\"\r\n\r\n0.001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lat\"\r\n\r\n11.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Lon\"\r\n\r\n12.0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

> Successful response:

```json
{
    "response": "35"
}
```

> Error response:

```json
{
    "response": "User account not registered on exchange"
}
```

This route issues a new purchase request for a given amount of cryptocurrency. If the request cannot be fulfilled the user will be notified and the order can be left open or cancelled. 

This request returns the purchase request id.

### HTTP Request

`POST /exchange/request`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
Currency | true | Currency to purchase. This must be a supported cryptocurrency
Amount | true | Amount to purchase
Lat | false | Latitude of purchase
Lon | false | Longitude of purchase

## View requests

```shell
curl -X GET \
  https://demo.bvnk.co/exchange/requests \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: cbb2552e-fe3c-d072-5d8f-08ac1e64032d' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/exchange/requests"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "842a7810-a8d6-cf36-d1f5-d5c970353630")

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
  url: 'https://demo.bvnk.co/exchange/requests',
  headers:
   { 'Postman-Token': '55731e58-bc77-a34f-9b95-f6d3fb15b8d7',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117',
     'Content-Type': 'application/json' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/exchange/requests"

headers = {
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "91ebb752-8987-53fb-f5f6-fb65b9f3b858"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/exchange/requests")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "d643f307-eca0-46e1-060c-68d5613862ad")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "Currency": "bct",
            "Amount": "0.0010000000474974513",
            "Rate": "0",
            "Status": "pending",
            "RequestNumber": "c7ec4a52-4e9b-4955-976b-922358964cee"
        }
        ...
    ]
}
```

> Error response:

```json
{
    "response": "Could not retrieve list of exchange requests"
}
```

This route returns a list of requests for the given user.

### HTTP Request

`GET /exchange/requests`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

This route requires no parameters.

## View single request

```shell
curl -X GET \
  https://demo.bvnk.co/exchange/request/ae4d3372-8313-43cf-9eb1-c7e4019508be \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: ac0c3a7f-95dd-ff59-209b-99425a255475' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/exchange/request/ae4d3372-8313-43cf-9eb1-c7e4019508be"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "5821c5d3-5bb1-db06-24f3-12fa17745258")

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
  url: 'https://demo.bvnk.co/exchange/request/ae4d3372-8313-43cf-9eb1-c7e4019508be',
  headers:
   { 'Postman-Token': '5e18728e-4882-92b7-9c60-41d8a54d4304',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117',
     'Content-Type': 'application/json' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://demo.bvnk.co/exchange/request/ae4d3372-8313-43cf-9eb1-c7e4019508be"

headers = {
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "3c30b6d6-5062-a6f6-9006-6643548044cd"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/exchange/request/ae4d3372-8313-43cf-9eb1-c7e4019508be")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "d6ad2f1f-3eea-f895-1da8-f98e342cb993")
  .asString();
```

> Successful response:

```json
{
    "response": [
        {
            "Currency": "bct",
            "Amount": "0.0010000000474974513",
            "Rate": "0",
            "Status": "pending",
            "RequestNumber": "c7ec4a52-4e9b-4955-976b-922358964cee"
        }
    ]
}
```

> Error response:

```json
{
    "response": "Could not retrieve request"
}
```

This route returns a single request for the given user.

### HTTP Request

`GET /exchange/request/{requestID}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
RequestID | true | The ID of the request.
