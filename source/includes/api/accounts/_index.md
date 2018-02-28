# Accounts

## Create Account

```shell
curl -X POST \
  https://demo.bvnk.co/account \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: b32bfcc5-d0c6-07bf-b833-9cd815c21980' \
  -H 'X-Auth-Token: ee2cd9fb-a165-40c7-95af-c05d4d5f8117' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountCurrency=usd \
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

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "9937aa75-ed63-3800-1973-9b343d1fcef8")

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
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "775810d4-bd8e-a3fd-c72c-aa5ba51de164")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://demo.bvnk.co/account',
  headers:
   { 'Postman-Token': 'a91f96a0-c484-0b3f-e01a-5c902292a3a8',
     'Cache-Control': 'no-cache',
     'X-Auth-Token': 'ee2cd9fb-a165-40c7-95af-c05d4d5f8117',
     'Content-Type': 'application/json',
     'content-type': 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' },
  formData: { AccountCurrency: 'usd', AccountType: 'cheque' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountType\"\r\n\r\ncheque\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "8500c7f9-4664-73ea-cb1d-ce9f9355406a"
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

This endpoint is used to create an account against an existing user. As the user has already been registered, only the account type and currency are optional for this call.

Cryptocurrency accounts are created through this route by specifying the account currency as a supported cryptocurrency, e.g. `AccountCurrency: btc`. If you want to create a cryptocurrency account 
using a seed, specify the field `AccountSeed`.

Supported currencies are retrieved through `GET /currencies`.

### HTTP Request

`POST https://demo.bvnk.co/account`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountType | false | Account type, one of savings, cheque, merchant, money-market, cd, ira, rcp, credit, mortgage, loan. Default cheque.
AccountCurrency | false | Account currency which must be valid according to list retrieved from `GET /currencies`. Will default to system default.
AccountSeed | false | Seed used to create a cryptocurrency account from.

## Get All Accounts By ID

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
        "FamilyName": "bvnk",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "300000-0000-001",
        "ContactNumber1": "558555-1234",
        "ContactNumber2": "",
        "EmailAddress": "alice@bvnk.co",
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

## Get All Users

```shell
curl -X GET \
  https://demo.bvnk.co/account/user \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 2e3e1e5d-6f77-bfef-7e53-5606f86bca97' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0'
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://demo.bvnk.co/account/user"

  req, _ := http.NewRequest("GET", url, nil)

  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "a2252eec-ac2b-3fde-3a5d-d01b6bb50de7")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/user")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "51b7d8f2-eda9-b59e-df2d-dadb2ab6a5f1")
  .asString();
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://demo.bvnk.co/account/user");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "6bfd8d10-46a0-8eea-73b2-89c746d47cb4");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/user"

headers = {
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "5350373e-18dd-e5a3-c71d-65c4cc449bfc"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [{
        "GivenName": "Customer",
        "FamilyName": "Director",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "19000101-1234-007",
        "ContactNumber1": "555-555-0007",
        "ContactNumber2": "DIAL_PREFIX800-test-fax2",
        "EmailAddress": "test7@bvnk.co",
        "AddressLine1": "Address 1",
        "AddressLine2": "Address 2",
        "AddressLine3": "Address 3",
        "PostalCode": "1234",
        "Country": "AO",
        "ExchangeCustomer": false,
        "UserRole": "customer",
        "Merchant": "9400ae23-8fd6-4062-be6d-0c417051fc3b",
        "Customer": "ee99b544-6560-44b6-a68b-fc95300b0145",
        "CustomerType": "",
        "CustomerMetaID": "",
        "CustomFields": {
            "AddressCity": "Test",
            "AddressComplexName": "Test",
            "AddressProvince": "Test",
            "AddressStreetName": "Test",
            "AddressStreetNumber": "Test",
            "AddressSuburb": "Test",
            "AddressUnitNo": "Test",
            "City": "Test",
            "ComplexName": "Test",
            "ContactnumberMobile": "0800-test-mobile3",
            "DateOfBirth": "1900-01-01",
            "EthnicGroup": "Caucasian",
            "FullName": "Paul P. Coulson",
            "Gender": "Male",
            "HomeLanguage": "English",
            "IDType": "Driver License",
            "IDexipiry": "2020-01-01",
            "Initials": "P.C.",
            "MaritalStatus": "Single",
            "Nationality": "United Kingdom",
            "PreferredName": "Mr. Coulson",
            "Province": "Test",
            "StreetName": "Test",
            "StreetNumber": "Test",
            "Suburb": "Test",
            "Title": "MR",
            "UnitNo": "Test",
            "isLocalResident": "Y"
        }
    }, {
        "GivenName": "Customer1",
        "FamilyName": "Admin",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "19000101-1234-008",
        "ContactNumber1": "555-555-0009",
        "ContactNumber2": "555555-4328",
        "EmailAddress": "test8@bvnk.co",
        "AddressLine1": "Address 1",
        "AddressLine2": "Address 2",
        "AddressLine3": "Address 3",
        "PostalCode": "1234",
        "Country": "AO",
        "ExchangeCustomer": false,
        "UserRole": "customer_admin",
        "Merchant": "9400ae23-8fd6-4062-be6d-0c417051fc3b",
        "Customer": "ee99b544-6560-44b6-a68b-fc95300b0145",
        "CustomerType": "",
        "CustomerMetaID": "",
        "CustomFields": null
    }, {
        "GivenName": "Customer 1",
        "FamilyName": "Employee",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "19000101-1234-009",
        "ContactNumber1": "555-555-0010",
        "ContactNumber2": "555555-4397",
        "EmailAddress": "test9@bvnk.co",
        "AddressLine1": "Address 1",
        "AddressLine2": "Address 2",
        "AddressLine3": "Address 3",
        "PostalCode": "1234",
        "Country": "AO",
        "ExchangeCustomer": false,
        "UserRole": "customer_staff",
        "Merchant": "9400ae23-8fd6-4062-be6d-0c417051fc3b",
        "Customer": "ee99b544-6560-44b6-a68b-fc95300b0145",
        "CustomerType": "",
        "CustomerMetaID": "",
        "CustomFields": null
    }, {
        "GivenName": "Customer1 Subaccount",
        "FamilyName": "Director",
        "DateOfBirth": "1900-01-01",
        "IdentificationNumber": "19000101-1234-010",
        "ContactNumber1": "555-555-0012",
        "ContactNumber2": "DIAL_PREFIX800-test1-fax2",
        "EmailAddress": "test11@bvnk.co",
        "AddressLine1": "Address 1",
        "AddressLine2": "Address 2",
        "AddressLine3": "Address 3",
        "PostalCode": "1234",
        "Country": "AO",
        "ExchangeCustomer": false,
        "UserRole": "customer_subaccount",
        "Merchant": "9400ae23-8fd6-4062-be6d-0c417051fc3b",
        "Customer": "ee99b544-6560-44b6-a68b-fc95300b0145",
        "CustomerType": "",
        "CustomerMetaID": "",
        "CustomFields": null
    }]
}
```

> Error response:

```json
{
    "error": "error message"
}
```

This endpoint returns a collection of all users that the current user has permissions to view.

### HTTP Request

`GET https://demo.bvnk.co/account/user`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

This request requires no parameters.

## Get All Accounts (owned by current user)

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

This route will return all user's account details. If the account is a cryptocurrency account, the additional 
field `WalletAddress` will be returned. This is not a static value.

> Successful response:

```json
{
    "response": [
        {
            "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "bvnk,Alice",
            "AccountBalance": "3507.61865234375",
            "Overdraft": "0",
            "AvailableBalance": "3507.61865234375",
            "Type": "",
            "Currency": "usd",
            "CurrencyType": "",
            "Timestamp": 0
        },
        {
            "AccountNumber": "738e813a-6f8f-498c-9274-dfbae618147b",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "Test Merchant Ltd",
            "AccountBalance": "0",
            "Overdraft": "0",
            "AvailableBalance": "0",
            "Type": "",
            "Currency": "btc",
            "CurrencyType": "",
            "Timestamp": 0,
            "WalletAddress": "19kS6CczeNTxoKjNwubQGQFmyFQAwwopq"
        }
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

## Get All Accounts

```shell
curl -X GET \
  https://demo.bvnk.co/account/all \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: f1858b57-6bab-cf56-ba54-4044e4260481' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0'
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://demo.bvnk.co/account/all"

  req, _ := http.NewRequest("GET", url, nil)

  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "1de3852a-6bc9-31b4-528f-3e2260a1481b")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/all")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "23775726-4bfe-9b5e-4e7c-f080b0cbaff1")
  .asString();
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://demo.bvnk.co/account/all");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "3c992704-078e-03bd-9488-dbd938f7e86d");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/all"

headers = {
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "15e5a727-6e94-7ada-0233-1abc37938c02"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

This endpoint returns a collection of all accounts that the current user has permissions to view. If an account is a cryptocurrency account, the additional 
field `WalletAddress` will be returned. This is not a static value.

> Successful response:

```json
{
    "response": [
        {
            "AccountNumber": "9bd356cd-1c54-498d-b6b5-26a8d0a17940",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "bvnk,Alice",
            "AccountBalance": "3507.61865234375",
            "Overdraft": "0",
            "AvailableBalance": "3507.61865234375",
            "Type": "",
            "Currency": "usd",
            "CurrencyType": "",
            "Timestamp": 0
        },
        {
            "AccountNumber": "738e813a-6f8f-498c-9274-dfbae618147b",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "Test Merchant Ltd",
            "AccountBalance": "0",
            "Overdraft": "0",
            "AvailableBalance": "0",
            "Type": "",
            "Currency": "btc",
            "CurrencyType": "",
            "Timestamp": 0,
            "WalletAddress": "19kS6CczeNTxoKjNwubQGQFmyFQAwwopq"
        }
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

`GET https://demo.bvnk.co/account/all`

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
        "AccountHolderName": "bvnk,Alice",
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
        "AccountHolderName": "bvnk,Alice",
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

## Get Holding Accounts

```shell
curl -X GET \
  https://demo.bvnk.co/account/holding \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: aaa778a1-a48f-24fd-f3b3-77f1ee162675'
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://demo.bvnk.co/account/holding"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "c9651785-bc4f-6038-9602-f1fada6cf3cf")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/holding")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "dc489c31-9aee-a909-d21c-3c7e84544eca")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/holding',
  headers:
   { 'Postman-Token': 'eea96f45-50bb-2ba0-4aed-11a9ea1438c8',
     'Cache-Control': 'no-cache' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://demo.bvnk.co/account/holding"

headers = {
    'Cache-Control': "no-cache",
    'Postman-Token': "c5c7cde8-32b7-c902-9e41-7de6a1e4a6ac"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": [
        {
            "AccountNumber": "1a63e0d8-e20c-4b5b-b0ca-9233c4bdb923",
            "BankNumber": "a0299975-b8e2-4358-8f1a-911ee12dbaac",
            "AccountHolderName": "BVNK,BVNK",
            "AccountBalance": "2.5977299213409424",
            "Overdraft": "0",
            "AvailableBalance": "2.5977299213409424",
            "Type": "",
            "Currency": "bct",
            "CurrencyType": "",
            "Timestamp": 0,
            "WalletAddress": "mrsZbMkiJYiPfsDQm5kgWdtg2B8zAtBLt3"
        },
        ...
```

> Error response:

```json
{
    "error": "Error retrieving auth headers"
}
```

This endpoint returns a JSON array of all holding account details including balances. This endpoint requires basic authentication. 

### HTTP Request

`GET https://demo.bvnk.co/account/holding`

### Headers

`X-Auth-Token: {auth token}`
`Authorization: Basic {basic auth}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------

This request requires no parameters.

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

## Export seed with mnemonic

```shell
curl -X GET \
  https://demo.bvnk.co/account/seed/7d05ab7f-0caf-4fc5-9381-d2f408575902 \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 8da0fb0a-214c-26e0-37eb-d919e566eb0a' \
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

	url := "https://demo.bvnk.co/account/seed/7d05ab7f-0caf-4fc5-9381-d2f408575902"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "1acc28eb-ad0b-b835-e958-225eee991152")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.get("https://demo.bvnk.co/account/seed/7d05ab7f-0caf-4fc5-9381-d2f408575902")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "ee2cd9fb-a165-40c7-95af-c05d4d5f8117")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "78f5b49f-3ddc-2420-491b-160f8b5595a2")
  .asString();
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://demo.bvnk.co/account/seed/7d05ab7f-0caf-4fc5-9381-d2f408575902',
  headers: 
   { 'Postman-Token': '84f78466-315c-3a64-5d56-056db5dcb668',
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

url = "https://demo.bvnk.co/account/seed/7d05ab7f-0caf-4fc5-9381-d2f408575902"

headers = {
    'Content-Type': "application/json",
    'X-Auth-Token': "ee2cd9fb-a165-40c7-95af-c05d4d5f8117",
    'Cache-Control': "no-cache",
    'Postman-Token': "4ababbca-5e84-1a7b-9c05-a658ed53b4e7"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

> Successful response:

```json
{
    "response": {
        "Seed": "fae26ee96db0db2fb77475b0ed0e96a47efaeeab20c021b432e10a1743342e3706127fa07b8f70fceefbeaa58e00aada2594d5af235af428c6c8013c126ad8tb",
        "Mnemonic": "miracle hello television custom apple asthma loud cloud middle bundle many retire"
    }
}
```

> Error response:

```json
{
    "error": "Wallet not found"
}
```

This endpoint will return a seed for a given cryptocurrency wallet linked to an account. 

<aside>This route is only applicable to cryptocurrency accounts.</aside>

### HTTP Request

`GET https://demo.bvnk.co/account/seed/{account}`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountNumber | true | Account number to get seed for. This account must be a cryptocurrency account.


