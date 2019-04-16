# Amazon Alexa Door bell Simple REST API

Looking to build a smart doorbell? Do you want use your Alexa as a doorbell extension? We have built a simple doorbell API service that when called, will trigger your Amazon Alexa into announcing that there's someone at your door, alternatively you can use one of the many chimes available.

You can even use this trigger API as a way of starting Alexa routines.  With routines, you can customise what actions are performed when the trigger occurs. Here are a few things of what you can do:

- Say a phrase
- Activate an Alexa connected device
- Play some music
- Read some news

In this repository you will find examples of how to call the API service.

## Links

- [Main Website](https://www.ijpuk.com)
- [Swagger API Service](https://api.ijpuk.com)

### Python

```
import requests

url = "https://api.ijpuk.com/api/v1/Doorbell/{your doorbell key}"

payload = ""
headers = {
    'Content-Length': "0",
    'Authorization': "Basic {your base64 encoded username:password}"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

### C# (RestSharp)
```cs
var client = new RestClient("https://api.ijpuk.com/api/v1/Doorbell/{your doorbell key}");
var request = new RestRequest(Method.POST);
request.AddHeader("Authorization", "Basic {your base64 encoded username:password}");
request.AddHeader("Content-Length", "0");
IRestResponse response = client.Execute(request);
```

### go
```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://api.ijpuk.com/api/v1/Doorbell/{your doorbell key}"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("Content-Length", "0")
	req.Header.Add("Authorization", "Basic {your base64 encoded username:password}")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

### Bash
```bash
curl -X POST https://api.ijpuk.com/api/v1/Doorbell/{your doorbell key} -H 'Authorization: Basic {your base64 encoded username:password}' -H 'Content-Length: 0'
```
