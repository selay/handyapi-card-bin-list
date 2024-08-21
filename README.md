# Handy API - BIN List Lookup API

Welcome to the official GitHub repository for the Handy API Free BIN List service. This API provides enterprise-grade, highly available, regularly updated data to help you verify and distinguish credit and debit card details using the first digits of the card number. It’s designed for both backend and frontend integrations, ensuring flexibility and ease of use for developers across the globe.

## Features

- **Broad Scheme Support**: Supports cards issued under Visa, Mastercard, American Express, and other popular schemes.
- **Comprehensive Data**: Near 1,000,000 records covering a wide range of credit and debit cards.
- **Regular Updates**: Our databases are continually updated to ensure the most accurate and current information.
- **Free Access**: Offered for free under a fair use policy, making it suitable for most projects.

## Use Cases

- **Surcharge Adjustment**: Easily adjust surcharge rates for different card types, particularly useful as credit cards often incur higher fees. Debit vs credit card is the most common use case we see. 
- **Card Verification**: Verify card details such as the issuing bank, card type, and country of issuance, enhancing transaction security.
- **Fraud Detection/Geographic Customization**: BIN data can be used to enhance fraud detection such as checking country of issuance.

## 6-digit and 8-digit BINs

The BIN (Bank Identification Number) has been in transition from a 6-digit to an 8-digit format to accommodate a growing number of issuers and products. The 6-digit BIN has been the industry standard for years, identifying the institution that issued the card and the card type. However, to ensure a greater supply of numbers and reduce the risk of duplication, the industry is moving towards 8-digit BINs. It is a slow process and 6-digit version is still most common.

Our API is at the forefront of this change, supporting both 6-digit and 8-digit BINs. This means you can rely on our API for up-to-date, accurate identification of card issuers and types, whether your systems are currently using the traditional 6-digit BINs or have transitioned to the newer 8-digit format.

Note 6-digit BIN is still widely used and is reasonably accurate for most purposes. 

**NEVER** send the full credit card number! 

## Referer

Including the Referer (not referrer) header with your API requests is highly encouraged. However, if you're making the request from the frontend (e.g., using JavaScript in a browser), the browser will automatically include the Referer header, so you don't need to set it manually. The Referer header helps us provide support when you reach out and may also reduce the chance of your request being blocked.

## Getting Started

Below are quick start guides for making API requests using different programming languages. Please note that these examples are provided for reference and may require adjustments to work in your specific environment. They have not been tested, so please ensure you validate functionality before use in production:

In this example, **535316** is the first 6 digits of the credit card to lookup. 


### API Response in the following JSON format. 
You can use Type to tell if a card is a debit or credit card. 
```
{
  "Status": "SUCCESS",
  "Scheme": "MASTERCARD",
  "Type": "CREDIT",
  "Issuer": "COMMONWEALTH BANK OF AUSTRALIA",
  "CardTier": "PLATINUM MASTERCARD",
  "Country": {
    "A2": "AU",
    "A3": "AUS",
    "N3": "036",
    "ISD": "61",
    "Name": "Australia",
    "Cont": "Oceania"
  },
  "Luhn": true
}
```

### cURL

```bash
curl -H "Referer: your-domain" "https://data.handyapi.com/bin/535316"
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
$response = @file_get_contents($url, false, $context);
$data = @json_decode($response,true);
print_r($data);
```

### JavaScript

```javascript
fetch('https://data.handyapi.com/bin/535316')
  .then(response => response.json())
  .then(data => {
    //use JSON here
      console.log(data)
  })
  .catch();

```

### Python

```python
import requests

response = requests.get('https://data.handyapi.com/bin/535316', headers={'Referer': 'your-domain'})

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
        .header("Referer", "your domain")
        .build();

HttpResponse response = client.send(request, HttpResponse.BodyHandlers.ofString());

String jsonString = response.body();
System.out.println(jsonString);

```

### Go

```go

url := "https://data.handyapi.com/bin/535316"
req, _ := http.NewRequest("GET", url, nil)
req.Header.Set("Referer", "your_domain")
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
        curl_easy_setopt(curl, CURLOPT_HTTPHEADER, "Referer: your-domain");

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
req = Net::HTTP::Get.new(uri, 'Referer' => 'your-domain')
res = Net::HTTP.start(uri.hostname, uri.port, use_ssl: uri.scheme == 'https') { |http| http.request(req) }
puts res.body

```


### Swift

```swift

let url = URL(string: "https://data.handyapi.com/bin/535316")!
var request = URLRequest(url: url)
request.addValue("your-domain", forHTTPHeaderField: "Referer")

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
axios.get('https://data.handyapi.com/bin/535316')
    .then(response => {
      //Use JSON here
        console.log(response.data);
    })
    .catch(error => {
        console.error('Error:', error);
    });

```

### Dart

```dart
 var url = Uri.parse('https://data.handyapi.com/bin/535316');
    var response = await http.get(url, headers: {'Referer': 'your-domain'});
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
        .header("Referer", "your-domain")
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
        setRequestProperty("Referer", "your-domain")
        println(inputStream.bufferedReader().readText())
    }
```

### R

```r
library(httr)

response <- GET("https://data.handyapi.com/bin/535316", add_headers(Referer = "your-domain"))
content <- content(response, "text")
print(content)

```

### Perl

```perl
my $url = "https://data.handyapi.com/bin/535316";
my $ua = LWP::UserAgent->new;
$ua->default_header('Referer' => 'your-domain');

my $response = $ua->get($url);

if ($response->is_success) {
    print $response->decoded_content;
} else {
    print "Error: " . $response->status_line;
}

```

## Support

For support, feedback, or more information, please visit [HandyApi.com](https://www.handyapi.com) or contact us directly through GitHub Issues.

