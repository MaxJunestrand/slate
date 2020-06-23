---
title: Abios Odds API v0.1.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="abios-odds-api">Abios Odds API v0.1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the Odds API for Abios' odds.

Base URLs:

* <a href="https://api.abiosgaming.com/v2">https://api.abiosgaming.com/v2</a>

* <a href="https://odds-service.stage.abios.net/v0">https://odds-service.stage.abios.net/v0</a>

* <a href="https://odds-service.dev.abios.net/v0">https://odds-service.dev.abios.net/v0</a>

<a href="https://abiosgaming.com/terms">Terms of service</a>
Email: <a href="mailto:contact@abiosgaming.com">Abios</a> Web: <a href="https://abiosgaming.com">Abios</a> 

# Authentication

* API Key (header)
    - Parameter Name: **Abios-Secret**, in: header. 

* API Key (query)
    - Parameter Name: **secret**, in: query. 

<h1 id="abios-odds-api-markets">MARKETS</h1>

## listMarkets

<a id="opIdlistMarkets"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.abiosgaming.com/v2/markets \
  -H 'Accept: application/json'

```

```http
GET https://api.abiosgaming.com/v2/markets HTTP/1.1
Host: api.abiosgaming.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.abiosgaming.com/v2/markets',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.abiosgaming.com/v2/markets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.abiosgaming.com/v2/markets', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.abiosgaming.com/v2/markets', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.abiosgaming.com/v2/markets");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.abiosgaming.com/v2/markets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /markets`

*List all markets*

Retrieve all the markets. By default all the markets in `open` state are returned.

<h3 id="listmarkets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|fixture.id|query|integer(int32)|false|Filters results so only markets for the given fixture id's are returned. When filtering with this parameter the `fixture.type` parameter MUST be set as well.|
|fixture.type|query|string|false|Filters results on the type of the fixture, e.g. `series` or `match`.|
|fixture.game_id|query|integer(int32)|false|Filters results on the game the related series belongs to.|
|fixture.tier|query|integer(int32)|false|Filters results on the tier the related series belongs to.|
|skip|query|integer(int32)|false|The number of results to skip before `take`ing results|
|state|query|any|false|Market state filter, only return markets in the given state|
|take|query|integer(int32)|false|How many results to return in the response.|
|type|query|integer(int32)|false|Filter the result on the given market type.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|fixture.type|series|
|fixture.type|match|
|fixture.tier|1|
|fixture.tier|2|
|fixture.tier|3|

> Example responses

> A list of market resources

```json
[
  {
    "id": 1558,
    "type": {
      "id": 1,
      "scope": "pre_game",
      "name": "series_winner",
      "label": "Series Winner",
      "context": "team"
    },
    "state": "open",
    "margin": 0.04,
    "label": "Series Winner",
    "fixture": {
      "id": 214135,
      "game_id": 2,
      "tier": 2,
      "type": "series",
      "href": "https://api.abiosgaming.com/v2/series/214135"
    },
    "selections": [
      {
        "id": 3589,
        "market_id": 1558,
        "state": "open",
        "was_outcome": false,
        "entity": {
          "id": 31038,
          "type": "team",
          "href": "https://api.abiosgaming.com/v2/teams/31038"
        },
        "label": "JD Gaming to win",
        "odds": 1.87,
        "updated_at": "2019-12-26T12:23:57Z"
      },
      {
        "id": 3592,
        "market_id": 1558,
        "state": "open",
        "was_outcome": false,
        "entity": {
          "id": 53805,
          "type": "team",
          "href": "https://api.abiosgaming.com/v2/teams/53805"
        },
        "label": "LNG Esports to win",
        "odds": 1.87,
        "updated_at": "2019-12-26T12:23:57Z"
      }
    ],
    "created_at": "2019-12-13T08:33:55Z",
    "updated_at": "2019-12-26T12:23:57Z"
  }
]
```

<h3 id="listmarkets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of market resources|Inline|

<h3 id="listmarkets-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Market](#schemamarket)]|false|none|none|
|» id|integer(int64)|true|none|The id of the market.|
|» state|[MarketState](#schemamarketstate)|true|none|Defines where in the 'life cycle' the market is.|
|» type|[MarketType](#schemamarkettype)|true|none|The market type information.|
|»» context|string|true|none|The type of resource the market is associated with|
|»» id|integer(int64)|true|none|The unique id of the market type|
|»» label|string|true|none|A label describing the market in human-readable form|
|»» name|string|true|none|The unique market name. It can used as the identity of the market instead of the `id`. Guaranteed to be in a URL-safe format.|
|»» scope|string|true|none|What the market selections relate to.|
|» margin|number(float)|true|none|The overround (margin) applied to the selections in this market.|
|» label|string|true|none|Explains, in a human readable way, what the market is about. Mostly for use by a stupid/thin client/front end.|
|» fixture|[MarketFixtureResource](#schemamarketfixtureresource)|true|none|The market's context (series, match or tournament etc).|
|»» id|integer(int64)|true|none|The id of the fixture resource.|
|»» game_id|integer(int32)|true|none|The game id for which the underlying series is part of.|
|»» type|string|true|none|The resource type.|
|»» href|string(uri)|true|none|The Abios API URI for the resource.|
|» selections|[[SelectionResource](#schemaselectionresource)]|true|none|The selections of the market as a list of selection resources.|
|»» id|integer(int64)|true|none|The id of this selection resource.|
|»» market_id|integer(int64)|true|none|The id for the market this selection is part of.|
|»» state|[MarketState](#schemamarketstate)|true|none|Defines where in the 'life cycle' the selection currently is.|
|»» was_outcome|boolean|true|none|If this was the market outcome.|
|»» entity|[SelectionEntityResource](#schemaselectionentityresource)|false|none|The entity the selection relates to.|
|»»» id|integer(int64)|true|none|The id of the resource.|
|»»» type|string|true|none|The resource type.|
|»»» href|string(uri)|true|none|The Abios API URI for the resource.|
|»» label|string|true|none|Explains, in a human readable way, this selection for the market. Mostly for use by a stupid/thin client/front end.|
|»» odds|number(float)|true|none|The odds for this selection.|
|»» updated_at|string(date-time)|true|none|When the odds resource was last updated. Note that `updated_at` is updated when either the `odds`, `state` or `was_outcome` fields change.|
|» created_at|string(date-time)|true|none|When the market was first created.|
|» updated_at|string(date-time)|true|none|When the market state was last updated. Note that `updated_at` does not change if any of the selection resources linked to this market is changed, it only shows when the last life-cycle state change happened.|

#### Enumerated Values

|Property|Value|
|---|---|
|state|created|
|state|open|
|state|cancelled|
|state|closed|
|state|settled|
|context|team|
|context|match|
|context|series|
|scope|pre_game|
|type|match|
|type|series|
|state|created|
|state|open|
|state|cancelled|
|state|closed|
|state|settled|
|type|match|
|type|series|

<aside class="success">
This operation does not require authentication
</aside>

## getMarketById

<a id="opIdgetMarketById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.abiosgaming.com/v2/markets/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.abiosgaming.com/v2/markets/{id} HTTP/1.1
Host: api.abiosgaming.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.abiosgaming.com/v2/markets/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.abiosgaming.com/v2/markets/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.abiosgaming.com/v2/markets/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.abiosgaming.com/v2/markets/{id}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.abiosgaming.com/v2/markets/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.abiosgaming.com/v2/markets/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /markets/{id}`

*Fetch a specific market*

Retrieve the market with the specified Id.

<h3 id="getmarketbyid-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|The id of the market to fetch|

> Example responses

> A market resource

```json
{
  "id": 1558,
  "type": {
    "id": 1,
    "scope": "pre_game",
    "name": "series_winner",
    "label": "Series Winner",
    "context": "team"
  },
  "state": "open",
  "margin": 0.04,
  "label": "Series Winner",
  "fixture": {
    "id": 214135,
    "game_id": 2,
    "tier": 2,
    "type": "series",
    "href": "https://api.abiosgaming.com/v2/series/214135"
  },
  "selections": [
    {
      "id": 3589,
      "market_id": 1558,
      "state": "open",
      "was_outcome": false,
      "entity": {
        "id": 31038,
        "type": "team",
        "href": "https://api.abiosgaming.com/v2/teams/31038"
      },
      "label": "JD Gaming to win",
      "odds": 1.87,
      "updated_at": "2019-12-26T12:23:57Z"
    },
    {
      "id": 3592,
      "market_id": 1558,
      "state": "open",
      "was_outcome": false,
      "entity": {
        "id": 53805,
        "type": "team",
        "href": "https://api.abiosgaming.com/v2/teams/53805"
      },
      "label": "LNG Esports to win",
      "odds": 1.87,
      "updated_at": "2019-12-26T12:23:57Z"
    }
  ],
  "created_at": "2019-12-13T08:33:55Z",
  "updated_at": "2019-12-26T12:23:57Z"
}
```

<h3 id="getmarketbyid-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A market resource|[Market](#schemamarket)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No market with the given id exists.|None|

<aside class="success">
This operation does not require authentication
</aside>

## patchMarketState

<a id="opIdpatchMarketState"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.abiosgaming.com/v2/markets/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.abiosgaming.com/v2/markets/{id} HTTP/1.1
Host: api.abiosgaming.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "op": "replace",
  "path": "/state",
  "value": "open"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.abiosgaming.com/v2/markets/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.abiosgaming.com/v2/markets/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.abiosgaming.com/v2/markets/{id}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PATCH','https://api.abiosgaming.com/v2/markets/{id}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.abiosgaming.com/v2/markets/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.abiosgaming.com/v2/markets/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /markets/{id}`

*Set market data*

Update the life-cycle state for a market

> Body parameter

```json
{
  "op": "replace",
  "path": "/state",
  "value": "open"
}
```

<h3 id="patchmarketstate-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» op|body|string|true|none|
|» path|body|string|true|none|
|» value|body|string|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» op|replace|
|» path|/state|
|» value|open|
|» value|cancelled|
|» value|suspended|
|» value|closed|
|» value|settled|

> Example responses

> 400 Response

```json
{
  "msg": "string"
}
```

<h3 id="patchmarketstate-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Update was successful|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request data was invalid. This is returned for a number of reasons, e.g. invalid patch specifications or attempt to set the market to a state it is not allowed to transition to.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The market id does not exists|None|

<h3 id="patchmarketstate-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» msg|string|true|none|Describes the problem.|

<aside class="success">
This operation does not require authentication
</aside>

## listPossibleMarketStates

<a id="opIdlistPossibleMarketStates"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.abiosgaming.com/v2/markets/states \
  -H 'Accept: application/json'

```

```http
GET https://api.abiosgaming.com/v2/markets/states HTTP/1.1
Host: api.abiosgaming.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.abiosgaming.com/v2/markets/states',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.abiosgaming.com/v2/markets/states',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.abiosgaming.com/v2/markets/states', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.abiosgaming.com/v2/markets/states', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.abiosgaming.com/v2/markets/states");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.abiosgaming.com/v2/markets/states", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /markets/states`

*List all possible market states*

List all possible market states

> Example responses

> 200 Response

```json
[
  {
    "name": "Open",
    "description": "Market and selections open for betting"
  },
  {
    "name": "Closed",
    "description": "Market and selections are closed and awaiting settlement"
  },
  {
    "name": "Suspended",
    "description": "Market and selections are suspended and no bets should be allowed"
  },
  {
    "name": "Settled",
    "description": "Market selection outcome has been determined"
  },
  {
    "name": "Cancelled",
    "description": "Markets are cancelled if something is wrong. Cancelled markets never move to another state, it is a final state"
  }
]
```

<h3 id="listpossiblemarketstates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all market states|[MarketStates](#schemamarketstates)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="abios-odds-api-selections">SELECTIONS</h1>

## listSelectionTypes

<a id="opIdlistSelectionTypes"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.abiosgaming.com/v2/selections/types \
  -H 'Accept: application/json'

```

```http
GET https://api.abiosgaming.com/v2/selections/types HTTP/1.1
Host: api.abiosgaming.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.abiosgaming.com/v2/selections/types',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.abiosgaming.com/v2/selections/types',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.abiosgaming.com/v2/selections/types', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.abiosgaming.com/v2/selections/types', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.abiosgaming.com/v2/selections/types");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.abiosgaming.com/v2/selections/types", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /selections/types`

*List all selection types*

List all selection types

> Example responses

> 200 Response

```json
[
  {
    "id": 4,
    "name": "series_score_1_1",
    "label": "1-1 draw"
  }
]
```

<h3 id="listselectiontypes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all selection types|Inline|

<h3 id="listselectiontypes-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[SelectionType](#schemaselectiontype)]|false|none|none|
|» id|integer(int64)|true|none|The id of the resource.|
|» name|string|true|none|A descriptive name for the selection type|
|» label|any|true|none|A string that describes the selection type. Suitable for showing as the name of the selection in a UI.|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_Market">Market</h2>
<!-- backwards compatibility -->
<a id="schemamarket"></a>
<a id="schema_Market"></a>
<a id="tocSmarket"></a>
<a id="tocsmarket"></a>

```json
{
  "id": 1558,
  "type": {
    "id": 1,
    "scope": "pre_game",
    "name": "series_winner",
    "label": "Series Winner",
    "context": "team"
  },
  "state": "open",
  "margin": 0.04,
  "label": "Series Winner",
  "fixture": {
    "id": 214135,
    "game_id": 2,
    "tier": 2,
    "type": "series",
    "href": "https://api.abiosgaming.com/v2/series/214135"
  },
  "selections": [
    {
      "id": 3589,
      "market_id": 1558,
      "state": "open",
      "was_outcome": false,
      "entity": {
        "id": 31038,
        "type": "team",
        "href": "https://api.abiosgaming.com/v2/teams/31038"
      },
      "label": "JD Gaming to win",
      "odds": 1.87,
      "updated_at": "2019-12-26T12:23:57Z"
    },
    {
      "id": 3592,
      "market_id": 1558,
      "state": "open",
      "was_outcome": false,
      "entity": {
        "id": 53805,
        "type": "team",
        "href": "https://api.abiosgaming.com/v2/teams/53805"
      },
      "label": "LNG Esports to win",
      "odds": 1.87,
      "updated_at": "2019-12-26T12:23:57Z"
    }
  ],
  "created_at": "2019-12-13T08:33:55Z",
  "updated_at": "2019-12-26T12:23:57Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|The id of the market.|
|state|[MarketState](#schemamarketstate)|true|none|Defines where in the 'life cycle' the market is.|
|type|[MarketType](#schemamarkettype)|true|none|The market type information.|
|margin|number(float)|true|none|The overround (margin) applied to the selections in this market.|
|label|string|true|none|Explains, in a human readable way, what the market is about. Mostly for use by a stupid/thin client/front end.|
|fixture|[MarketFixtureResource](#schemamarketfixtureresource)|true|none|The market's context (series, match or tournament etc).|
|selections|[[SelectionResource](#schemaselectionresource)]|true|none|The selections of the market as a list of selection resources.|
|created_at|string(date-time)|true|none|When the market was first created.|
|updated_at|string(date-time)|true|none|When the market state was last updated. Note that `updated_at` does not change if any of the selection resources linked to this market is changed, it only shows when the last life-cycle state change happened.|

<h2 id="tocS_MarketType">MarketType</h2>
<!-- backwards compatibility -->
<a id="schemamarkettype"></a>
<a id="schema_MarketType"></a>
<a id="tocSmarkettype"></a>
<a id="tocsmarkettype"></a>

```json
{
  "context": "team",
  "id": 0,
  "label": "string",
  "name": "string",
  "scope": "pre_game"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|context|string|true|none|The type of resource the market is associated with|
|id|integer(int64)|true|none|The unique id of the market type|
|label|string|true|none|A label describing the market in human-readable form|
|name|string|true|none|The unique market name. It can used as the identity of the market instead of the `id`. Guaranteed to be in a URL-safe format.|
|scope|string|true|none|What the market selections relate to.|

#### Enumerated Values

|Property|Value|
|---|---|
|context|team|
|context|match|
|context|series|
|scope|pre_game|

<h2 id="tocS_MarketState">MarketState</h2>
<!-- backwards compatibility -->
<a id="schemamarketstate"></a>
<a id="schema_MarketState"></a>
<a id="tocSmarketstate"></a>
<a id="tocsmarketstate"></a>

```json
"created"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|created|
|*anonymous*|open|
|*anonymous*|cancelled|
|*anonymous*|closed|
|*anonymous*|settled|

<h2 id="tocS_MarketStates">MarketStates</h2>
<!-- backwards compatibility -->
<a id="schemamarketstates"></a>
<a id="schema_MarketStates"></a>
<a id="tocSmarketstates"></a>
<a id="tocsmarketstates"></a>

```json
[
  {
    "name": "Open",
    "description": "Market and selections open for betting"
  },
  {
    "name": "Closed",
    "description": "Market and selections are closed and awaiting settlement"
  },
  {
    "name": "Suspended",
    "description": "Market and selections are suspended and no bets should be allowed"
  },
  {
    "name": "Settled",
    "description": "Market selection outcome has been determined"
  },
  {
    "name": "Cancelled",
    "description": "Markets are cancelled if something is wrong. Cancelled markets never move to another state, it is a final state"
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|none|
|description|string|false|none|none|

<h2 id="tocS_MarketFixtureResource">MarketFixtureResource</h2>
<!-- backwards compatibility -->
<a id="schemamarketfixtureresource"></a>
<a id="schema_MarketFixtureResource"></a>
<a id="tocSmarketfixtureresource"></a>
<a id="tocsmarketfixtureresource"></a>

```json
{
  "id": 210275,
  "tier": 2,
  "game_id": 1,
  "type": "series",
  "href": "https://atlas.abiosgaming.com/v3/series/210275"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|The id of the fixture resource.|
|game_id|integer(int32)|true|none|The game id for which the underlying series is part of.|
|type|string|true|none|The resource type.|
|href|string(uri)|true|none|The Abios API URI for the resource.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|match|
|type|series|

<h2 id="tocS_SelectionResource">SelectionResource</h2>
<!-- backwards compatibility -->
<a id="schemaselectionresource"></a>
<a id="schema_SelectionResource"></a>
<a id="tocSselectionresource"></a>
<a id="tocsselectionresource"></a>

```json
{
  "id": 0,
  "market_id": 0,
  "state": "created",
  "was_outcome": true,
  "entity": {
    "id": 11,
    "type": "team",
    "href": "https://atlas.abiosgaming.com/v3/teams/11"
  },
  "label": "string",
  "odds": 0,
  "updated_at": "2020-06-02T14:45:37Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|The id of this selection resource.|
|market_id|integer(int64)|true|none|The id for the market this selection is part of.|
|state|[MarketState](#schemamarketstate)|true|none|Defines where in the 'life cycle' the selection currently is.|
|was_outcome|boolean|true|none|If this was the market outcome.|
|entity|[SelectionEntityResource](#schemaselectionentityresource)|false|none|The entity the selection relates to.|
|label|string|true|none|Explains, in a human readable way, this selection for the market. Mostly for use by a stupid/thin client/front end.|
|odds|number(float)|true|none|The odds for this selection.|
|updated_at|string(date-time)|true|none|When the odds resource was last updated. Note that `updated_at` is updated when either the `odds`, `state` or `was_outcome` fields change.|

<h2 id="tocS_SelectionType">SelectionType</h2>
<!-- backwards compatibility -->
<a id="schemaselectiontype"></a>
<a id="schema_SelectionType"></a>
<a id="tocSselectiontype"></a>
<a id="tocsselectiontype"></a>

```json
{
  "id": 4,
  "name": "series_score_1_1",
  "label": "1-1 draw"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|The id of the resource.|
|name|string|true|none|A descriptive name for the selection type|
|label|any|true|none|A string that describes the selection type. Suitable for showing as the name of the selection in a UI.|

<h2 id="tocS_SelectionEntityResource">SelectionEntityResource</h2>
<!-- backwards compatibility -->
<a id="schemaselectionentityresource"></a>
<a id="schema_SelectionEntityResource"></a>
<a id="tocSselectionentityresource"></a>
<a id="tocsselectionentityresource"></a>

```json
{
  "id": 11,
  "type": "team",
  "href": "https://atlas.abiosgaming.com/v3/teams/11"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|The id of the resource.|
|type|string|true|none|The resource type.|
|href|string(uri)|true|none|The Abios API URI for the resource.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|match|
|type|series|

