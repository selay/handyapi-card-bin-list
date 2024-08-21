# Handy API - BIN List API

Welcome to the official GitHub repository for the Handy API's BIN List service. This API provides enterprise-grade, highly available, regularly updated data to help you verify and distinguish credit and debit card details using the first digits of the card number. It’s designed for both backend and frontend integrations, ensuring flexibility and ease of use for developers across the globe.

## Features

- **Broad Scheme Support**: Supports cards issued under Visa, Mastercard, American Express, and other popular schemes.
- **Comprehensive Data**: Near 1,000,000 records covering a wide range of credit and debit cards.
- **Regular Updates**: Our databases are continually updated to ensure the most accurate and current information.
- **Free Access**: Offered for free under a fair use policy, making it suitable for most projects.

## Use Cases

- **Surcharge Adjustment**: Easily adjust surcharge rates for different card types, particularly useful as credit cards often incur higher fees.
- **Card Verification**: Verify card details such as the issuing bank, card type, and country of issuance, enhancing transaction security.
- **Geographic Customization**: Tailor experiences based on the card’s country of issuance.

## Getting Started

Below are quick start guides for making API requests using different programming languages. Please note that these examples are provided for reference and may require adjustments to work in your specific environment. They have not been tested, so please ensure you validate functionality before use in production:

### cURL

```bash
curl -H "referrer: your-domain" "https://data.handyapi.com/bin/535316"
```

### PHP

```php
$url = "https://data.handyapi.com/bin/535316";
$options = [
    "http" => [
        "method" => "GET",
        "header" => "Referer: your_domain\r\n"
    ]
];
$context = stream_context_create($options);
$response = file_get_contents($url, false, $context);
$data = json_decode($response, true);
print_r($data);
```

### JavaScript

```javascript
fetch('https://data.handyapi.com/bin/535316', {
    headers: { 'referrer': 'your-domain' }
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));

```

### Python

```python
import requests

response = requests.get('https://data.handyapi.com/bin/535316', headers={'referrer': 'your-domain'})

if response.status_code == 200:
  data = response.json()
  print(data)
else:
  print('Error:', response.status_code)

```

### Java

```java

String url = "https://data.handyapi.com/bin/535316";
HttpClient client = HttpClient.newHttpClient();
HttpRequest request = HttpRequest.newBuilder()
        .uri(URI.create(url))
        .header("referrer", "your domain")
        .build();

HttpResponse response = client.send(request, HttpResponse.BodyHandlers.ofString());

String jsonString = response.body();
System.out.println(jsonString);

```

### Go

```go

url := "https://data.handyapi.com/bin/535316"
req, _ := http.NewRequest("GET", url, nil)
req.Header.Set("referrer", "your_domain")
client := &http.Client{}
resp, _ := client.Do(req)
defer resp.Body.Close()
fmt.Println(resp.Body)

```

### C/C++

```c
int main() {
    CURL *curl;
    CURLcode res;

    curl = curl_easy_init();
    if(curl) {
        curl_easy_setopt(curl, CURLOPT_URL, "https://data.handyapi.com/bin/535316");
        curl_easy_setopt(curl, CURLOPT_HTTPHEADER, "referrer: your-domain");

        res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);
        if(res != CURLE_OK)
            fprintf(stderr, "curl_easy_perform() failed: %s\n", curl_easy_strerror(res));

        curl_easy_cleanup(curl);
    }
    return 0;
}
```

### Ruby

```ruby
uri = URI("https://data.handyapi.com/bin/535316")
req = Net::HTTP::Get.new(uri, 'referrer' => 'your-domain')
res = Net::HTTP.start(uri.hostname, uri.port, use_ssl: uri.scheme == 'https') { |http| http.request(req) }
puts res.body

```


### Swift

```swift

let url = URL(string: "https://data.handyapi.com/bin/535316")!
var request = URLRequest(url: url)
request.addValue("your-domain", forHTTPHeaderField: "referrer")

let task = URLSession.shared.dataTask(with: request) { data, response, error in
    guard let data = data, error == nil else {
        print("Error:", error?.localizedDescription ?? "Unknown error")
        return
    }
    if let responseString = String(data: data, encoding: .utf8) {
        print(responseString)
    }
}

task.resume()
```

### TypeScript

```typescript
axios.get('https://data.handyapi.com/bin/535316', {
    headers: {
        'referrer': 'your-domain'
    }
}).then(response => {
    console.log(response.data);
}).catch(error => {
    console.error('Error:', error);
});
```

### Dart

```dart
 var url = Uri.parse('https://data.handyapi.com/bin/535316');
    var response = await http.get(url, headers: {'referrer': 'your-domain'});
    if (response.statusCode == 200) {
        print(response.body);
    } else {
        print('Error: ${response.statusCode}');
    }
```

### Rust

```rust
 #[tokio::main]
 async fn main() -> Result<(), reqwest::Error> {
    let client = reqwest::Client::new();
    let res = client.get("https://data.handyapi.com/bin/535316")
        .header("referrer", "your-domain")
        .send()
        .await?;

    println!("Status: {}", res.status());
    println!("Headers:\n{:#?}", res.headers());
    Ok(())
}
```

### Kotlin

```kotlin
 val url = URL("https://data.handyapi.com/bin/535316")
    with(url.openConnection() as HttpURLConnection) {
        setRequestProperty("referrer", "your-domain")
        println(inputStream.bufferedReader().readText())
    }
```

### R

```r
library(httr)

response <- GET("https://data.handyapi.com/bin/535316", add_headers(referrer = "your-domain"))
content <- content(response, "text")
print(content)

```

### Perl

```perl
my $url = "https://data.handyapi.com/bin/535316";
my $ua = LWP::UserAgent->new;
$ua->default_header('referrer' => 'your-domain');

my $response = $ua->get($url);

if ($response->is_success) {
    print $response->decoded_content;
} else {
    print "Error: " . $response->status_line;
}

```

## Support

For support, feedback, or more information, please visit [HandyApi.com](https://www.handyapi.com) or contact us directly through GitHub Issues.

