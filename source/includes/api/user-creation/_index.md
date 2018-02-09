# User creation

> To create a new user:

```shell
curl -X POST \
  https://debug.bvnk.co/account/user \
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

url = "https://debug.bvnk.co/account/user"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
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

	url := "https://debug.bvnk.co/account/user"

	payload := strings.NewReader("------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderGivenName\"\r\n\r\nDebug\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderFamilyName\"\r\n\r\nAccount\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderDateOfBirth\"\r\n\r\n1900-01-01\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderIdentificationNumber\"\r\n\r\n400000-0000-001\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderContactNumber1\"\r\n\r\n(558) 555-42381\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderEmailAddress\"\r\n\r\nalice@bankai.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine1\"\r\n\r\nAddress 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine2\"\r\n\r\nAddress 2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderAddressLine3\"\r\n\r\nAddress 3\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPassword\"\r\n\r\npassword\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderPostalCode\"\r\n\r\n1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"AccountHolderCountry\"\r\n\r\nGB\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
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
HttpResponse<String> response = Unirest.post("https://debug.bvnk.co/account/user")
  .header("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
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

xhr.open("POST", "https://debug.bvnk.co/account/user");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Postman-Token", "7c40dcd5-3eef-f583-e3e6-f99320a9e796");

xhr.send(data);
```

Users act as account holders and need to be created as the first action. All accounts need to be linked to users, and Know Your Customer requirements centre around users. Country must be valid ISO2 code, a list of valid countries and their codes can be retrieved through `GET /countries`.

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
AccountHolderCountry | true | Valid ISO2 code for country. List of countries can be retrieved from `/countries`.
AccountHolderPassword | true | Password for the users account

<aside class="notice">
The password sent through on this call will used along with the <code>AccountHolderIdentificationNumber</code> to generate authentication credentials.
</aside>

