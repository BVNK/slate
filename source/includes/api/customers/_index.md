# Customers

## Create Individual Customer

```shell
curl -X POST \
  https://demo.bvnk.co/account/single \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: d4035df3-2d1e-b376-e5c1-efb6e7752d34' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderGivenName=Test \
  -F AccountHolderFamilyName=User1 \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=19000101-1234-005 \
  -F AccountHolderContactNumber1=555-555-0017 \
  -F AccountHolderContactNumber2=0800-test-fax22 \
  -F AccountHolderEmailAddress=test17@bvnk.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderCountry=AO \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderPassword=password \
  -F CustomerTag=cardmanager \
  -F CustomerID=9691f2de-f3e4-4a84-bf89-a07c0de69fac
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

  url := "https://demo.bvnk.co/account/single"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-005\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest17@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69fac\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "00f865bf-9413-3708-bd1e-7aeab264af7d")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/single")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "2bd71bdb-9705-b0f9-21bf-7fc4afb7c684")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-005\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest17@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69fac\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderGivenName", "Test");
data.append("AccountHolderFamilyName", "User1");
data.append("AccountHolderDateOfBirth", "1900-01-01");
data.append("AccountHolderIdentificationNumber", "19000101-1234-005");
data.append("AccountHolderContactNumber1", "555-555-0017");
data.append("AccountHolderContactNumber2", "0800-test-fax22");
data.append("AccountHolderEmailAddress", "test17@bvnk.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderCountry", "AO");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderPassword", "password");
data.append("CustomerTag", "cardmanager");
data.append("CustomerID", "9691f2de-f3e4-4a84-bf89-a07c0de69fac");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/single");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "d69142f5-d471-0440-a5e6-fb4b795f8330");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/single"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-005\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0017\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest17@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69fac\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "365110b7-0ba4-cb8c-ebea-5c6e098a60ed"
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
    "error": "error message"
}
```

This endpoint creates an individual customer for a merchant. The response is the account number for the new customer account. The individual customer is a person (not business) and therefore does not have the extra KYC requirements besides the standard KYC for all BVNK users.

### HTTP Request

`POST https://demo.bvnk.co/account/single`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
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
AccountHolderCountry | true | Valid ISO2 code for country. List of countries can be retrieved from `/countries`.
AccountHolderPassword | true | Password for the users account
CustomerTag | true | A tag to identify the merchant's business product
CustomerID | true | A unique ID provided by the merchant to identify the customer in their own system

## Create Merchant Customer

```shell
curl -X POST \
  https://demo.bvnk.co/account/customer \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 80d75c8d-3c58-c896-c594-09058605b3fd' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F DirectorGivenName=Customer \
  -F DirectorFamilyName=Director \
  -F DirectorDateOfBirth=1900-01-01 \
  -F DirectorIdentificationNumber=19000101-1234-007 \
  -F DirectorPassword=password \
  -F DirectorEmailAddress=test7@bvnk.co \
  -F DirectorContactNumber1=555-555-0007 \
  -F DirectorContactNumber2=0800-test-fax2 \
  -F DirectorContactnumberMobile=555-555-0008 \
  -F 'DirectorAddressLine1=Address 1' \
  -F 'DirectorAddressLine2=Address 2' \
  -F 'DirectorAddressLine3=Address 3' \
  -F DirectorPostalCode=1234 \
  -F DirectorCountry=AO \
  -F 'CustomerName=CardManager Customer One' \
  -F CustomerType=master \
  -F CustomerTag=cardmanager \
  -F CustomerID=9691f2de-f3e4-4a84-bf89-a07c0de69f58 \
  -F CustomerMerchant=e46d3ff7-6bfc-437e-ab2b-ceb875537b22 \
  -F CustomerAddressCity=Test \
  -F 'CustomerAddressCountry=United States' \
  -F 'CustomerAddressLine1=Office 1B' \
  -F 'CustomerAddressLine2=Office Road 1B' \
  -F 'CustomerAddressLine3=Office Road 1C' \
  -F CustomerAddressPostalCode=12345 \
  -F CustomerAddressProvince=Test \
  -F CustomerAddressStreetName=Test \
  -F CustomerAddressStreetNumber=Test \
  -F CustomerBusinessSector=Transportation \
  -F CustomerContactEmail=test10@bvnk.co \
  -F CustomerContactFamilyName=Doe \
  -F CustomerContactFax=0800-test-fax2 \
  -F CustomerContactGivenName=John \
  -F CustomerContactPhone=555-555-0011 \
  -F CustomerCorrespondenceType=Email \
  -F 'CustomerDescription=The first Card Manager Customer' \
  -F CustomerAccountCurrency=usd \
  -F CustomerLogo= \
  -F CustomerRegistrationDate=2017-02-09 \
  -F CustomerRegistrationNumber=thisisaregistrationnumber \
  -F CustomerStatementDelivery=Email \
  -F CustomerStatementFrequency=Annually \
  -F CustomerTaxNumber=some_tax_number \
  -F CustomerWebsite=uber.com
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

  url := "https://demo.bvnk.co/account/customer"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorGivenName\"\r\n\r\nCustomer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorFamilyName\"\r\n\r\nDirector\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorIdentificationNumber\"\r\n\r\n19000101-1234-007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorEmailAddress\"\r\n\r\ntest7@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber1\"\r\n\r\n555-555-0007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber2\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactnumberMobile\"\r\n\r\n555-555-0008\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nmaster\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCity\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressProvince\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetNumber\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest10@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0011\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationNumber\"\r\n\r\nthisisaregistrationnumber\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTaxNumber\"\r\n\r\nsome_tax_number\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "495148d8-6c39-b375-7f3e-c30671c7f6cb")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/customer")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "a3678804-5067-bc9f-83af-c05925e2f665")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorGivenName\"\r\n\r\nCustomer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorFamilyName\"\r\n\r\nDirector\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorIdentificationNumber\"\r\n\r\n19000101-1234-007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorEmailAddress\"\r\n\r\ntest7@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber1\"\r\n\r\n555-555-0007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber2\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactnumberMobile\"\r\n\r\n555-555-0008\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nmaster\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCity\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressProvince\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetNumber\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest10@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0011\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationNumber\"\r\n\r\nthisisaregistrationnumber\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTaxNumber\"\r\n\r\nsome_tax_number\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("DirectorGivenName", "Customer");
data.append("DirectorFamilyName", "Director");
data.append("DirectorDateOfBirth", "1900-01-01");
data.append("DirectorIdentificationNumber", "19000101-1234-007");
data.append("DirectorPassword", "password");
data.append("DirectorEmailAddress", "test7@bvnk.co");
data.append("DirectorContactNumber1", "555-555-0007");
data.append("DirectorContactNumber2", "0800-test-fax2");
data.append("DirectorContactnumberMobile", "555-555-0008");
data.append("DirectorAddressLine1", "Address 1");
data.append("DirectorAddressLine2", "Address 2");
data.append("DirectorAddressLine3", "Address 3");
data.append("DirectorPostalCode", "1234");
data.append("DirectorCountry", "AO");
data.append("CustomerName", "CardManager Customer One");
data.append("CustomerType", "master");
data.append("CustomerTag", "cardmanager");
data.append("CustomerID", "9691f2de-f3e4-4a84-bf89-a07c0de69f58");
data.append("CustomerMerchant", "e46d3ff7-6bfc-437e-ab2b-ceb875537b22");
data.append("CustomerAddressCity", "Test");
data.append("CustomerAddressCountry", "United States");
data.append("CustomerAddressLine1", "Office 1B");
data.append("CustomerAddressLine2", "Office Road 1B");
data.append("CustomerAddressLine3", "Office Road 1C");
data.append("CustomerAddressPostalCode", "12345");
data.append("CustomerAddressProvince", "Test");
data.append("CustomerAddressStreetName", "Test");
data.append("CustomerAddressStreetNumber", "Test");
data.append("CustomerBusinessSector", "Transportation");
data.append("CustomerContactEmail", "test10@bvnk.co");
data.append("CustomerContactFamilyName", "Doe");
data.append("CustomerContactFax", "0800-test-fax2");
data.append("CustomerContactGivenName", "John");
data.append("CustomerContactPhone", "555-555-0011");
data.append("CustomerCorrespondenceType", "Email");
data.append("CustomerDescription", "The first Card Manager Customer");
data.append("CustomerAccountCurrency", "usd");
data.append("CustomerLogo", "");
data.append("CustomerRegistrationDate", "2017-02-09");
data.append("CustomerRegistrationNumber", "thisisaregistrationnumber");
data.append("CustomerStatementDelivery", "Email");
data.append("CustomerStatementFrequency", "Annually");
data.append("CustomerTaxNumber", "some_tax_number");
data.append("CustomerWebsite", "uber.com");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/customer");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "0a32f06d-0842-373d-498a-9c6aaae25784");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/customer"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorGivenName\"\r\n\r\nCustomer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorFamilyName\"\r\n\r\nDirector\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorIdentificationNumber\"\r\n\r\n19000101-1234-007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorEmailAddress\"\r\n\r\ntest7@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber1\"\r\n\r\n555-555-0007\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactNumber2\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorContactnumberMobile\"\r\n\r\n555-555-0008\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"DirectorCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nmaster\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCity\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressProvince\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressStreetNumber\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest10@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0011\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationNumber\"\r\n\r\nthisisaregistrationnumber\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTaxNumber\"\r\n\r\nsome_tax_number\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "fb208070-36dd-eb61-c4ef-9512e5847330"
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
    "error": "error message"
}
```

This endpoint creates a business customer for a merchant. The customer may be the final customer or it may be a reseller with the ability to create subaccounts for its final customers. The response is the account number for the new customer account. This customer requires additional KYC information (FICA details) as opposed to the Individual Customer

### HTTP Request

`POST https://demo.bvnk.co/account/customer`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
DirectorGivenName | true | 
DirectorFamilyName | true | 
DirectorDateOfBirth | true | 
DirectorIdentificationNumber | true | 
DirectorPassword | true | 
DirectorEmailAddress | true | 
DirectorContactNumber1 | true | 
DirectorContactNumber2 | true | 
DirectorContactnumberMobile | true | 
DirectorAddressLine1 | true | 
DirectorAddressLine2 | true | 
DirectorAddressLine3 | true | 
DirectorPostalCode | true | 
DirectorCountry | true | 
CustomerName | true | 
CustomerType | true | single or master (determines if customer can have subaccounts)
CustomerTag | true | A tag to identify the merchant's business product
CustomerID | true | A unique ID provided by the merchant to identify the customer in their own system
CustomerMerchant | true | 
CustomerAddressCity | true | 
CustomerAddressCountry | true | 
CustomerAddressLine1 | true | 
CustomerAddressLine2 | true | 
CustomerAddressLine3 | true | 
CustomerAddressPostalCode | true | 
CustomerAddressProvince | true | 
CustomerAddressStreetName | true | 
CustomerAddressStreetNumber | true | 
CustomerBusinessSector | true | 
CustomerContactEmail | true | 
CustomerContactFamilyName | true | 
CustomerContactFax | true | 
CustomerContactGivenName | true | 
CustomerContactPhone | true | 
CustomerCorrespondenceType | true | 
CustomerDescription | true | 
CustomerAccountCurrency | true | 
CustomerLogo | true | 
CustomerRegistrationDate | true | 
CustomerRegistrationNumber | true | 
CustomerStatementDelivery | true | 
CustomerStatementFrequency | true | 
CustomerTaxNumber | true | 
CustomerWebsite | true | 


## Create Individual Subaccount

```shell
curl -X POST \
  https://demo.bvnk.co/account/cardholder \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: e7c09178-2294-fb0e-7ab1-abd4dd39fcc1' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderGivenName=Test \
  -F AccountHolderFamilyName=User1 \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=19000101-1234-009 \
  -F AccountHolderContactNumber1=555-555-0015 \
  -F AccountHolderContactNumber2=0800-test-fax22 \
  -F AccountHolderEmailAddress=test13@bvnk.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderCountry=AO \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderPassword=password \
  -F 'CustomerName=CardManager Company Customer Three' \
  -F 'CustomerDescription=The third Card Manager Customer' \
  -F AccountCurrency=usd \
  -F CustomerType=subaccount \
  -F CustomerTag=cardmanager \
  -F CustomerID=9691f2de-f3e4-4a84-bf89-a07c0de69f58 \
  -F Unique_CompanyCardNumber=cardnumber3 \
  -F 'CustomerIDType=Driver License' \
  -F CustomerIDexipiry=2020-01-01 \
  -F CustomerGender=Female \
  -F 'HollardAccountPolicy=hollard account policy' \
  -F CustomerBusinessSector=Transportation
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

  url := "https://demo.bvnk.co/account/cardholder"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0015\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest13@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer Three\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe third Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Unique_CompanyCardNumber\"\r\n\r\ncardnumber3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDType\"\r\n\r\nDriver License\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDexipiry\"\r\n\r\n2020-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerGender\"\r\n\r\nFemale\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"HollardAccountPolicy\"\r\n\r\nhollard account policy\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "1d12d380-5e2d-aa4a-9720-e9b57b87a4ce")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/cardholder")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "bf4fc55f-5f3b-9814-560f-5a372d38d6f1")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0015\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest13@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer Three\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe third Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Unique_CompanyCardNumber\"\r\n\r\ncardnumber3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDType\"\r\n\r\nDriver License\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDexipiry\"\r\n\r\n2020-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerGender\"\r\n\r\nFemale\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"HollardAccountPolicy\"\r\n\r\nhollard account policy\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderGivenName", "Test");
data.append("AccountHolderFamilyName", "User1");
data.append("AccountHolderDateOfBirth", "1900-01-01");
data.append("AccountHolderIdentificationNumber", "19000101-1234-009");
data.append("AccountHolderContactNumber1", "555-555-0015");
data.append("AccountHolderContactNumber2", "0800-test-fax22");
data.append("AccountHolderEmailAddress", "test13@bvnk.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderCountry", "AO");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderPassword", "password");
data.append("CustomerName", "CardManager Company Customer Three");
data.append("CustomerDescription", "The third Card Manager Customer");
data.append("AccountCurrency", "usd");
data.append("CustomerType", "subaccount");
data.append("CustomerTag", "cardmanager");
data.append("CustomerID", "9691f2de-f3e4-4a84-bf89-a07c0de69f58");
data.append("Unique_CompanyCardNumber", "cardnumber3");
data.append("CustomerIDType", "Driver License");
data.append("CustomerIDexipiry", "2020-01-01");
data.append("CustomerGender", "Female");
data.append("HollardAccountPolicy", "hollard account policy");
data.append("CustomerBusinessSector", "Transportation");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/cardholder");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "9c73b12d-9e52-bd84-7c39-dd03d0f26609");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/cardholder"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nTest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nUser1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-009\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0015\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test-fax22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest13@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer Three\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe third Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"Unique_CompanyCardNumber\"\r\n\r\ncardnumber3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDType\"\r\n\r\nDriver License\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerIDexipiry\"\r\n\r\n2020-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerGender\"\r\n\r\nFemale\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"HollardAccountPolicy\"\r\n\r\nhollard account policy\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "0fa88cd9-c3ae-21ac-a3b7-bb4b4b095e97"
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
    "error": "error message"
}
```

This endpoint creates a subaccount under a merchant's customer, meant for an individual (not company) and therefore, without the additional KYC/FICA requirements. The response is the account number for the new subaccount. 

### HTTP Request

`POST https://demo.bvnk.co/account/cardholder`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountHolderGivenName | true | 
AccountHolderFamilyName | true | 
AccountHolderDateOfBirth | true | 
AccountHolderIdentificationNumber | true | 
AccountHolderContactNumber1 | true | 
AccountHolderContactNumber2 | true | 
AccountHolderEmailAddress | true | 
AccountHolderAddressLine1 | true | 
AccountHolderAddressLine2 | true | 
AccountHolderAddressLine3 | true | 
AccountHolderCountry | true | 
AccountHolderPostalCode | true | 
AccountHolderPassword | true | 
CustomerName | true | 
CustomerDescription | true | 
AccountCurrency | true | 
CustomerType | true | 
CustomerTag | true | 
CustomerID | true | 
Unique_CompanyCardNumber | true | 
CustomerIDType | true | 
CustomerIDexipiry | true | 
CustomerGender | true | 
HollardAccountPolicy | true | 
CustomerBusinessSector | true | 

## Create Enterprise Subaccount

```shell
curl -X POST \
  https://demo.bvnk.co/account/subaccount \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: fba6e25b-878b-e546-ac91-f287b0ef7046' \
  -H 'X-Auth-Token: 8400a09e-7676-4aa3-bce0-57a216b7f1b0' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderIdentificationNumber=19000101-1234-010 \
  -F AccountHolderContactNumber1=555-555-0012 \
  -F AccountHolderContactNumber2=0800-test1-fax2 \
  -F AccountHolderEmailAddress=test11@bvnk.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderCountry=AO \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderPassword=password \
  -F 'CustomerName=CardManager Company Customer One' \
  -F 'CustomerDescription=The first Card Manager Customer' \
  -F CustomerContactGivenName=John \
  -F CustomerContactFamilyName=Doe \
  -F 'CustomerAddressLine1=Office 1B' \
  -F 'CustomerAddressLine2=Office Road 1B' \
  -F 'CustomerAddressLine3=Office Road 1C' \
  -F 'CustomerAddressCountry=United States' \
  -F CustomerWebsite=uber.com \
  -F CustomerContactPhone=555-555-0014 \
  -F CustomerContactFax=0800-test-fax3 \
  -F CustomerContactEmail=test12@bvnk.co \
  -F CustomerLogo= \
  -F AccountCurrency=usd \
  -F CustomerType=subaccount \
  -F CustomerTag=cardmanager \
  -F CustomerID=9691f2de-f3e4-4a84-bf89-a07c0de69f58 \
  -F CustomerMerchant=e46d3ff7-6bfc-437e-ab2b-ceb875537b22 \
  -F 'CustomerAddressCountry=United States' \
  -F CustomerAddressPostalCode=12345 \
  -F CustomerBusinessSector=Transportation \
  -F CustomerWebsite=uber.com \
  -F CustomerContactPhone=555-555-0014 \
  -F CustomerContactFax=0800-test-fax3 \
  -F CustomerContactEmail=test12@bvnk.co \
  -F CustomerRegistrationDate=2017-02-09 \
  -F CustomerStatementDelivery=Email \
  -F CustomerCorrespondenceType=Email \
  -F CustomerStatementFrequency=Annually
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

  url := "https://demo.bvnk.co/account/subaccount"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-010\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0012\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test1-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest11@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "c7b6d716-36ed-70bc-9f69-7e4b087673cd")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/subaccount")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "dbd1c595-500d-233a-0bc8-41599e973a97")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-010\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0012\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test1-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest11@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderIdentificationNumber", "19000101-1234-010");
data.append("AccountHolderContactNumber1", "555-555-0012");
data.append("AccountHolderContactNumber2", "0800-test1-fax2");
data.append("AccountHolderEmailAddress", "test11@bvnk.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderCountry", "AO");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderPassword", "password");
data.append("CustomerName", "CardManager Company Customer One");
data.append("CustomerDescription", "The first Card Manager Customer");
data.append("CustomerContactGivenName", "John");
data.append("CustomerContactFamilyName", "Doe");
data.append("CustomerAddressLine1", "Office 1B");
data.append("CustomerAddressLine2", "Office Road 1B");
data.append("CustomerAddressLine3", "Office Road 1C");
data.append("CustomerAddressCountry", "United States");
data.append("CustomerWebsite", "uber.com");
data.append("CustomerContactPhone", "555-555-0014");
data.append("CustomerContactFax", "0800-test-fax3");
data.append("CustomerContactEmail", "test12@bvnk.co");
data.append("CustomerLogo", "");
data.append("AccountCurrency", "usd");
data.append("CustomerType", "subaccount");
data.append("CustomerTag", "cardmanager");
data.append("CustomerID", "9691f2de-f3e4-4a84-bf89-a07c0de69f58");
data.append("CustomerMerchant", "e46d3ff7-6bfc-437e-ab2b-ceb875537b22");
data.append("CustomerAddressCountry", "United States");
data.append("CustomerAddressPostalCode", "12345");
data.append("CustomerBusinessSector", "Transportation");
data.append("CustomerWebsite", "uber.com");
data.append("CustomerContactPhone", "555-555-0014");
data.append("CustomerContactFax", "0800-test-fax3");
data.append("CustomerContactEmail", "test12@bvnk.co");
data.append("CustomerRegistrationDate", "2017-02-09");
data.append("CustomerStatementDelivery", "Email");
data.append("CustomerCorrespondenceType", "Email");
data.append("CustomerStatementFrequency", "Annually");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/subaccount");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "d54c54fa-6ea5-c7a6-ce81-9db3cf3fb591");

xhr.send(data);

```

```python
import requests

url = "https://demo.bvnk.co/account/subaccount"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-010\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0012\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n0800-test1-fax2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest11@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerName\"\r\n\r\nCardManager Company Customer One\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerDescription\"\r\n\r\nThe first Card Manager Customer\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactGivenName\"\r\n\r\nJohn\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFamilyName\"\r\n\r\nDoe\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine1\"\r\n\r\nOffice 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine2\"\r\n\r\nOffice Road 1B\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressLine3\"\r\n\r\nOffice Road 1C\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerLogo\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountCurrency\"\r\n\r\nusd\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerType\"\r\n\r\nsubaccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerTag\"\r\n\r\ncardmanager\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerID\"\r\n\r\n9691f2de-f3e4-4a84-bf89-a07c0de69f58\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerMerchant\"\r\n\r\ne46d3ff7-6bfc-437e-ab2b-ceb875537b22\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressCountry\"\r\n\r\nUnited States\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerAddressPostalCode\"\r\n\r\n12345\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerBusinessSector\"\r\n\r\nTransportation\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerWebsite\"\r\n\r\nuber.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactPhone\"\r\n\r\n555-555-0014\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactFax\"\r\n\r\n0800-test-fax3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerContactEmail\"\r\n\r\ntest12@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerRegistrationDate\"\r\n\r\n2017-02-09\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementDelivery\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerCorrespondenceType\"\r\n\r\nEmail\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"CustomerStatementFrequency\"\r\n\r\nAnnually\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "8400a09e-7676-4aa3-bce0-57a216b7f1b0",
    'Cache-Control': "no-cache",
    'Postman-Token': "7622abe6-04dd-092e-12f2-4bde03ddfd8d"
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
    "error": "error message"
}
```

This endpoint creates a subaccount under a merchant's customer, meant for a company, requiring additional KYC/FICA information. The response is the account number for the new subaccount. 

### HTTP Request

`POST https://demo.bvnk.co/account/subaccount`

### Headers

`X-Auth-Token: {auth token}`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ----------
AccountHolderIdentificationNumber | true | 
AccountHolderContactNumber1 | true | 
AccountHolderContactNumber2 | true | 
AccountHolderEmailAddress | true | 
AccountHolderAddressLine1 | true | 
AccountHolderAddressLine2 | true | 
AccountHolderAddressLine3 | true | 
AccountHolderCountry | true | 
AccountHolderPostalCode | true | 
AccountHolderPassword | true | 
CustomerName | true | 
CustomerDescription | true | 
CustomerContactGivenName | true | 
CustomerContactFamilyName | true | 
CustomerAddressLine1 | true | 
CustomerAddressLine2 | true | 
CustomerAddressLine3 | true | 
CustomerAddressCountry | true | 
CustomerWebsite | true | 
CustomerContactPhone | true | 
CustomerContactFax | true | 
CustomerContactEmail | true | 
CustomerLogo | true | 
AccountCurrency | true | 
CustomerType | true | 
CustomerTag | true | 
CustomerID | true | 
CustomerMerchant | true | 
CustomerAddressCountry | true | 
CustomerAddressPostalCode | true | 
CustomerBusinessSector | true | 
CustomerWebsite | true | 
CustomerContactPhone | true | 
CustomerContactFax | true | 
CustomerContactEmail | true | 
CustomerRegistrationDate | true | 
CustomerStatementDelivery | true | 
CustomerCorrespondenceType | true | 
CustomerStatementFrequency | true | 