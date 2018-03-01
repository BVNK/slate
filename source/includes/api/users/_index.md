# Users

## User Signup

> To signup to BVNK:

```shell
curl -X POST \
  https://demo.bvnk.co/account/signup \
  -H 'Authorization: Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=' \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: a7d75f11-876a-9458-b195-43c967d62111' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderGivenName=Debug \
  -F AccountHolderFamilyName=Account \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=400000-0000-001 \
  -F 'AccountHolderContactNumber1=(558) 555-42381' \
  -F AccountHolderEmailAddress=alice@bankai.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderPassword=password \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderCountry=GB
```

```python
import requests

url = "https://demo.bvnk.co/account/signup"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Authorization': "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=",
    'Cache-Control': "no-cache",
    'Postman-Token': "becd926e-c9bd-0d37-dde3-95d94b649f04"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
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

  url := "https://demo.bvnk.co/account/signup"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "98be2b0b-b895-e1e4-22e2-d2d26aa21c37")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/account/signup")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "6fe15eac-7e64-b093-b04a-30ae914d8031")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderGivenName", "Debug");
data.append("AccountHolderFamilyName", "Account");
data.append("AccountHolderDateOfBirth", "1900-01-01");
data.append("AccountHolderIdentificationNumber", "400000-0000-001");
data.append("AccountHolderContactNumber1", "(558) 555-42381");
data.append("AccountHolderEmailAddress", "alice@bankai.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderPassword", "password");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderCountry", "GB");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/signup");
xhr.setRequestHeader("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "7c40dcd5-3eef-f583-e3e6-f99320a9e796");

xhr.send(data);
```

Users act as account holders and need to be created as the first action. All accounts need to be linked to users, and Know Your Customer requirements centre around users. Country must be valid ISO2 code, a list of valid countries and their codes can be retrieved through `GET /countries`. The signup request should be done via a BVNK interface (web or mobile app) because it also uses HTTP authentication as a new customer would not have an account.

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

`POST https://demo.bvnk.co/account/signup`

### Headers

`X-Auth-Token: {auth token}`

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
AccountHolderCountry | true | Valid ISO2 code for country. List of countries can be retrieved from `/countries`.
AccountHolderPassword | true | Password for the users account

<aside class="notice">
The password sent through on this call will used along with the <code>AccountHolderIdentificationNumber</code> to generate authentication credentials.
</aside>


## Admin User creation

> To create a new administrator:

```shell
curl -X POST \
  https://demo.bvnk.co/account/user \
  -H 'Authorization: Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=' \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: a7d75f11-876a-9458-b195-43c967d62111' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderGivenName=Debug \
  -F AccountHolderFamilyName=Account \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=400000-0000-001 \
  -F 'AccountHolderContactNumber1=(558) 555-42381' \
  -F AccountHolderEmailAddress=alice@bankai.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderPassword=password \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderCountry=GB
```

```python
import requests

url = "https://demo.bvnk.co/account/user"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Authorization': "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=",
    'Cache-Control': "no-cache",
    'Postman-Token': "becd926e-c9bd-0d37-dde3-95d94b649f04"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
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

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=")
	req.Header.Add("Cache-Control", "no-cache")
	req.Header.Add("Postman-Token", "98be2b0b-b895-e1e4-22e2-d2d26aa21c37")

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
  .header("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "6fe15eac-7e64-b093-b04a-30ae914d8031")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderGivenName", "Debug");
data.append("AccountHolderFamilyName", "Account");
data.append("AccountHolderDateOfBirth", "1900-01-01");
data.append("AccountHolderIdentificationNumber", "400000-0000-001");
data.append("AccountHolderContactNumber1", "(558) 555-42381");
data.append("AccountHolderEmailAddress", "alice@bankai.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderPassword", "password");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderCountry", "GB");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/account/user");
xhr.setRequestHeader("Authorization", "Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "7c40dcd5-3eef-f583-e3e6-f99320a9e796");

xhr.send(data);
```

While all accounts must be linked to users and Know Your Customer requirements center around users, not all users need to have an account. At BVNK, every user has a role, including Administrators, Merchants, Merchant Customers and regular account holders. This endpoint allows Administrators that aren't BVNK users to create users through HTTP authentication. This is necessary for new installations where no user exists and the first administrator must be created. It is therefore not an endpoint to be used often.

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

### Headers

`Authorization: {Basic Basic YnZuazpldml0YWJsZS1jYXVjdXMtZm9yZXNhdy1wcmVzc21hbi1mbGF0Y2FyLWZpZXJ5LW9mZnNob290LWhvdXI=}`

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
AccountHolderCountry | true | Valid ISO2 code for country. List of countries can be retrieved from `/countries`.
AccountHolderPassword | true | Password for the users account

<aside class="notice">
The password sent through on this call will used along with the <code>AccountHolderIdentificationNumber</code> to generate authentication credentials.
</aside>

## IAM User creation

> To create a new IAM User:

```shell
curl -X POST \
  https://demo.bvnk.co/iam/user \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: a4b4a190-c876-0461-302e-f1de16ca1c3c' \
  -H 'X-Auth-Token: 256f8024-2271-445c-88f2-6cdeed30531b' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F AccountHolderGivenName=PayDNA \
  -F 'AccountHolderFamilyName=Admin 1' \
  -F AccountHolderDateOfBirth=1900-01-01 \
  -F AccountHolderIdentificationNumber=19000101-1234-003 \
  -F AccountHolderContactNumber1=555-555-0003 \
  -F 'AccountHolderContactNumber2=(555) 555-4366' \
  -F AccountHolderEmailAddress=test3@bvnk.co \
  -F 'AccountHolderAddressLine1=Address 1' \
  -F 'AccountHolderAddressLine2=Address 2' \
  -F 'AccountHolderAddressLine3=Address 3' \
  -F AccountHolderCountry=GB \
  -F AccountHolderPostalCode=1234 \
  -F AccountHolderPassword=password \
  -F UserType=admin
```

```python
import requests

url = "https://demo.bvnk.co/iam/user"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nPayDNA\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAdmin 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n(555) 555-4366\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest3@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserType\"\r\n\r\nadmin\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'Content-Type': "application/json",
    'X-Auth-Token': "256f8024-2271-445c-88f2-6cdeed30531b",
    'Cache-Control': "no-cache",
    'Postman-Token': "1126f433-dedb-24e8-512d-af111bb25697"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
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

  url := "https://demo.bvnk.co/iam/user"

  payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nPayDNA\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAdmin 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n(555) 555-4366\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest3@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserType\"\r\n\r\nadmin\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

  req, _ := http.NewRequest("POST", url, payload)

  req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  req.Header.Add("Cache-Control", "no-cache")
  req.Header.Add("Postman-Token", "8348a26e-3b5c-92bd-668f-d08974fa4f10")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

```java
HttpResponse<String> response = Unirest.post("https://demo.bvnk.co/iam/user")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .header("Content-Type", "application/json")
  .header("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0")
  .header("Cache-Control", "no-cache")
  .header("Postman-Token", "4590f99d-00e2-a1d6-0f7b-0eea1c028d0a")
  .body("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nPayDNA\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAdmin 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n19000101-1234-003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n555-555-0003\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber2\"\r\n\r\n(555) 555-4366\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\ntest3@bvnk.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nAO\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"UserType\"\r\n\r\nadmin\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")
  .asString();
```

```javascript
var data = new FormData();
data.append("AccountHolderGivenName", "PayDNA");
data.append("AccountHolderFamilyName", "Admin 1");
data.append("AccountHolderDateOfBirth", "1900-01-01");
data.append("AccountHolderIdentificationNumber", "19000101-1234-003");
data.append("AccountHolderContactNumber1", "555-555-0003");
data.append("AccountHolderContactNumber2", "(555) 555-4366");
data.append("AccountHolderEmailAddress", "test3@bvnk.co");
data.append("AccountHolderAddressLine1", "Address 1");
data.append("AccountHolderAddressLine2", "Address 2");
data.append("AccountHolderAddressLine3", "Address 3");
data.append("AccountHolderCountry", "AO");
data.append("AccountHolderPostalCode", "1234");
data.append("AccountHolderPassword", "password");
data.append("UserType", "admin");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://demo.bvnk.co/iam/user");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("X-Auth-Token", "8400a09e-7676-4aa3-bce0-57a216b7f1b0");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "989b404a-b05e-c2da-83a1-c375d137f6c9");

xhr.send(data);
```

This endpoint allows organizations to create user accounts for their own staff or customers, and administrators users to create other administrators and users. Users created this way are added to IAM groups according to the role of the user creating them. For example, a user created by a merchant or merchant's customer has permissions only on the company's resources. An administrator created by a BVNK admin will have the same roles as that admin, and a simple user created by the same admin will have permissions only over their own resources.

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

`POST https://demo.bvnk.co/iam/user`

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
AccountHolderCountry | true | Valid ISO2 code for country. List of countries can be retrieved from `/countries`.
AccountHolderPassword | true | Password for the users account
UserType | true | One of admin, staff, user

<aside class="notice">
The password sent through on this call will used along with the <code>AccountHolderIdentificationNumber</code> to generate authentication credentials.
</aside>
