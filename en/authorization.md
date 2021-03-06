{% method %}
# Authorization

We require a JSON Web Token ([JWT](https://jwt.io/)) be sent along with your request via the `Authorization` header.  
JWTs are passed as bearer tokens in the Authorization header, and look like the following:

`Authorization: <Enter your API Key>`


There's no need to create JWTs manually, they will be created for you when you register for the API - [Register Here!](https://developer.vainglorygame.com/users/sign_in)

In some cases an `X-API-KEY` will give you more access to information, and in all cases it means that you are operating under a per-token rate limit.

{% sample lang="shell" %}
> To specify the Headers, use this code:

```shell
  # With shell, you can just pass the correct header with each request
  curl "<endpoint-url>" \
  -H "Authorization: <api-key>"
  -H "Accept: application/vnd.api+json"
```
{% sample lang="java" %}
```java
import java.io.*;
import java.net.*;

URL url = new URL("<endpoint-url>");
HttpURLConnection conn = (HttpURLConnection) url.openConnection();
conn.setRequestMethod("GET");
conn.setRequestProperty("Authorization","<api-key>");
conn.setRequestProperty("Accept", "application/vnd.api+json");

conn.getInputStream()
```

{% sample lang="python" %}
```python
import requests

url = "<endpoint-url>"

header = {
    "Authorization": "<api-key>",
    "Accept": "application/vnd.api+json"
}

r = requests.get(url, headers=header)
```
{% sample lang="ruby" %}
```ruby
```
{% sample lang="js" %}
```javascript
```

{% sample lang="go" %}
```go
import "net/http"

client := &http.Client{}
req, _ := http.NewRequest("GET","<endpoint-url>",nil)
req.Header.Set("Authorization", "<api-key>")
req.Header.Set("Accept", "application/vnd.api+json")
res, _ := client.Do(req)
```

{% sample lang="swift" %}
```swift
import Foundation

let urlString = endpoint-url"

let url = NSURL(string: urlString)
var downloadTask = URLRequest(url: (url as URL?)!, cachePolicy: URLRequest.CachePolicy.ReloadIgnoringCacheData, timeoutInterval: 20)

downloadTask.httpMethod = "GET"

downloadTask.addValue("apiKey", forHTTPHeaderField: "Authorization")
downloadTask.addValue("application/vnd.api+json", forHTTPHeaderField: "Accept")

URLSession.shared.dataTask(with: downloadTask) { (data, response, error) in
if let response = response {
    print(response)
}

if let data = data {
    do {
    let jsonData = try JSONSerialization.jsonObject(with: data, options: .allowFragments) as? NSDictionary
    print(jsonData!.value(forKey: "data") as Any)
    } catch {
    print(error)
    }
}
}.resume()
```

{% endmethod %}
