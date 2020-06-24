---
title: Abios REST API v3.0
language_tabs:
  - ruby: Ruby
  - python: Python
  - go: Go
language_clients:
  - ruby: ""
  - python: ""
  - go: ""
toc_footers: []
includes:
  - oddsapi
  - pushapi
search: false
highlight_theme: darkula
headingLevel: 2
generator: widdershins v4.0.1

---

<h1 id="abios-rest-api">Abios REST API v3.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The Abios API is an extensive, live-updated, database of esports everything!

Base URLs:

* <a href="https://atlas.abiosgaming.com/v3">https://atlas.abiosgaming.com/v3</a>

* <a href="https://atlas.stage.abios.net/v3">https://atlas.stage.abios.net/v3</a>

* <a href="https://atlas.develop.abios.net/v3">https://atlas.develop.abios.net/v3</a>

<a href="https://abiosgaming.com/terms">Terms of service</a>
Email: <a href="mailto:info@abiosgaming.com">Abios Gaming AB</a> Web: <a href="https://abiosgaming.com">Abios Gaming AB</a> 

# Authentication

* API Key (header)
    - Parameter Name: **Abios-Secret**, in: header. 

* API Key (query)
    - Parameter Name: **secret**, in: query. 

<h1 id="abios-rest-api-games">GAMES</h1>

## /games

<a id="opIdgetGames"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games`

Fetch all games

<h3 id="/games-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "abbreviation": "string",
    "title": "string",
    "default_match_type": "team",
    "default_map": {
      "id": 0
    },
    "defaults": {
      "match_type": "team",
      "map": {
        "id": 0,
        "name": "string",
        "external_name": "string",
        "official": true,
        "game": {
          "id": 0
        }
      },
      "lineup_size": 1
    },
    "deleted_at": "2020-06-24T09:20:48Z",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "circle"
      }
    ],
    "color": "string"
  }
]
```

<h3 id="/games-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Games.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1games/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1games/get/responses/200/content/application~1json/schema/items)]|false|none|none|
|» id|integer|true|none|none|
|» abbreviation|string|true|none|none|
|» title|string|true|none|none|
|» default_match_type|[Game/properties/default_match_type](#schemagame/properties/default_match_type)|true|none|none|
|» default_map|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|
|»» id|integer|true|none|none|
|» defaults|object|true|none|none|
|»» match_type|[Game/properties/default_match_type](#schemagame/properties/default_match_type)|true|none|none|
|»» map|[Game/properties/defaults/properties/map/allOf/0](#schemagame/properties/defaults/properties/map/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» external_name|string¦null|false|none|none|
|»»» official|boolean|true|none|none|
|»»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»»» id|integer|true|none|none|
|»» lineup_size|integer¦null|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|
|» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» url|string|true|none|none|
|»»» thumbnail|string|true|none|none|
|»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Game/properties/images/items/allOf/1](#schemagame/properties/images/items/allof/1)|false|none|none|
|»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» color|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|default_match_type|team|
|default_match_type|player|
|default_match_type|brawl|
|default_match_type|battle_royale|
|match_type|team|
|match_type|player|
|match_type|brawl|
|match_type|battle_royale|
|type|circle|
|type|square|
|type|rectangle|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id

<a id="opIdgetGameById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}`

Fetch one game from its id

<h3 id="/games/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "abbreviation": "string",
  "title": "string",
  "default_match_type": "team",
  "default_map": {
    "id": 0
  },
  "defaults": {
    "match_type": "team",
    "map": {
      "id": 0,
      "name": "string",
      "external_name": "string",
      "official": true,
      "game": {
        "id": 0
      }
    },
    "lineup_size": 1
  },
  "deleted_at": "2020-06-24T09:20:48Z",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "circle"
    }
  ],
  "color": "string"
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Game.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|true|none|none|
|» abbreviation|string|true|none|none|
|» title|string|true|none|none|
|» default_match_type|[Game/properties/default_match_type](#schemagame/properties/default_match_type)|true|none|none|
|» default_map|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|
|»» id|integer|true|none|none|
|» defaults|object|true|none|none|
|»» match_type|[Game/properties/default_match_type](#schemagame/properties/default_match_type)|true|none|none|
|»» map|[Game/properties/defaults/properties/map/allOf/0](#schemagame/properties/defaults/properties/map/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» external_name|string¦null|false|none|none|
|»»» official|boolean|true|none|none|
|»»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»»» id|integer|true|none|none|
|»» lineup_size|integer¦null|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|
|» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» url|string|true|none|none|
|»»» thumbnail|string|true|none|none|
|»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Game/properties/images/items/allOf/1](#schemagame/properties/images/items/allof/1)|false|none|none|
|»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» color|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|default_match_type|team|
|default_match_type|player|
|default_match_type|brawl|
|default_match_type|battle_royale|
|match_type|team|
|match_type|player|
|match_type|brawl|
|match_type|battle_royale|
|type|circle|
|type|square|
|type|rectangle|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id/assets

<a id="opIdgetAssetsByGameId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}/assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}/assets', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}/assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}/assets`

Fetch available assets for game from its id.

<h3 id="/games/:id/assets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
{
  "weapons": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    }
  ],
  "win_reasons": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    }
  ]
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id/assets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A game assets.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id/assets-responseschema">Response Schema</h3>

#### Enumerated Values

|Property|Value|
|---|---|
|type|small|
|type|grey|
|type|outline|
|type|white|
|type|small|
|type|default|
|type|small|
|type|large|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id/maps

<a id="opIdgetMapsByGameId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}/maps',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}/maps', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}/maps", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}/maps`

Fetch available maps for game from its id.

<h3 id="/games/:id/maps-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "external_name": "string",
    "official": true,
    "game": {
      "id": 0
    }
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id/maps-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of maps.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id/maps-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Game/properties/defaults/properties/map/allOf/0](#schemagame/properties/defaults/properties/map/allof/0)]|false|none|none|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» external_name|string¦null|false|none|none|
|» official|boolean|true|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id/mappools

<a id="opIdgetMapPoolsByGameId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}/mappools',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}/mappools', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}/mappools", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}/mappools`

Fetch available map pools for game from its id.

<h3 id="/games/:id/mappools-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "from": "2020-06-24T09:20:48Z",
    "to": "2020-06-24T09:20:48Z",
    "maps": [
      {
        "id": 0
      }
    ]
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id/mappools-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of map pools|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id/mappools-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|true|none|none|
|» from|string(date-time)|true|none|none|
|» to|string(date-time)¦null|true|none|none|
|» maps|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id/races

<a id="opIdgetRacesByGameId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}/races',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}/races', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}/races", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}/races`

Fetch available races for game from its id.

<h3 id="/games/:id/races-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "game": {
      "id": 0
    }
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id/races-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of races.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id/races-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1games~1%7Bid%7D~1races/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1games~1%7bid%7d~1races/get/responses/200/content/application~1json/schema/items)]|false|none|none|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /games/:id/roles

<a id="opIdgetRolesByGameId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/games/{id}/roles',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/games/{id}/roles', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/games/{id}/roles", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /games/{id}/roles`

Fetch available roles for game from its id.

<h3 id="/games/:id/roles-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "game": {
      "id": 0
    }
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/games/:id/roles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of roles.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/games/:id/roles-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-countries">COUNTRIES</h1>

## regions/:id/countries

<a id="opIdgetCountriesByRegionId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/regions/{id}/countries',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/regions/{id}/countries', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/regions/{id}/countries", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /regions/{id}/countries`

Fetch all countries in the region

<h3 id="regions/:id/countries-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "abbreviation": "strin",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    ]
  }
]
```

<h3 id="regions/:id/countries-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of countries.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="regions/:id/countries-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)]|false|none|[A Country, nationality, or language associated with a resource.]|
|» id|integer|true|none|none|
|» name|string|true|none|The name of the Country.|
|» abbreviation|string|true|none|The Country's abbreviation.|
|» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» url|string|true|none|none|
|»»» thumbnail|string|true|none|none|
|»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-images">IMAGES</h1>

## /images/:id

<a id="opIdgetImageById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/images/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/images/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/images/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /images/{id}`

Fetch one image from its id

<h3 id="/images/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "url": "string",
  "thumbnail": "string",
  "fallback": true
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/images/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An Image.|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-incidents">INCIDENTS</h1>

## /incidents

<a id="opIdgetIncidents"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/incidents',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/incidents', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/incidents", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /incidents`

Fetch all incidents

<h3 id="/incidents-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "series": {
      "id": 0
    },
    "match": {
      "id": 0
    },
    "comment": "string",
    "game": {
      "id": 0
    },
    "tournament": {
      "id": 0
    },
    "created_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="/incidents-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of incidents.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/incidents-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-maps">MAPS</h1>

## /maps

<a id="opIdgetMaps"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/maps',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/maps', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/maps", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /maps`

Fetch all maps

<h3 id="/maps-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "name": "string",
  "external_name": "string",
  "official": true,
  "game": {
    "id": 0
  }
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/maps-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Map.|[Game/properties/defaults/properties/map/allOf/0](#schemagame/properties/defaults/properties/map/allof/0)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /maps/:id

<a id="opIdgetMapById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/maps/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/maps/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/maps/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /maps/{id}`

Fetch one map from its id

<h3 id="/maps/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "name": "string",
  "external_name": "string",
  "official": true,
  "game": {
    "id": 0
  }
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/maps/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Map.|[Game/properties/defaults/properties/map/allOf/0](#schemagame/properties/defaults/properties/map/allof/0)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-matches">MATCHES</h1>

## /matches/:id

<a id="opIddeleteMatchById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/matches/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/matches/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/matches/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /matches/{id}`

Delete matches from its id

<h3 id="/matches/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/matches/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /matches/:id/participants

<a id="opIdupdateParticipantsByMatchId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/matches/{id}/participants',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/matches/{id}/participants', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/matches/{id}/participants", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /matches/{id}/participants`

Update participants for match

> Body parameter

```json
[
  {
    "seed": 1,
    "score": 0,
    "forfeit": true,
    "roster": {
      "id": 0
    },
    "winner": true,
    "stats": {
      "kills": 0,
      "placement": 0
    }
  }
]
```

<h3 id="/matches/:id/participants-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1matches~1%7Bid%7D~1participants/put/requestBody/content/application~1json/schema/items](#schema#/paths/~1matches~1%7bid%7d~1participants/put/requestbody/content/application~1json/schema/items)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/matches/:id/participants-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## matches/:id/rosters

<a id="opIdgetRostersByMatchId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/matches/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/matches/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/matches/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /matches/{id}/rosters`

Fetch all rosters participating in the match

<h3 id="matches/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

<h3 id="matches/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Rosters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="matches/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /matches/:id/rosters/:roster_id

<a id="opIddeleteRosterByIdWithMatchById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/matches/{id}/rosters/{roster_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/matches/{id}/rosters/{roster_id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/matches/{id}/rosters/{roster_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /matches/{id}/rosters/{roster_id}`

Delete a match roster

<h3 id="/matches/:id/rosters/:roster_id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|roster_id|path|integer|true|Roster Id.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/matches/:id/rosters/:roster_id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /matches/:id/server/summary

<a id="opIdgetMatchesServerSummaryById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/matches/{id}/server/summary',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/matches/{id}/server/summary', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/matches/{id}/server/summary", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /matches/{id}/server/summary`

Fetch a match server summary from its id

<h3 id="/matches/:id/server/summary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
{
  "length": 0,
  "ended": true,
  "patch": "string",
  "dire": {
    "roster": {
      "id": 0
    },
    "score": 0,
    "is_winner": true,
    "structures_standing": {
      "towers": {
        "top_tier_1": true,
        "top_tier_2": true,
        "top_tier_3": true,
        "top_tier_4": true,
        "mid_tier_1": true,
        "mid_tier_2": true,
        "mid_tier_3": true,
        "bot_tier_1": true,
        "bot_tier_2": true,
        "bot_tier_3": true,
        "bot_tier_4": true
      },
      "barracks": {
        "top_ranged": true,
        "top_melee": true,
        "mid_ranged": true,
        "mid_melee": true,
        "bot_ranged": true,
        "bot_melee": true
      }
    },
    "players": [
      {
        "player": {
          "id": 0
        },
        "hero": {
          "items": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "runes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "spells": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "heroes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "small"
              }
            }
          ]
        },
        "kills": 0,
        "assists": 0,
        "deaths": 0,
        "gpm": 0,
        "xpm": 0,
        "networth": 0,
        "side": 2,
        "seed": 0,
        "level": 0,
        "creeps": {
          "faction": {
            "kills": {
              "total": 0
            },
            "denies": {
              "total": 0
            }
          },
          "neutrals": {
            "kills": {
              "total": 0,
              "roshan": 0
            },
            "stacks": {
              "total": 0
            }
          }
        },
        "damage": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "by_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "from_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "healing": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0
              },
              "by_mobs": {
                "total": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0
              },
              "from_mobs": {
                "total": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "multi_kills": [
          {
            "nr_kills": 0,
            "count": 0
          }
        ],
        "kill_streaks": [
          0
        ],
        "runes": {
          "arcane": 0,
          "bounty": 0,
          "double_damage": 0,
          "haste": 0,
          "illusion": 0,
          "invisibility": 0,
          "regeneration": 0
        },
        "items": {
          "hero": {
            "inventory": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "backpack": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "tp_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "neutral_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            }
          },
          "stash": {
            "items": [
              {
                "items": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "runes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "spells": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "heroes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ]
              }
            ],
            "default_size": 0
          },
          "mobs": [
            {
              "type": "string",
              "inventory": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              },
              "backpack": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              }
            }
          ]
        }
      }
    ]
  },
  "radiant": {
    "roster": {
      "id": 0
    },
    "score": 0,
    "is_winner": true,
    "structures_standing": {
      "towers": {
        "top_tier_1": true,
        "top_tier_2": true,
        "top_tier_3": true,
        "top_tier_4": true,
        "mid_tier_1": true,
        "mid_tier_2": true,
        "mid_tier_3": true,
        "bot_tier_1": true,
        "bot_tier_2": true,
        "bot_tier_3": true,
        "bot_tier_4": true
      },
      "barracks": {
        "top_ranged": true,
        "top_melee": true,
        "mid_ranged": true,
        "mid_melee": true,
        "bot_ranged": true,
        "bot_melee": true
      }
    },
    "players": [
      {
        "player": {
          "id": 0
        },
        "hero": {
          "items": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "runes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "spells": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "heroes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "small"
              }
            }
          ]
        },
        "kills": 0,
        "assists": 0,
        "deaths": 0,
        "gpm": 0,
        "xpm": 0,
        "networth": 0,
        "side": 2,
        "seed": 0,
        "level": 0,
        "creeps": {
          "faction": {
            "kills": {
              "total": 0
            },
            "denies": {
              "total": 0
            }
          },
          "neutrals": {
            "kills": {
              "total": 0,
              "roshan": 0
            },
            "stacks": {
              "total": 0
            }
          }
        },
        "damage": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "by_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "from_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "healing": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0
              },
              "by_mobs": {
                "total": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0
              },
              "from_mobs": {
                "total": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "multi_kills": [
          {
            "nr_kills": 0,
            "count": 0
          }
        ],
        "kill_streaks": [
          0
        ],
        "runes": {
          "arcane": 0,
          "bounty": 0,
          "double_damage": 0,
          "haste": 0,
          "illusion": 0,
          "invisibility": 0,
          "regeneration": 0
        },
        "items": {
          "hero": {
            "inventory": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "backpack": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "tp_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "neutral_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            }
          },
          "stash": {
            "items": [
              {
                "items": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "runes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "spells": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "heroes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ]
              }
            ],
            "default_size": 0
          },
          "mobs": [
            {
              "type": "string",
              "inventory": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              },
              "backpack": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              }
            }
          ]
        }
      }
    ]
  }
}
```

<h3 id="/matches/:id/server/summary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Match server summary.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/matches/:id/server/summary-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» length|integer|true|none|none|
|» ended|boolean|true|none|none|
|» patch|string|true|none|none|
|» dire|[MatchSummary/properties/dire](#schemamatchsummary/properties/dire)|true|none|none|
|»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» id|integer|true|none|none|
|»» score|integer|true|none|none|
|»» is_winner|boolean|true|none|none|
|»» structures_standing|object|true|none|none|
|»»» towers|object|true|none|none|
|»»»» top_tier_1|boolean|true|none|none|
|»»»» top_tier_2|boolean|true|none|none|
|»»»» top_tier_3|boolean|true|none|none|
|»»»» top_tier_4|boolean|true|none|none|
|»»»» mid_tier_1|boolean|true|none|none|
|»»»» mid_tier_2|boolean|true|none|none|
|»»»» mid_tier_3|boolean|true|none|none|
|»»»» bot_tier_1|boolean|true|none|none|
|»»»» bot_tier_2|boolean|true|none|none|
|»»»» bot_tier_3|boolean|true|none|none|
|»»»» bot_tier_4|boolean|true|none|none|
|»»» barracks|object|true|none|none|
|»»»» top_ranged|boolean|true|none|none|
|»»»» top_melee|boolean|true|none|none|
|»»»» mid_ranged|boolean|true|none|none|
|»»»» mid_melee|boolean|true|none|none|
|»»»» bot_ranged|boolean|true|none|none|
|»»»» bot_melee|boolean|true|none|none|
|»» players|[object]|true|none|none|
|»»» player|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» hero|[#/paths/~1games~1%7Bid%7D~1assets/get/responses/200/content/application~1json/schema/oneOf/1](#schema#/paths/~1games~1%7bid%7d~1assets/get/responses/200/content/application~1json/schema/oneof/1)|true|none|none|
|»»»» items|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|
|»»»»»» id|integer|true|none|none|
|»»»»»» name|string|true|none|none|
|»»»»»» external_id|integer¦null|false|none|none|
|»»»»»» external_string_id|string¦null|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|object|false|none|none|
|»»»»»» images|any|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»»»»» id|integer|true|read-only|none|
|»»»»»»»» url|string|true|none|none|
|»»»»»»»» thumbnail|string|true|none|none|
|»»»»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» runes|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|object|false|none|none|
|»»»»»» images|any|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» spells|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|object|false|none|none|
|»»»»»» images|any|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» heroes|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|object|false|none|none|
|»»»»»» images|any|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/1](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/1)|false|none|none|
|»»»»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» kills|integer|true|none|none|
|»»» assists|integer|true|none|none|
|»»» deaths|integer|true|none|none|
|»»» gpm|number(float)|true|none|none|
|»»» xpm|number(float)|true|none|none|
|»»» networth|integer|true|none|none|
|»»» side|integer|true|none|none|
|»»» seed|integer|true|none|none|
|»»» level|integer|true|none|none|
|»»» creeps|object|true|none|none|
|»»»» faction|object|true|none|none|
|»»»»» kills|object|true|none|none|
|»»»»»» total|integer|true|none|none|
|»»»»» denies|object|true|none|none|
|»»»»»» total|integer|true|none|none|
|»»»» neutrals|object|true|none|none|
|»»»»» kills|object|true|none|none|
|»»»»»» total|integer|true|none|none|
|»»»»»» roshan|integer|true|none|none|
|»»»»» stacks|object|true|none|none|
|»»»»»» total|integer|true|none|none|
|»»» damage|object|true|none|none|
|»»»» hero|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»»»» hp_removal|integer|true|none|none|
|»»»»»»» magical|integer|true|none|none|
|»»»»»»» physical|integer|true|none|none|
|»»»»»»» pure|integer|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» from_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» from_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»» structures|object|true|none|none|
|»»»»» towers|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» taken|object|true|none|none|
|»»»»»»» by_hero|object|true|none|none|
|»»»»»»»» total|integer|true|none|none|
|»»»»»»» by_mobs|object|true|none|none|
|»»»»»»»» total|integer|true|none|none|
|»»»»» barracks|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» shrines|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» ancient|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» other|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» taken|object|true|none|none|
|»»»»»»» by_hero|object|true|none|none|
|»»»»»»»» total|integer|true|none|none|
|»»»»»»» by_mobs|object|true|none|none|
|»»»»»»»» total|integer|true|none|none|
|»»» healing|object|true|none|none|
|»»»» hero|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» from_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» from_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» structures|object|true|none|none|
|»»»»» towers|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» barracks|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» shrines|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» taken|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» ancient|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» other|object|true|none|none|
|»»»»»» given|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» taken|object|true|none|none|
|»»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»» multi_kills|[object]|true|none|none|
|»»»» nr_kills|integer|true|none|none|
|»»»» count|integer|true|none|none|
|»»» kill_streaks|[integer]|true|none|none|
|»»» runes|object|true|none|none|
|»»»» arcane|integer|true|none|none|
|»»»» bounty|integer|true|none|none|
|»»»» double_damage|integer|true|none|none|
|»»»» haste|integer|true|none|none|
|»»»» illusion|integer|true|none|none|
|»»»» invisibility|integer|true|none|none|
|»»»» regeneration|integer|true|none|none|
|»»» items|object|true|none|none|
|»»»» hero|object|true|none|none|
|»»»»» inventory|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»»»» items|[[#/paths/~1games~1%7Bid%7D~1assets/get/responses/200/content/application~1json/schema/oneOf/1](#schema#/paths/~1games~1%7bid%7d~1assets/get/responses/200/content/application~1json/schema/oneof/1)]|true|none|none|
|»»»»»» default_size|integer|true|none|none|
|»»»»» backpack|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»»» tp_slot|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»»» neutral_slot|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» stash|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» mobs|[object]|true|none|none|
|»»»»» type|string|true|none|none|
|»»»»» inventory|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»»» backpack|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|» radiant|[MatchSummary/properties/dire](#schemamatchsummary/properties/dire)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|
|type|small|
|type|large|
|side|2|
|side|3|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## series/:id/matches

<a id="opIdgetMatchesBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/series/{id}/matches',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/series/{id}/matches', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/series/{id}/matches", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /series/{id}/matches`

Fetch all matches in the series

<h3 id="series/:id/matches-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "map": {
      "id": 0
    },
    "order": 0,
    "series": {
      "id": 0
    },
    "deleted_at": "2020-06-24T09:20:48Z",
    "game": {
      "id": 0
    },
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ]
  }
]
```

<h3 id="series/:id/matches-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Matches.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="series/:id/matches-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Match/allOf/0](#schemamatch/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» map|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» order|integer|true|none|none|
|»» series|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» id|integer|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/matches

<a id="opIdcreateMatchBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.post 'https://atlas.abiosgaming.com/v3/series/{id}/matches',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.post('https://atlas.abiosgaming.com/v3/series/{id}/matches', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://atlas.abiosgaming.com/v3/series/{id}/matches", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /series/{id}/matches`

Create a match

> Body parameter

```json
{
  "map": {
    "id": 0
  }
}
```

<h3 id="/series/:id/matches-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[Match/allOf/0](#schemamatch/allof/0)|false|none|
|» id|body|integer|true|none|
|» map|body|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|
|»» id|body|integer|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/matches-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|match id.|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-regions">REGIONS</h1>

## /regions

<a id="opIdgetRegions"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/regions',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/regions', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/regions", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /regions`

Fetch all regions

<h3 id="/regions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "name": "string",
    "abbreviation": "string",
    "country": {
      "id": 0,
      "name": "string",
      "abbreviation": "strin",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  }
]
```

<h3 id="/regions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of regions.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/regions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)]|false|none|none|
|» name|string|true|none|none|
|» abbreviation|string|true|none|none|
|» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»» id|integer|true|none|none|
|»» name|string|true|none|The name of the Country.|
|»» abbreviation|string|true|none|The Country's abbreviation.|
|»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»» id|integer|true|read-only|none|
|»»»» url|string|true|none|none|
|»»»» thumbnail|string|true|none|none|
|»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-rosters">ROSTERS</h1>

## /rosters

<a id="opIdcreateRoster"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.post 'https://atlas.abiosgaming.com/v3/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.post('https://atlas.abiosgaming.com/v3/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://atlas.abiosgaming.com/v3/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /rosters`

Create a Roster

"team" or "line_up" can be null but *NOT* both

> Body parameter

```json
{
  "team": {
    "id": 0
  },
  "line_up": {
    "players": [
      {
        "id": 0
      }
    ]
  }
}
```

<h3 id="/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|body|body|[Roster/allOf/0](#schemaroster/allof/0)|true|none|
|» id|body|integer|true|none|
|» team|body|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|
|»» id|body|integer|true|none|
|» line_up|body|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|
|»» id|body|integer|true|none|
|»» players|body|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|
|»»» id|body|integer|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 201 Response

```json
{
  "id": 0
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Id of created roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict, roster exists|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /rosters/:id

<a id="opIdgetRosterById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/rosters/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/rosters/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/rosters/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /rosters/{id}`

Fetch one roster from its id

<h3 id="/rosters/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "team": {
    "id": 0
  },
  "line_up": {
    "id": 0,
    "players": [
      {
        "id": 0
      }
    ]
  }
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/rosters/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Roster.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/rosters/:id-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /rosters/:id/series

<a id="opIdgetSeriesByRosterId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/rosters/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/rosters/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/rosters/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /rosters/{id}/series`

Fetch available series for roster from its id.

<h3 id="/rosters/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/rosters/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of series.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/rosters/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-series">SERIES</h1>

## /series

<a id="opIdgetSeries"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /series`

Fetch all series

<h3 id="/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

<h3 id="/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of series.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id

<a id="opIddeleteSeriesById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/series/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/series/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/series/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /series/{id}`

Delete series from its id

<h3 id="/series/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## series/:id/casters

<a id="opIdgetCastersBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/series/{id}/casters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/series/{id}/casters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/series/{id}/casters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /series/{id}/casters`

Fetch all casters of the series

<h3 id="series/:id/casters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "display_name": "string",
    "username": "string",
    "game": {
      "id": 0
    },
    "platform": {
      "id": 0,
      "name": "string",
      "color": "string",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    },
    "stream": {
      "id": 0,
      "username": "string",
      "display_name": "string",
      "status_text": "string",
      "viewer_count": 0,
      "online": true,
      "last_online": "2020-06-24T09:20:48Z",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "external"
        }
      ],
      "platform": {
        "id": 0,
        "name": "string",
        "color": "string",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    }
  }
]
```

<h3 id="series/:id/casters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Casters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="series/:id/casters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Caster/allOf/0](#schemacaster/allof/0)|false|none|A caster is an individual shoutcaster casting a series. It will have a stream associated with it.|
|»» id|integer|true|read-only|The internal id of the caster.|
|»» display_name|string|false|none|The name of the caster.|
|»» username|string|false|none|The username of the caster|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» color|string¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»» id|integer|true|read-only|none|
|»»»»» url|string|true|none|none|
|»»»»» thumbnail|string|true|none|none|
|»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» stream|[Caster/allOf/1/properties/stream/allOf/0](#schemacaster/allof/1/properties/stream/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» username|string¦null|true|none|none|
|»»» display_name|string|true|none|none|
|»»» status_text|string¦null|true|none|none|
|»»» viewer_count|integer|true|none|none|
|»»» online|boolean|true|none|none|
|»»» last_online|string(date-time)¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Stream/properties/images/items/allOf/1](#schemastream/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|none|
|»»»» color|string¦null|true|none|none|
|»»»» images|[allOf]|true|none|none|
|»» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|true|none|none|
|»»» name|string|true|none|none|
|»»» abbreviation|string|true|none|none|
|»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|The name of the Country.|
|»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|
|type|external|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/casters

<a id="opIdupdateCastersBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/series/{id}/casters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/series/{id}/casters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/series/{id}/casters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /series/{id}/casters`

Update series casters

> Body parameter

```json
[
  {
    "primary": true,
    "caster": {
      "id": 0
    }
  }
]
```

<h3 id="/series/:id/casters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/casters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/end

<a id="opIdendSeriesById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/series/{id}/end',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/series/{id}/end', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/series/{id}/end", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /series/{id}/end`

End series from its id

<h3 id="/series/:id/end-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/end-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/note

<a id="opIdupdateNoteBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/series/{id}/note',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/series/{id}/note', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/series/{id}/note", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /series/{id}/note`

Update series note

> Body parameter

```json
{
  "note": "string",
  "user": {
    "id": 0
  }
}
```

<h3 id="/series/:id/note-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1series~1%7Bid%7D~1note/put/requestBody/content/application~1json/schema](#schema#/paths/~1series~1%7bid%7d~1note/put/requestbody/content/application~1json/schema)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/note-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/participants

<a id="opIdupdateParticipantsBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/series/{id}/participants',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/series/{id}/participants', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/series/{id}/participants", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /series/{id}/participants`

Update participants for series

> Body parameter

```json
[
  {
    "seed": 1,
    "score": 0,
    "forfeit": true,
    "roster": {
      "id": 0
    },
    "winner": true,
    "stats": {
      "kills": 0,
      "placement": 0
    }
  }
]
```

<h3 id="/series/:id/participants-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1matches~1%7Bid%7D~1participants/put/requestBody/content/application~1json/schema/items](#schema#/paths/~1matches~1%7bid%7d~1participants/put/requestbody/content/application~1json/schema/items)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/participants-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## series/:id/rosters

<a id="opIdgetRostersBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/series/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/series/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/series/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /series/{id}/rosters`

Fetch all rosters participating in the series

<h3 id="series/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

<h3 id="series/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Rosters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="series/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /series/:id/scoring

<a id="opIddeleteScoringBySeriesId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/series/{id}/scoring',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/series/{id}/scoring', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/series/{id}/scoring", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /series/{id}/scoring`

Delete battle royale scoring for series from its id

<h3 id="/series/:id/scoring-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/series/:id/scoring-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-stages">STAGES</h1>

## /stages

<a id="opIdgetStages"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/stages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/stages', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/stages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /stages`

Fetch all stages

<h3 id="/stages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "tournament": {
      "id": 0
    },
    "order": 0,
    "substages": [
      {
        "id": 0,
        "stage": {
          "id": 0
        },
        "title": "string",
        "tier": 0,
        "type": 0,
        "phase": "qualifier",
        "tournament": {
          "id": 0
        },
        "order": 0,
        "start": "2020-06-24T09:20:48Z",
        "deleted_at": "2020-06-24T09:20:48Z"
      }
    ],
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="/stages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of stages.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/stages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Stage/allOf/0](#schemastage/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» order|integer|true|none|none|
|»» substages|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|
|»»»» id|integer|true|none|none|
|»»»» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» title|string|false|none|none|
|»»»» tier|integer|false|none|none|
|»»»» type|integer|false|none|none|
|»»»» phase|string|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»»» order|integer|true|none|none|
|»»»» start|string(date-time)¦null|true|none|none|
|»»»» deleted_at|string(date-time)¦null|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /stages/:id

<a id="opIddeleteStageById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/stages/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/stages/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/stages/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /stages/{id}`

Delete stage from its id

<h3 id="/stages/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/stages/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## stages/:id/substages

<a id="opIdgetSubstagesByStageId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/stages/{id}/substages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/stages/{id}/substages', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/stages/{id}/substages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /stages/{id}/substages`

Fetch all substages in the stage

<h3 id="stages/:id/substages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "stage": {
      "id": 0
    },
    "title": "string",
    "tier": 0,
    "type": 0,
    "phase": "qualifier",
    "tournament": {
      "id": 0
    },
    "order": 0,
    "start": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="stages/:id/substages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of substages.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="stages/:id/substages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|
|»» id|integer|true|none|none|
|»» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|
|»» title|string|false|none|none|
|»» tier|integer|false|none|none|
|»» type|integer|false|none|none|
|»» phase|string|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» order|integer|true|none|none|
|»» start|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-substages">SUBSTAGES</h1>

## /substages

<a id="opIdgetSubstages"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/substages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/substages', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/substages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /substages`

Fetch all substages

<h3 id="/substages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "stage": {
      "id": 0
    },
    "title": "string",
    "tier": 0,
    "type": 0,
    "phase": "qualifier",
    "tournament": {
      "id": 0
    },
    "order": 0,
    "start": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="/substages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of substages.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/substages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|
|»» id|integer|true|none|none|
|»» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|
|»» title|string|false|none|none|
|»» tier|integer|false|none|none|
|»» type|integer|false|none|none|
|»» phase|string|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» order|integer|true|none|none|
|»» start|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /substages/:id

<a id="opIddeleteSubstageById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/substages/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/substages/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/substages/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /substages/{id}`

Delete substage from its id

<h3 id="/substages/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/substages/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## substages/:id/rosters

<a id="opIdgetRostersBySubstageid"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/substages/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/substages/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/substages/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /substages/{id}/rosters`

Fetch all rosters in the substage

<h3 id="substages/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

<h3 id="substages/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of rosters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="substages/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /substages/:id/rosters

<a id="opIdupdateRostersBySubstageId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/substages/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/substages/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/substages/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /substages/{id}/rosters`

Update substage rosters

> Body parameter

```json
[
  {
    "id": 0
  }
]
```

<h3 id="/substages/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/substages/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## substages/:id/series

<a id="opIdgetSeriesBySubstageId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/substages/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/substages/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/substages/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /substages/{id}/series`

Fetch all series in the substage

<h3 id="substages/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

<h3 id="substages/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of series.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="substages/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-players">PLAYERS</h1>

## /players

<a id="opIdgetPlayers"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players`

Fetch all players

<h3 id="/players-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "first_name": "string",
    "last_name": "string",
    "nick_name": "string",
    "active": true,
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    ],
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "game": {
      "id": 0
    },
    "race": {
      "id": 0,
      "name": "string",
      "game": {
        "id": 0
      }
    },
    "role": {
      "id": 0
    },
    "teams": [
      {
        "id": 0
      }
    ],
    "social_media_accounts": [
      {
        "handle": "string",
        "url": "string",
        "platform": {
          "id": 0,
          "name": "string",
          "slug": "string"
        }
      }
    ],
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="/players-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Players.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/players-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Player/allOf/0](#schemaplayer/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» first_name|string¦null|false|none|none|
|»» last_name|string¦null|false|none|none|
|»» nick_name|string|false|none|none|
|»» active|boolean|false|none|none|
|»» images|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»» id|integer|true|read-only|none|
|»»»» url|string|true|none|none|
|»»»» thumbnail|string|true|none|none|
|»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|false|none|none|
|»»» name|string|true|none|none|
|»»» abbreviation|string|true|none|none|
|»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|The name of the Country.|
|»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|
|»» race|[#/paths/~1games~1%7Bid%7D~1races/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1games~1%7bid%7d~1races/get/responses/200/content/application~1json/schema/items)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» role|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» teams|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|none|
|»» social_media_accounts|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[SocialMediaAccount/allOf/0](#schemasocialmediaaccount/allof/0)|false|none|none|
|»»»» handle|string|false|none|none|
|»»»» url|string|true|read-only|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» platform|[SocialMediaAccount/allOf/1/properties/platform](#schemasocialmediaaccount/allof/1/properties/platform)|true|none|none|
|»»»»» id|integer|true|none|none|
|»»»»» name|string|true|none|none|
|»»»»» slug|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /players/:id

<a id="opIddeletePlayerById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/players/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/players/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/players/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /players/{id}`

Delete player from its id

<h3 id="/players/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/players/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /players/:id/lineups

<a id="opIdgetLineupsByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players/{id}/lineups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players/{id}/lineups', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players/{id}/lineups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players/{id}/lineups`

Fetch lineups that the player has been part of

<h3 id="/players/:id/lineups-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "players": [
      {
        "id": 0
      }
    ]
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/players/:id/lineups-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Lineups.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/players/:id/lineups-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)]|false|none|none|
|» id|integer|true|read-only|none|
|» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## players/:id/rosters

<a id="opIdgetRostersByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players/{id}/rosters`

Fetch all rosters the player has been part of

<h3 id="players/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

<h3 id="players/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Rosters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="players/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## players/:id/series

<a id="opIdgetSeriesByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players/{id}/series`

Fetch all series the player has participated in

<h3 id="players/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

<h3 id="players/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of series.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="players/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /players/:id/eids

<a id="opIdgetEidsByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players/{id}/eids',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players/{id}/eids', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players/{id}/eids", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players/{id}/eids`

Fetch player eids from its id

<h3 id="/players/:id/eids-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "platform": {
      "id": 0,
      "name": "string"
    },
    "eids": [
      "string"
    ]
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/players/:id/eids-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of player eids associated with their platforms|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|A list of player eids associated with their platforms for a soft-deleted player|Inline|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/players/:id/eids-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1players~1%7Bid%7D~1eids/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1players~1%7bid%7d~1eids/get/responses/200/content/application~1json/schema/items)]|false|none|none|
|» platform|object|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|» eids|[string]|true|none|none|

Status Code **410**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1players~1%7Bid%7D~1eids/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1players~1%7bid%7d~1eids/get/responses/200/content/application~1json/schema/items)]|false|none|none|
|» platform|object|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|» eids|[string]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /players/:id/roles

<a id="opIdcreateRoleByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.post 'https://atlas.abiosgaming.com/v3/players/{id}/roles',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.post('https://atlas.abiosgaming.com/v3/players/{id}/roles', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://atlas.abiosgaming.com/v3/players/{id}/roles", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /players/{id}/roles`

Create a role for player

> Body parameter

```json
{
  "role": {
    "id": 0
  },
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z"
}
```

<h3 id="/players/:id/roles-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1players~1%7Bid%7D~1roles/post/requestBody/content/application~1json/schema](#schema#/paths/~1players~1%7bid%7d~1roles/post/requestbody/content/application~1json/schema)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/players/:id/roles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## players/:id/rolehistory

<a id="opIdgetRoleHistoryByPlayerId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/players/{id}/rolehistory',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/players/{id}/rolehistory', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/players/{id}/rolehistory", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /players/{id}/rolehistory`

Fetch all roles the player had

<h3 id="players/:id/rolehistory-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "role": {
      "id": 0
    },
    "from": "2020-06-24T09:20:48Z",
    "to": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="players/:id/rolehistory-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of RoleHistory.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="players/:id/rolehistory-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /players/:id/roles/:role_id

<a id="opIdupdateRoleByIdWithPlayerById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/players/{id}/roles/{role_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/players/{id}/roles/{role_id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/players/{id}/roles/{role_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /players/{id}/roles/{role_id}`

Update role for player

> Body parameter

```json
{
  "role": {
    "id": 0
  },
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z"
}
```

<h3 id="/players/:id/roles/:role_id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|role_id|path|integer|true|none|
|body|body|[#/paths/~1players~1%7Bid%7D~1roles/post/requestBody/content/application~1json/schema](#schema#/paths/~1players~1%7bid%7d~1roles/post/requestbody/content/application~1json/schema)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/players/:id/roles/:role_id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-organisations">ORGANISATIONS</h1>

## /organisations

<a id="opIdgetOrganisations"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/organisations',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/organisations', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/organisations", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /organisations`

Fetch all organisations

<h3 id="/organisations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "teams": [
      {
        "id": 0
      }
    ]
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/organisations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of organisations.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/organisations-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[#/paths/~1organisations/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1organisations/get/responses/200/content/application~1json/schema/items)]|false|none|none|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|true|none|none|
|»» name|string|true|none|none|
|»» abbreviation|string|true|none|none|
|»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|The name of the Country.|
|»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»» id|integer|true|read-only|none|
|»»»»» url|string|true|none|none|
|»»»»» thumbnail|string|true|none|none|
|»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» teams|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» id|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /organisations/:id

<a id="opIdgetOrganisationById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/organisations/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/organisations/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/organisations/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /organisations/{id}`

Fetch one organisation from its id

<h3 id="/organisations/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "name": "string",
  "region": {
    "name": "string",
    "abbreviation": "string",
    "country": {
      "id": 0,
      "name": "string",
      "abbreviation": "strin",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  },
  "teams": [
    {
      "id": 0
    }
  ]
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/organisations/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An Organisation.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/organisations/:id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|true|none|none|
|»» name|string|true|none|none|
|»» abbreviation|string|true|none|none|
|»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|The name of the Country.|
|»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»» id|integer|true|read-only|none|
|»»»»» url|string|true|none|none|
|»»»»» thumbnail|string|true|none|none|
|»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» teams|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» id|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-teams">TEAMS</h1>

## /teams

<a id="opIdgetTeams"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/teams',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/teams', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/teams", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /teams`

Fetch all teams

<h3 id="/teams-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "abbreviation": "string",
    "active": true,
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "game": {
      "id": 0
    },
    "deleted_at": "2020-06-24T09:20:48Z",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    ],
    "social_media_accounts": [
      {
        "handle": "string",
        "url": "string",
        "platform": {
          "id": 0,
          "name": "string",
          "slug": "string"
        }
      }
    ],
    "standing_roster": {
      "id": 0,
      "from": "2020-06-24T09:20:48Z",
      "to": "2020-06-24T09:20:48Z",
      "roster": {
        "id": 0
      },
      "deleted_at": "2020-06-24T09:20:48Z"
    },
    "organisation": {
      "id": 0
    }
  }
]
```

<h3 id="/teams-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of teams.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/teams-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Team/allOf/0](#schemateam/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» name|string|false|none|none|
|»» abbreviation|string|false|none|none|
|»» active|boolean|false|none|none|
|»» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|false|none|none|
|»»» name|string|true|none|none|
|»»» abbreviation|string|true|none|none|
|»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|The name of the Country.|
|»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»»» id|integer|true|read-only|none|
|»»»»»» url|string|true|none|none|
|»»»»»» thumbnail|string|true|none|none|
|»»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» social_media_accounts|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[SocialMediaAccount/allOf/0](#schemasocialmediaaccount/allof/0)|false|none|none|
|»»»» handle|string|false|none|none|
|»»»» url|string|true|read-only|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» platform|[SocialMediaAccount/allOf/1/properties/platform](#schemasocialmediaaccount/allof/1/properties/platform)|true|none|none|
|»»»»» id|integer|true|none|none|
|»»»»» name|string|true|none|none|
|»»»»» slug|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» standing_roster|any|true|none|none|
|»» organisation|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|
|»»» id|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /teams/:id

<a id="opIdpatchTeamById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.patch 'https://atlas.abiosgaming.com/v3/teams/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.patch('https://atlas.abiosgaming.com/v3/teams/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://atlas.abiosgaming.com/v3/teams/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /teams/{id}`

Patch team

> Body parameter

```json
[
  {
    "op": "replace",
    "path": "/name",
    "value": "name"
  }
]
```

<h3 id="/teams/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|array[any]|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/teams/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /teams/:id/rosters

<a id="opIdgetRostersByTeamId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/teams/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/teams/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/teams/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /teams/{id}/rosters`

Fetch available rosters for team from its id

<h3 id="/teams/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/teams/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of rosters|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|A list of rosters for soft-deleted team|Inline|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/teams/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

Status Code **410**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /teams/:id/series

<a id="opIdgetSeriesByTeamId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/teams/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/teams/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/teams/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /teams/{id}/series`

Fetch available series for team from its id

<h3 id="/teams/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/teams/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of series|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|A list of series for soft-deleted team|Inline|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/teams/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

Status Code **410**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|410|Location|string||Link to next page|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-standing-rosters">STANDING ROSTERS</h1>

## /standingrosters/:id

<a id="opIdgetStandingRosterById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/standingrosters/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/standingrosters/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/standingrosters/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /standingrosters/{id}`

Fetch a standing roster from its id

<h3 id="/standingrosters/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z",
  "roster": {
    "id": 0
  },
  "deleted_at": "2020-06-24T09:20:48Z"
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/standingrosters/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A standing roster|[Team/allOf/1/properties/standing_roster/allOf/0](#schemateam/allof/1/properties/standing_roster/allof/0)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|A soft-deleted standing roster|[Team/allOf/1/properties/standing_roster/allOf/0](#schemateam/allof/1/properties/standing_roster/allof/0)|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /teams/:id/standingrosters

<a id="opIdgetStandingRostersByTeamId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /teams/{id}/standingrosters`

Fetch available standing rosters for a team from its id

<h3 id="/teams/:id/standingrosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "from": "2020-06-24T09:20:48Z",
    "to": "2020-06-24T09:20:48Z",
    "roster": {
      "id": 0
    },
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/teams/:id/standingrosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of standing rosters|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|A list of standing rosters for soft-deleted team|Inline|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/teams/:id/standingrosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[StandingRoster/allOf/0](#schemastandingroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» from|string(date-time)|false|none|none|
|»» to|string(date-time)¦null|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» id|integer|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|

Status Code **410**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[StandingRoster/allOf/0](#schemastandingroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» from|string(date-time)|false|none|none|
|»» to|string(date-time)¦null|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» id|integer|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /teams/:id/standingrosters/:standingroster_id

<a id="opIdupdateStandingRostersByIdWithTeamById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters/{standingroster_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters/{standingroster_id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/teams/{id}/standingrosters/{standingroster_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /teams/{id}/standingrosters/{standingroster_id}`

Update standing roster

> Body parameter

```json
{
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z"
}
```

<h3 id="/teams/:id/standingrosters/:standingroster_id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|standingroster_id|path|integer|true|none|
|body|body|any|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/teams/:id/standingrosters/:standingroster_id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-streams">STREAMS</h1>

## /streams

<a id="opIdgetStreams"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/streams',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/streams', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/streams", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /streams`

Fetch all streams

<h3 id="/streams-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "username": "string",
    "display_name": "string",
    "status_text": "string",
    "viewer_count": 0,
    "online": true,
    "last_online": "2020-06-24T09:20:48Z",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "external"
      }
    ],
    "platform": {
      "id": 0,
      "name": "string",
      "color": "string",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  }
]
```

<h3 id="/streams-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of streams.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/streams-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Caster/allOf/1/properties/stream/allOf/0](#schemacaster/allof/1/properties/stream/allof/0)]|false|none|none|
|» id|integer|true|none|none|
|» username|string¦null|true|none|none|
|» display_name|string|true|none|none|
|» status_text|string¦null|true|none|none|
|» viewer_count|integer|true|none|none|
|» online|boolean|true|none|none|
|» last_online|string(date-time)¦null|true|none|none|
|» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» url|string|true|none|none|
|»»» thumbnail|string|true|none|none|
|»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Stream/properties/images/items/allOf/1](#schemastream/properties/images/items/allof/1)|false|none|none|
|»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|»» color|string¦null|true|none|none|
|»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|external|
|type|default|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-tournaments">TOURNAMENTS</h1>

## /tournaments

<a id="opIdgetTournaments"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/tournaments',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/tournaments', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/tournaments", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tournaments`

Fetch all tournaments

<h3 id="/tournaments-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "short_title": "string",
    "tier": 0,
    "copy": {
      "general_description": "string",
      "short_description": "string",
      "format_description": "string"
    },
    "links": {
      "website": "string",
      "wiki": "string"
    },
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "game": {
      "id": 0
    },
    "string_prize_pool": {
      "total": "string",
      "first": "string",
      "second": "string",
      "third": "string"
    },
    "location": {
      "host": {
        "name": "string",
        "abbreviation": "string",
        "country": {
          "id": 0,
          "name": "string",
          "abbreviation": "strin",
          "images": [
            {
              "id": 0,
              "url": "string",
              "thumbnail": "string",
              "fallback": true,
              "type": "default"
            }
          ]
        }
      },
      "participants": [
        {
          "name": "string",
          "abbreviation": "string",
          "country": {
            "id": 0,
            "name": "string",
            "abbreviation": "strin",
            "images": [
              {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            ]
          }
        }
      ]
    },
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    ],
    "stages": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "default": true,
        "caster": {
          "id": 0
        }
      }
    ]
  }
]
```

<h3 id="/tournaments-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of tournaments.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/tournaments-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Tournament/allOf/0/allOf/0](#schematournament/allof/0/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» short_title|string|false|none|none|
|»» tier|integer|false|none|none|
|»» copy|object|false|none|none|
|»»» general_description|string|true|none|none|
|»»» short_description|string|true|none|none|
|»»» format_description|string|true|none|none|
|»» links|object|false|none|none|
|»»» website|string¦null|true|none|none|
|»»» wiki|string¦null|true|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|
|»» string_prize_pool|object|false|none|none|
|»»» total|string¦null|true|none|none|
|»»» first|string¦null|true|none|none|
|»»» second|string¦null|true|none|none|
|»»» third|string¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» location|object|true|none|none|
|»»» host|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)|true|none|none|
|»»»» name|string|true|none|none|
|»»»» abbreviation|string|true|none|none|
|»»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»»» id|integer|true|none|none|
|»»»»» name|string|true|none|The name of the Country.|
|»»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»»»» id|integer|true|read-only|none|
|»»»»»»» url|string|true|none|none|
|»»»»»»» thumbnail|string|true|none|none|
|»»»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» participants|[[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)]|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[TournamentPatchImages/allOf/1/properties/value/items/allOf/1](#schematournamentpatchimages/allof/1/properties/value/items/allof/1)|false|none|none|
|»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» stages|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[#/paths/~1tournaments~1%7Bid%7D~1casters/put/requestBody/content/application~1json/schema/items](#schema#/paths/~1tournaments~1%7bid%7d~1casters/put/requestbody/content/application~1json/schema/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» default|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|
|type|small|
|type|large|
|type|square|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /tournaments/:id

<a id="opIddeleteTournamentById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/tournaments/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/tournaments/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/tournaments/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /tournaments/{id}`

Delete tournament from its id

<h3 id="/tournaments/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/tournaments/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## tournaments/:id/casters

<a id="opIdgetCastersByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/tournaments/{id}/casters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/tournaments/{id}/casters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/tournaments/{id}/casters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tournaments/{id}/casters`

Fetch all casters of the tournament

<h3 id="tournaments/:id/casters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "display_name": "string",
    "username": "string",
    "game": {
      "id": 0
    },
    "platform": {
      "id": 0,
      "name": "string",
      "color": "string",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    },
    "stream": {
      "id": 0,
      "username": "string",
      "display_name": "string",
      "status_text": "string",
      "viewer_count": 0,
      "online": true,
      "last_online": "2020-06-24T09:20:48Z",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "external"
        }
      ],
      "platform": {
        "id": 0,
        "name": "string",
        "color": "string",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    }
  }
]
```

<h3 id="tournaments/:id/casters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Casters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="tournaments/:id/casters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Caster/allOf/0](#schemacaster/allof/0)|false|none|A caster is an individual shoutcaster casting a series. It will have a stream associated with it.|
|»» id|integer|true|read-only|The internal id of the caster.|
|»» display_name|string|false|none|The name of the caster.|
|»» username|string|false|none|The username of the caster|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» color|string¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»» id|integer|true|read-only|none|
|»»»»» url|string|true|none|none|
|»»»»» thumbnail|string|true|none|none|
|»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» stream|[Caster/allOf/1/properties/stream/allOf/0](#schemacaster/allof/1/properties/stream/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» username|string¦null|true|none|none|
|»»» display_name|string|true|none|none|
|»»» status_text|string¦null|true|none|none|
|»»» viewer_count|integer|true|none|none|
|»»» online|boolean|true|none|none|
|»»» last_online|string(date-time)¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Stream/properties/images/items/allOf/1](#schemastream/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|none|
|»»»» color|string¦null|true|none|none|
|»»»» images|[allOf]|true|none|none|
|»» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|true|none|none|
|»»» name|string|true|none|none|
|»»» abbreviation|string|true|none|none|
|»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|The name of the Country.|
|»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|
|type|external|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /tournaments/:id/casters

<a id="opIdupdateCastersByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/tournaments/{id}/casters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/tournaments/{id}/casters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/tournaments/{id}/casters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /tournaments/{id}/casters`

Update tournament casters

> Body parameter

```json
[
  {
    "primary": true,
    "default": true,
    "caster": {
      "id": 0
    }
  }
]
```

<h3 id="/tournaments/:id/casters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1tournaments~1%7Bid%7D~1casters/put/requestBody/content/application~1json/schema/items](#schema#/paths/~1tournaments~1%7bid%7d~1casters/put/requestbody/content/application~1json/schema/items)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/tournaments/:id/casters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## tournaments/:id/stages

<a id="opIdgetStagesByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/tournaments/{id}/stages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/tournaments/{id}/stages', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/tournaments/{id}/stages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tournaments/{id}/stages`

Fetch all stages of the tournament

<h3 id="tournaments/:id/stages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "tournament": {
      "id": 0
    },
    "order": 0,
    "substages": [
      {
        "id": 0,
        "stage": {
          "id": 0
        },
        "title": "string",
        "tier": 0,
        "type": 0,
        "phase": "qualifier",
        "tournament": {
          "id": 0
        },
        "order": 0,
        "start": "2020-06-24T09:20:48Z",
        "deleted_at": "2020-06-24T09:20:48Z"
      }
    ],
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="tournaments/:id/stages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of stages.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="tournaments/:id/stages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Stage/allOf/0](#schemastage/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» order|integer|true|none|none|
|»» substages|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|
|»»»» id|integer|true|none|none|
|»»»» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» title|string|false|none|none|
|»»»» tier|integer|false|none|none|
|»»»» type|integer|false|none|none|
|»»»» phase|string|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»»» order|integer|true|none|none|
|»»»» start|string(date-time)¦null|true|none|none|
|»»»» deleted_at|string(date-time)¦null|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## tournaments/:id/substages

<a id="opIdgetSubstagesByTournamentid"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/tournaments/{id}/substages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/tournaments/{id}/substages', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/tournaments/{id}/substages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tournaments/{id}/substages`

Fetch all substages of the tournament

<h3 id="tournaments/:id/substages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "stage": {
      "id": 0
    },
    "title": "string",
    "tier": 0,
    "type": 0,
    "phase": "qualifier",
    "tournament": {
      "id": 0
    },
    "order": 0,
    "start": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z"
  }
]
```

<h3 id="tournaments/:id/substages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of substages.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="tournaments/:id/substages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|
|»» id|integer|true|none|none|
|»» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|
|»» title|string|false|none|none|
|»» tier|integer|false|none|none|
|»» type|integer|false|none|none|
|»» phase|string|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» order|integer|true|none|none|
|»» start|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## tournaments/:id/series

<a id="opIdgetSeriesByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-IdSpace' => 'kambi',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/tournaments/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-IdSpace': 'kambi',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/tournaments/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-IdSpace": []string{"kambi"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/tournaments/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tournaments/{id}/series`

Fetch all series of the tournament

<h3 id="tournaments/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|
|Abios-IdSpace|header|string|false|Which id space is in use for this query. Is chosen over the query parameter|
|id_space|query|string|false|Which id space is in use for this query. Is chosen after the header.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|
|Abios-IdSpace|kambi|
|Abios-IdSpace|gig|
|Abios-IdSpace|sbtech|
|Abios-IdSpace|stoiximan|
|Abios-IdSpace|betfan|
|id_space|kambi|
|id_space|gig|
|id_space|sbtech|
|id_space|stoiximan|
|id_space|betfan|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

<h3 id="tournaments/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of series.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="tournaments/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /tournaments/:id/note

<a id="opIdupdateNoteByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/tournaments/{id}/note',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/tournaments/{id}/note', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/tournaments/{id}/note", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /tournaments/{id}/note`

Update tournament note

> Body parameter

```json
{
  "note": "string",
  "user": {
    "id": 0
  }
}
```

<h3 id="/tournaments/:id/note-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|[#/paths/~1series~1%7Bid%7D~1note/put/requestBody/content/application~1json/schema](#schema#/paths/~1series~1%7bid%7d~1note/put/requestbody/content/application~1json/schema)|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/tournaments/:id/note-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /tournaments/:id/tickets

<a id="opIdupdateTicketsByTournamentId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/tournaments/{id}/tickets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/tournaments/{id}/tickets', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/tournaments/{id}/tickets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /tournaments/{id}/tickets`

Update tournament tickets

> Body parameter

```json
[
  0
]
```

<h3 id="/tournaments/:id/tickets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|body|body|array[integer]|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/tournaments/:id/tickets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-casters">CASTERS</h1>

## /casters

<a id="opIdgetCasters"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/casters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/casters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/casters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /casters`

Fetch all casters

<h3 id="/casters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "display_name": "string",
    "username": "string",
    "game": {
      "id": 0
    },
    "platform": {
      "id": 0,
      "name": "string",
      "color": "string",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    },
    "stream": {
      "id": 0,
      "username": "string",
      "display_name": "string",
      "status_text": "string",
      "viewer_count": 0,
      "online": true,
      "last_online": "2020-06-24T09:20:48Z",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "external"
        }
      ],
      "platform": {
        "id": 0,
        "name": "string",
        "color": "string",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "region": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    }
  }
]
```

<h3 id="/casters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Casters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/casters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Caster/allOf/0](#schemacaster/allof/0)|false|none|A caster is an individual shoutcaster casting a series. It will have a stream associated with it.|
|»» id|integer|true|read-only|The internal id of the caster.|
|»» display_name|string|false|none|The name of the caster.|
|»» username|string|false|none|The username of the caster|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» name|string|true|none|none|
|»»» color|string¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|
|»»»»» id|integer|true|read-only|none|
|»»»»» url|string|true|none|none|
|»»»»» thumbnail|string|true|none|none|
|»»»»» fallback|boolean|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» stream|[Caster/allOf/1/properties/stream/allOf/0](#schemacaster/allof/1/properties/stream/allof/0)¦null|true|none|none|
|»»» id|integer|true|none|none|
|»»» username|string¦null|true|none|none|
|»»» display_name|string|true|none|none|
|»»» status_text|string¦null|true|none|none|
|»»» viewer_count|integer|true|none|none|
|»»» online|boolean|true|none|none|
|»»» last_online|string(date-time)¦null|true|none|none|
|»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[Stream/properties/images/items/allOf/1](#schemastream/properties/images/items/allof/1)|false|none|none|
|»»»»» type|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|none|
|»»»» color|string¦null|true|none|none|
|»»»» images|[allOf]|true|none|none|
|»» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|true|none|none|
|»»» name|string|true|none|none|
|»»» abbreviation|string|true|none|none|
|»»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|
|»»»» id|integer|true|none|none|
|»»»» name|string|true|none|The name of the Country.|
|»»»» abbreviation|string|true|none|The Country's abbreviation.|
|»»»» images|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|
|type|external|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /casters/:id

<a id="opIddeleteCasterById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.delete 'https://atlas.abiosgaming.com/v3/casters/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.delete('https://atlas.abiosgaming.com/v3/casters/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://atlas.abiosgaming.com/v3/casters/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /casters/{id}`

Delete caster from its id

<h3 id="/casters/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/casters/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## /casters/:id/restore

<a id="opIdrestoreCasterById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.put 'https://atlas.abiosgaming.com/v3/casters/{id}/restore',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.put('https://atlas.abiosgaming.com/v3/casters/{id}/restore', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://atlas.abiosgaming.com/v3/casters/{id}/restore", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /casters/{id}/restore`

Restore caster from its id

<h3 id="/casters/:id/restore-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/casters/:id/restore-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|410|[Gone](https://tools.ietf.org/html/rfc7231#section-6.5.9)|Gone|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-lineups">LINEUPS</h1>

## /lineups/:id

<a id="opIdgetLineupById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/lineups/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/lineups/{id}', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/lineups/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /lineups/{id}`

Fetch one lineup from its id

<h3 id="/lineups/:id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "players": [
    {
      "id": 0
    }
  ]
}
```

> 400 Response

```json
{
  "msg": "Invalid id."
}
```

<h3 id="/lineups/:id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A Lineup.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[#/components/responses/400/content/application~1json/schema](#schema#/components/responses/400/content/application~1json/schema)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/lineups/:id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|true|read-only|none|
|» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» id|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## lineups/:id/rosters

<a id="opIdgetRostersByLineupId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/lineups/{id}/rosters',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/lineups/{id}/rosters', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/lineups/{id}/rosters", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /lineups/{id}/rosters`

Fetch all rosters the lineups has been part of

<h3 id="lineups/:id/rosters-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "team": {
      "id": 0
    },
    "line_up": {
      "id": 0,
      "players": [
        {
          "id": 0
        }
      ]
    }
  }
]
```

<h3 id="lineups/:id/rosters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of Rosters.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="lineups/:id/rosters-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Roster/allOf/0](#schemaroster/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|»»» id|integer|true|none|none|
|»» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|
|»»» id|integer|true|read-only|none|
|»»» players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»»»» id|integer|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

## lineups/:id/series

<a id="opIdgetSeriesByLineupId"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/lineups/{id}/series',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/lineups/{id}/series', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/lineups/{id}/series", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /lineups/{id}/series`

Fetch all series the lineup has participated in

<h3 id="lineups/:id/series-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|id|path|integer|true|Resource id|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "title": "string",
    "start": "2020-06-24T09:20:48Z",
    "end": "2020-06-24T09:20:48Z",
    "tier": 0,
    "best_of": 0,
    "chain": [
      {
        "id": 0
      }
    ],
    "streamed": true,
    "bracket_position": {
      "part": "UB",
      "col": 0,
      "offset": 0
    },
    "tournament": {
      "id": 0
    },
    "substage": {
      "id": 0
    },
    "game": {
      "id": 0
    },
    "postponed_from": "2020-06-24T09:20:48Z",
    "deleted_at": "2020-06-24T09:20:48Z",
    "coverage": {
      "full_postgame": "available",
      "light_postgame": "available",
      "light_live": "available"
    },
    "participants": [
      {
        "seed": 1,
        "score": 0,
        "forfeit": true,
        "roster": {
          "id": 0
        },
        "winner": true,
        "stats": {
          "kills": 0,
          "placement": 0
        }
      }
    ],
    "matches": [
      {
        "id": 0
      }
    ],
    "casters": [
      {
        "primary": true,
        "caster": {
          "id": 0
        }
      }
    ],
    "has_incident_report": true
  }
]
```

<h3 id="lineups/:id/series-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of series.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="lineups/:id/series-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Series/allOf/0](#schemaseries/allof/0)|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» tier|integer|false|none|none|
|»» best_of|integer|false|none|none|
|»» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|»»» id|integer|true|none|none|
|»» streamed|boolean|false|none|none|
|»» bracket_position|object¦null|false|none|none|
|»»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»»» col|integer|true|none|none|
|»»» offset|integer|true|none|none|
|»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» postponed_from|string(date-time)¦null|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» participants|[allOf]|true|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|
|»»»» seed|integer|false|none|none|
|»»»» score|integer¦null|false|none|none|
|»»»» forfeit|boolean|false|none|none|
|»»»» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»»»» winner|boolean|false|none|none|
|»»»» stats|object¦null|false|none|none|
|»»»»» kills|integer|true|none|none|
|»»»»» placement|integer¦null|true|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[Series/allOf/1/properties/casters/items](#schemaseries/allof/1/properties/casters/items)]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» has_incident_report|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|
|light_postgame|available|
|light_postgame|partial|
|light_postgame|expected|
|light_postgame|possible|
|light_postgame|deffered|
|light_postgame|unlikely|
|light_postgame|unavailable|
|light_postgame|unknown|
|light_live|available|
|light_live|partial|
|light_live|expected|
|light_live|possible|
|light_live|deffered|
|light_live|unlikely|
|light_live|unavailable|
|light_live|unknown|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

<h1 id="abios-rest-api-socialmedia">SOCIALMEDIA</h1>

## /socialmedia/platforms

<a id="opIdgetSocialMediaPlatforms"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'X-Authorization-Method' => 'abios-beta',
  'Abios-Secret' => 'API_KEY'
}

result = RestClient.get 'https://atlas.abiosgaming.com/v3/socialmedia/platforms',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'X-Authorization-Method': 'abios-beta',
  'Abios-Secret': 'API_KEY'
}

r = requests.get('https://atlas.abiosgaming.com/v3/socialmedia/platforms', headers = headers)

print(r.json())

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
        "X-Authorization-Method": []string{"abios-beta"},
        "Abios-Secret": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://atlas.abiosgaming.com/v3/socialmedia/platforms", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /socialmedia/platforms`

Fetch all social media platforms

<h3 id="/socialmedia/platforms-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|X-Authorization-Method|header|string|false|The method with which to authorize|
|skip|query|integer|false|Amount of results to skip|
|take|query|integer|false|Amount of results to take|

#### Enumerated Values

|Parameter|Value|
|---|---|
|X-Authorization-Method|abios-beta|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "name": "string",
    "slug": "string"
  }
]
```

<h3 id="/socialmedia/platforms-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A List of social media platforms.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|429|[Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)|Too Many Requests|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|None|

<h3 id="/socialmedia/platforms-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[SocialMediaAccount/allOf/1/properties/platform](#schemasocialmediaaccount/allof/1/properties/platform)]|false|none|none|
|» id|integer|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
header, query
</aside>

# Schemas

<h2 id="tocS_BattleRoyaleScoring">BattleRoyaleScoring</h2>

<a id="schemabattleroyalescoring"></a>
<a id="schema_BattleRoyaleScoring"></a>
<a id="tocSbattleroyalescoring"></a>
<a id="tocsbattleroyalescoring"></a>

```json
{
  "kill_multiplier": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|kill_multiplier|integer|false|none|none|

<h2 id="tocS_BracketPosition">BracketPosition</h2>

<a id="schemabracketposition"></a>
<a id="schema_BracketPosition"></a>
<a id="tocSbracketposition"></a>
<a id="tocsbracketposition"></a>

```json
{
  "part": "UB",
  "col": 0,
  "offset": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|part|string|true|none|none|
|col|integer|true|none|none|
|offset|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|part|UB|
|part|LB|
|part|GF|
|part|LF|

<h2 id="tocS_Caster">Caster</h2>

<a id="schemacaster"></a>
<a id="schema_Caster"></a>
<a id="tocScaster"></a>
<a id="tocscaster"></a>

```json
{
  "id": 0,
  "display_name": "string",
  "username": "string",
  "game": {
    "id": 0
  },
  "platform": {
    "id": 0,
    "name": "string",
    "color": "string",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    ]
  },
  "stream": {
    "id": 0,
    "username": "string",
    "display_name": "string",
    "status_text": "string",
    "viewer_count": 0,
    "online": true,
    "last_online": "2020-06-24T09:20:48Z",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "external"
      }
    ],
    "platform": {
      "id": 0,
      "name": "string",
      "color": "string",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  },
  "region": {
    "name": "string",
    "abbreviation": "string",
    "country": {
      "id": 0,
      "name": "string",
      "abbreviation": "strin",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|A caster is an individual shoutcaster casting a series. It will have a stream associated with it.|
|» id|integer|true|read-only|The internal id of the caster.|
|» display_name|string|false|none|The name of the caster.|
|» username|string|false|none|The username of the caster|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» platform|object¦null|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|»» color|string¦null|true|none|none|
|»» images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» stream|object¦null|true|none|none|
|»» id|integer|true|none|none|
|»» username|string¦null|true|none|none|
|»» display_name|string|true|none|none|
|»» status_text|string¦null|true|none|none|
|»» viewer_count|integer|true|none|none|
|»» online|boolean|true|none|none|
|»» last_online|string(date-time)¦null|true|none|none|
|»» images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Stream/properties/images/items/allOf/1](#schemastream/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|
|» region|object¦null|true|none|none|
|»» name|string|true|none|none|
|»» abbreviation|string|true|none|none|
|»» country|[#/paths/~1regions~1%7Bid%7D~1countries/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1regions~1%7bid%7d~1countries/get/responses/200/content/application~1json/schema/items)¦null|true|none|A Country, nationality, or language associated with a resource.|

<h2 id="tocS_CasterPatchDisplayName">CasterPatchDisplayName</h2>

<a id="schemacasterpatchdisplayname"></a>
<a id="schema_CasterPatchDisplayName"></a>
<a id="tocScasterpatchdisplayname"></a>
<a id="tocscasterpatchdisplayname"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_CasterPatchUsername">CasterPatchUsername</h2>

<a id="schemacasterpatchusername"></a>
<a id="schema_CasterPatchUsername"></a>
<a id="tocScasterpatchusername"></a>
<a id="tocscasterpatchusername"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_CasterPatchPlatform">CasterPatchPlatform</h2>

<a id="schemacasterpatchplatform"></a>
<a id="schema_CasterPatchPlatform"></a>
<a id="tocScasterpatchplatform"></a>
<a id="tocscasterpatchplatform"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_CasterPatchRegion">CasterPatchRegion</h2>

<a id="schemacasterpatchregion"></a>
<a id="schema_CasterPatchRegion"></a>
<a id="tocScasterpatchregion"></a>
<a id="tocscasterpatchregion"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0,
    "country": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|any|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_CasterPatchStream">CasterPatchStream</h2>

<a id="schemacasterpatchstream"></a>
<a id="schema_CasterPatchStream"></a>
<a id="tocScasterpatchstream"></a>
<a id="tocscasterpatchstream"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_Chain">Chain</h2>

<a id="schemachain"></a>
<a id="schema_Chain"></a>
<a id="tocSchain"></a>
<a id="tocschain"></a>

```json
[
  {
    "id": 0
  }
]

```

The chain accounts for where the series belongs in a chain of series

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|The chain accounts for where the series belongs in a chain of series|

<h2 id="tocS_Country">Country</h2>

<a id="schemacountry"></a>
<a id="schema_Country"></a>
<a id="tocScountry"></a>
<a id="tocscountry"></a>

```json
{
  "id": 0,
  "name": "string",
  "abbreviation": "strin",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "default"
    }
  ]
}

```

A Country, nationality, or language associated with a resource.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|The name of the Country.|
|abbreviation|string|true|none|The Country's abbreviation.|
|images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|default|

<h2 id="tocS_Coverage">Coverage</h2>

<a id="schemacoverage"></a>
<a id="schema_Coverage"></a>
<a id="tocScoverage"></a>
<a id="tocscoverage"></a>

```json
{
  "full_postgame": "available",
  "light_postgame": "available",
  "light_live": "available"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|full_postgame|string|true|none|none|
|light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|full_postgame|available|
|full_postgame|partial|
|full_postgame|expected|
|full_postgame|possible|
|full_postgame|deffered|
|full_postgame|unlikely|
|full_postgame|unavailable|
|full_postgame|unknown|

<h2 id="tocS_Error">Error</h2>

<a id="schemaerror"></a>
<a id="schema_Error"></a>
<a id="tocSerror"></a>
<a id="tocserror"></a>

```json
{
  "msg": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|msg|string|true|none|none|

<h2 id="tocS_Game">Game</h2>

<a id="schemagame"></a>
<a id="schema_Game"></a>
<a id="tocSgame"></a>
<a id="tocsgame"></a>

```json
{
  "id": 0,
  "abbreviation": "string",
  "title": "string",
  "default_match_type": "team",
  "default_map": {
    "id": 0
  },
  "defaults": {
    "match_type": "team",
    "map": {
      "id": 0,
      "name": "string",
      "external_name": "string",
      "official": true,
      "game": {
        "id": 0
      }
    },
    "lineup_size": 1
  },
  "deleted_at": "2020-06-24T09:20:48Z",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "circle"
    }
  ],
  "color": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|abbreviation|string|true|none|none|
|title|string|true|none|none|
|default_match_type|string|true|none|none|
|default_map|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|
|defaults|object|true|none|none|
|» match_type|[Game/properties/default_match_type](#schemagame/properties/default_match_type)|true|none|none|
|» map|object¦null|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|»» external_name|string¦null|false|none|none|
|»» official|boolean|true|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» lineup_size|integer¦null|true|none|none|
|deleted_at|string(date-time)¦null|true|none|none|
|images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» type|string|true|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|color|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|default_match_type|team|
|default_match_type|player|
|default_match_type|brawl|
|default_match_type|battle_royale|
|type|circle|
|type|square|
|type|rectangle|

<h2 id="tocS_GameAsset">GameAsset</h2>

<a id="schemagameasset"></a>
<a id="schema_GameAsset"></a>
<a id="tocSgameasset"></a>
<a id="tocsgameasset"></a>

```json
{
  "id": 0,
  "name": "string",
  "external_id": 0,
  "external_string_id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|external_id|integer¦null|false|none|none|
|external_string_id|string¦null|false|none|none|

<h2 id="tocS_CSGOGameAssets">CSGOGameAssets</h2>

<a id="schemacsgogameassets"></a>
<a id="schema_CSGOGameAssets"></a>
<a id="tocScsgogameassets"></a>
<a id="tocscsgogameassets"></a>

```json
{
  "weapons": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    }
  ],
  "win_reasons": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|weapons|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|»» external_id|integer¦null|false|none|none|
|»» external_string_id|string¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|win_reasons|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|small|
|type|grey|
|type|outline|
|type|white|
|type|small|

<h2 id="tocS_Dota2GameAssets">Dota2GameAssets</h2>

<a id="schemadota2gameassets"></a>
<a id="schema_Dota2GameAssets"></a>
<a id="tocSdota2gameassets"></a>
<a id="tocsdota2gameassets"></a>

```json
{
  "items": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    }
  ],
  "runes": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    }
  ],
  "spells": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    }
  ],
  "heroes": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "small"
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|runes|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|spells|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|heroes|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» id|integer|true|read-only|none|
|»»»» url|string|true|none|none|
|»»»» thumbnail|string|true|none|none|
|»»»» fallback|boolean|true|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|small|
|type|large|

<h2 id="tocS_LolGameAssets">LolGameAssets</h2>

<a id="schemalolgameassets"></a>
<a id="schema_LolGameAssets"></a>
<a id="tocSlolgameassets"></a>
<a id="tocslolgameassets"></a>

```json
{
  "items": {
    "id": 0,
    "name": "string",
    "external_id": 0,
    "external_string_id": "string",
    "images": {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "default"
    }
  },
  "champions": [
    {
      "id": 0,
      "name": "string",
      "external_id": 0,
      "external_string_id": "string",
      "images": {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|any|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|champions|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CSGOGameAssets/properties/weapons/items/allOf/0](#schemacsgogameassets/properties/weapons/items/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» images|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

<h2 id="tocS_Image">Image</h2>

<a id="schemaimage"></a>
<a id="schema_Image"></a>
<a id="tocSimage"></a>
<a id="tocsimage"></a>

```json
{
  "id": 0,
  "url": "string",
  "thumbnail": "string",
  "fallback": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|read-only|none|
|url|string|true|none|none|
|thumbnail|string|true|none|none|
|fallback|boolean|true|none|none|

<h2 id="tocS_Incident">Incident</h2>

<a id="schemaincident"></a>
<a id="schema_Incident"></a>
<a id="tocSincident"></a>
<a id="tocsincident"></a>

```json
{
  "id": 0,
  "series": {
    "id": 0
  },
  "match": {
    "id": 0
  },
  "comment": "string",
  "game": {
    "id": 0
  },
  "tournament": {
    "id": 0
  },
  "created_at": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» series|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» match|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|
|» comment|string|true|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» created_at|string(date-time)|true|none|none|

<h2 id="tocS_Lineup">Lineup</h2>

<a id="schemalineup"></a>
<a id="schema_Lineup"></a>
<a id="tocSlineup"></a>
<a id="tocslineup"></a>

```json
{
  "id": 0,
  "players": [
    {
      "id": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|read-only|none|
|players|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|

<h2 id="tocS_Map">Map</h2>

<a id="schemamap"></a>
<a id="schema_Map"></a>
<a id="tocSmap"></a>
<a id="tocsmap"></a>

```json
{
  "id": 0,
  "name": "string",
  "external_name": "string",
  "official": true,
  "game": {
    "id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|external_name|string¦null|false|none|none|
|official|boolean|true|none|none|
|game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

<h2 id="tocS_MapPool">MapPool</h2>

<a id="schemamappool"></a>
<a id="schema_MapPool"></a>
<a id="tocSmappool"></a>
<a id="tocsmappool"></a>

```json
{
  "id": 0,
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z",
  "maps": [
    {
      "id": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|from|string(date-time)|true|none|none|
|to|string(date-time)¦null|true|none|none|
|maps|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|

<h2 id="tocS_Match">Match</h2>

<a id="schemamatch"></a>
<a id="schema_Match"></a>
<a id="tocSmatch"></a>
<a id="tocsmatch"></a>

```json
{
  "id": 0,
  "map": {
    "id": 0
  },
  "order": 0,
  "series": {
    "id": 0
  },
  "deleted_at": "2020-06-24T09:20:48Z",
  "game": {
    "id": 0
  },
  "coverage": {
    "full_postgame": "available",
    "light_postgame": "available",
    "light_live": "available"
  },
  "participants": [
    {
      "seed": 1,
      "score": 0,
      "forfeit": true,
      "roster": {
        "id": 0
      },
      "winner": true,
      "stats": {
        "kills": 0,
        "placement": 0
      }
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» map|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» order|integer|true|none|none|
|» series|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» coverage|object|true|none|none|
|»» full_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» light_postgame|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|»» light_live|[Coverage/properties/full_postgame](#schemacoverage/properties/full_postgame)|true|none|none|
|» participants|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Participant/allOf/0](#schemaparticipant/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|

<h2 id="tocS_MatchPatchMap">MatchPatchMap</h2>

<a id="schemamatchpatchmap"></a>
<a id="schema_MatchPatchMap"></a>
<a id="tocSmatchpatchmap"></a>
<a id="tocsmatchpatchmap"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|any|false|none|The value to be used within the operations.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_MatchSummary">MatchSummary</h2>

<a id="schemamatchsummary"></a>
<a id="schema_MatchSummary"></a>
<a id="tocSmatchsummary"></a>
<a id="tocsmatchsummary"></a>

```json
{
  "length": 0,
  "ended": true,
  "patch": "string",
  "dire": {
    "roster": {
      "id": 0
    },
    "score": 0,
    "is_winner": true,
    "structures_standing": {
      "towers": {
        "top_tier_1": true,
        "top_tier_2": true,
        "top_tier_3": true,
        "top_tier_4": true,
        "mid_tier_1": true,
        "mid_tier_2": true,
        "mid_tier_3": true,
        "bot_tier_1": true,
        "bot_tier_2": true,
        "bot_tier_3": true,
        "bot_tier_4": true
      },
      "barracks": {
        "top_ranged": true,
        "top_melee": true,
        "mid_ranged": true,
        "mid_melee": true,
        "bot_ranged": true,
        "bot_melee": true
      }
    },
    "players": [
      {
        "player": {
          "id": 0
        },
        "hero": {
          "items": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "runes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "spells": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "heroes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "small"
              }
            }
          ]
        },
        "kills": 0,
        "assists": 0,
        "deaths": 0,
        "gpm": 0,
        "xpm": 0,
        "networth": 0,
        "side": 2,
        "seed": 0,
        "level": 0,
        "creeps": {
          "faction": {
            "kills": {
              "total": 0
            },
            "denies": {
              "total": 0
            }
          },
          "neutrals": {
            "kills": {
              "total": 0,
              "roshan": 0
            },
            "stacks": {
              "total": 0
            }
          }
        },
        "damage": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "by_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "from_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "healing": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0
              },
              "by_mobs": {
                "total": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0
              },
              "from_mobs": {
                "total": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "multi_kills": [
          {
            "nr_kills": 0,
            "count": 0
          }
        ],
        "kill_streaks": [
          0
        ],
        "runes": {
          "arcane": 0,
          "bounty": 0,
          "double_damage": 0,
          "haste": 0,
          "illusion": 0,
          "invisibility": 0,
          "regeneration": 0
        },
        "items": {
          "hero": {
            "inventory": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "backpack": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "tp_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "neutral_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            }
          },
          "stash": {
            "items": [
              {
                "items": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "runes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "spells": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "heroes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ]
              }
            ],
            "default_size": 0
          },
          "mobs": [
            {
              "type": "string",
              "inventory": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              },
              "backpack": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              }
            }
          ]
        }
      }
    ]
  },
  "radiant": {
    "roster": {
      "id": 0
    },
    "score": 0,
    "is_winner": true,
    "structures_standing": {
      "towers": {
        "top_tier_1": true,
        "top_tier_2": true,
        "top_tier_3": true,
        "top_tier_4": true,
        "mid_tier_1": true,
        "mid_tier_2": true,
        "mid_tier_3": true,
        "bot_tier_1": true,
        "bot_tier_2": true,
        "bot_tier_3": true,
        "bot_tier_4": true
      },
      "barracks": {
        "top_ranged": true,
        "top_melee": true,
        "mid_ranged": true,
        "mid_melee": true,
        "bot_ranged": true,
        "bot_melee": true
      }
    },
    "players": [
      {
        "player": {
          "id": 0
        },
        "hero": {
          "items": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "runes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "spells": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "default"
              }
            }
          ],
          "heroes": [
            {
              "id": 0,
              "name": "string",
              "external_id": 0,
              "external_string_id": "string",
              "images": {
                "id": 0,
                "url": "string",
                "thumbnail": "string",
                "fallback": true,
                "type": "small"
              }
            }
          ]
        },
        "kills": 0,
        "assists": 0,
        "deaths": 0,
        "gpm": 0,
        "xpm": 0,
        "networth": 0,
        "side": 2,
        "seed": 0,
        "level": 0,
        "creeps": {
          "faction": {
            "kills": {
              "total": 0
            },
            "denies": {
              "total": 0
            }
          },
          "neutrals": {
            "kills": {
              "total": 0,
              "roshan": 0
            },
            "stacks": {
              "total": 0
            }
          }
        },
        "damage": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "by_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              },
              "from_mobs": {
                "total": 0,
                "hp_removal": 0,
                "magical": 0,
                "physical": 0,
                "pure": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                },
                "by_mobs": {
                  "total": 0,
                  "hp_removal": 0,
                  "magical": 0,
                  "physical": 0,
                  "pure": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "healing": {
          "hero": {
            "given": {
              "by_hero": {
                "total": 0
              },
              "by_mobs": {
                "total": 0
              }
            },
            "taken": {
              "from_hero": {
                "total": 0
              },
              "from_mobs": {
                "total": 0
              }
            }
          },
          "structures": {
            "towers": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "barracks": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "shrines": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "ancient": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            },
            "other": {
              "given": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              },
              "taken": {
                "by_hero": {
                  "total": 0
                },
                "by_mobs": {
                  "total": 0
                }
              }
            }
          }
        },
        "multi_kills": [
          {
            "nr_kills": 0,
            "count": 0
          }
        ],
        "kill_streaks": [
          0
        ],
        "runes": {
          "arcane": 0,
          "bounty": 0,
          "double_damage": 0,
          "haste": 0,
          "illusion": 0,
          "invisibility": 0,
          "regeneration": 0
        },
        "items": {
          "hero": {
            "inventory": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "backpack": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "tp_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            },
            "neutral_slot": {
              "items": [
                {
                  "items": [
                    {}
                  ],
                  "runes": [
                    {}
                  ],
                  "spells": [
                    {}
                  ],
                  "heroes": [
                    {}
                  ]
                }
              ],
              "default_size": 0
            }
          },
          "stash": {
            "items": [
              {
                "items": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "runes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "spells": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ],
                "heroes": [
                  {
                    "id": 0,
                    "name": "string",
                    "external_id": 0,
                    "external_string_id": "string",
                    "images": {}
                  }
                ]
              }
            ],
            "default_size": 0
          },
          "mobs": [
            {
              "type": "string",
              "inventory": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              },
              "backpack": {
                "items": [
                  {
                    "items": [],
                    "runes": [],
                    "spells": [],
                    "heroes": []
                  }
                ],
                "default_size": 0
              }
            }
          ]
        }
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|length|integer|true|none|none|
|ended|boolean|true|none|none|
|patch|string|true|none|none|
|dire|object|true|none|none|
|» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» score|integer|true|none|none|
|» is_winner|boolean|true|none|none|
|» structures_standing|object|true|none|none|
|»» towers|object|true|none|none|
|»»» top_tier_1|boolean|true|none|none|
|»»» top_tier_2|boolean|true|none|none|
|»»» top_tier_3|boolean|true|none|none|
|»»» top_tier_4|boolean|true|none|none|
|»»» mid_tier_1|boolean|true|none|none|
|»»» mid_tier_2|boolean|true|none|none|
|»»» mid_tier_3|boolean|true|none|none|
|»»» bot_tier_1|boolean|true|none|none|
|»»» bot_tier_2|boolean|true|none|none|
|»»» bot_tier_3|boolean|true|none|none|
|»»» bot_tier_4|boolean|true|none|none|
|»» barracks|object|true|none|none|
|»»» top_ranged|boolean|true|none|none|
|»»» top_melee|boolean|true|none|none|
|»»» mid_ranged|boolean|true|none|none|
|»»» mid_melee|boolean|true|none|none|
|»»» bot_ranged|boolean|true|none|none|
|»»» bot_melee|boolean|true|none|none|
|» players|[object]|true|none|none|
|»» player|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»» hero|[#/paths/~1games~1%7Bid%7D~1assets/get/responses/200/content/application~1json/schema/oneOf/1](#schema#/paths/~1games~1%7bid%7d~1assets/get/responses/200/content/application~1json/schema/oneof/1)|true|none|none|
|»» kills|integer|true|none|none|
|»» assists|integer|true|none|none|
|»» deaths|integer|true|none|none|
|»» gpm|number(float)|true|none|none|
|»» xpm|number(float)|true|none|none|
|»» networth|integer|true|none|none|
|»» side|integer|true|none|none|
|»» seed|integer|true|none|none|
|»» level|integer|true|none|none|
|»» creeps|object|true|none|none|
|»»» faction|object|true|none|none|
|»»»» kills|object|true|none|none|
|»»»»» total|integer|true|none|none|
|»»»» denies|object|true|none|none|
|»»»»» total|integer|true|none|none|
|»»» neutrals|object|true|none|none|
|»»»» kills|object|true|none|none|
|»»»»» total|integer|true|none|none|
|»»»»» roshan|integer|true|none|none|
|»»»» stacks|object|true|none|none|
|»»»»» total|integer|true|none|none|
|»» damage|object|true|none|none|
|»»» hero|object|true|none|none|
|»»»» given|object|true|none|none|
|»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»» taken|object|true|none|none|
|»»»»» from_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» from_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»» structures|object|true|none|none|
|»»»» towers|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» by_hero|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»»» by_mobs|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»» barracks|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»»»» hp_removal|integer|true|none|none|
|»»»»»»» magical|integer|true|none|none|
|»»»»»»» physical|integer|true|none|none|
|»»»»»»» pure|integer|true|none|none|
|»»»» shrines|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»» ancient|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»» other|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/damage/properties/structures/properties/barracks/properties/given/properties/by_mobs)|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» by_hero|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»»» by_mobs|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»» healing|object|true|none|none|
|»»» hero|object|true|none|none|
|»»»» given|object|true|none|none|
|»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» taken|object|true|none|none|
|»»»»» from_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» from_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»» structures|object|true|none|none|
|»»»» towers|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» barracks|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» shrines|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|object|true|none|none|
|»»»»»»» total|integer|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» ancient|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»» other|object|true|none|none|
|»»»»» given|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»» taken|object|true|none|none|
|»»»»»» by_hero|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»»»»»» by_mobs|[MatchSummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs](#schemamatchsummary/properties/dire/properties/players/items/properties/healing/properties/structures/properties/shrines/properties/given/properties/by_mobs)|true|none|none|
|»» multi_kills|[object]|true|none|none|
|»»» nr_kills|integer|true|none|none|
|»»» count|integer|true|none|none|
|»» kill_streaks|[integer]|true|none|none|
|»» runes|object|true|none|none|
|»»» arcane|integer|true|none|none|
|»»» bounty|integer|true|none|none|
|»»» double_damage|integer|true|none|none|
|»»» haste|integer|true|none|none|
|»»» illusion|integer|true|none|none|
|»»» invisibility|integer|true|none|none|
|»»» regeneration|integer|true|none|none|
|»» items|object|true|none|none|
|»»» hero|object|true|none|none|
|»»»» inventory|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» backpack|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» tp_slot|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» neutral_slot|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»» stash|object|true|none|none|
|»»»» items|[[#/paths/~1games~1%7Bid%7D~1assets/get/responses/200/content/application~1json/schema/oneOf/1](#schema#/paths/~1games~1%7bid%7d~1assets/get/responses/200/content/application~1json/schema/oneof/1)]|true|none|none|
|»»»» default_size|integer|true|none|none|
|»»» mobs|[object]|true|none|none|
|»»»» type|string|true|none|none|
|»»»» inventory|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|»»»» backpack|[MatchSummary/properties/dire/properties/players/items/properties/items/properties/stash](#schemamatchsummary/properties/dire/properties/players/items/properties/items/properties/stash)|true|none|none|
|radiant|[MatchSummary/properties/dire](#schemamatchsummary/properties/dire)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|2|
|side|3|

<h2 id="tocS_Participant">Participant</h2>

<a id="schemaparticipant"></a>
<a id="schema_Participant"></a>
<a id="tocSparticipant"></a>
<a id="tocsparticipant"></a>

```json
{
  "seed": 1,
  "score": 0,
  "forfeit": true,
  "roster": {
    "id": 0
  },
  "winner": true,
  "stats": {
    "kills": 0,
    "placement": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» seed|integer|false|none|none|
|» score|integer¦null|false|none|none|
|» forfeit|boolean|false|none|none|
|» roster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» winner|boolean|false|none|none|
|» stats|object¦null|false|none|none|
|»» kills|integer|true|none|none|
|»» placement|integer¦null|true|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|

<h2 id="tocS_Platform">Platform</h2>

<a id="schemaplatform"></a>
<a id="schema_Platform"></a>
<a id="tocSplatform"></a>
<a id="tocsplatform"></a>

```json
{
  "id": 0,
  "name": "string",
  "color": "string",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "default"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|color|string¦null|true|none|none|
|images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

<h2 id="tocS_Player">Player</h2>

<a id="schemaplayer"></a>
<a id="schema_Player"></a>
<a id="tocSplayer"></a>
<a id="tocsplayer"></a>

```json
{
  "id": 0,
  "first_name": "string",
  "last_name": "string",
  "nick_name": "string",
  "active": true,
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "default"
    }
  ],
  "region": {
    "name": "string",
    "abbreviation": "string",
    "country": {
      "id": 0,
      "name": "string",
      "abbreviation": "strin",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  },
  "game": {
    "id": 0
  },
  "race": {
    "id": 0,
    "name": "string",
    "game": {
      "id": 0
    }
  },
  "role": {
    "id": 0
  },
  "teams": [
    {
      "id": 0
    }
  ],
  "social_media_accounts": [
    {
      "handle": "string",
      "url": "string",
      "platform": {
        "id": 0,
        "name": "string",
        "slug": "string"
      }
    }
  ],
  "deleted_at": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» first_name|string¦null|false|none|none|
|» last_name|string¦null|false|none|none|
|» nick_name|string|false|none|none|
|» active|boolean|false|none|none|
|» images|[allOf]|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|false|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» race|[#/paths/~1games~1%7Bid%7D~1races/get/responses/200/content/application~1json/schema/items](#schema#/paths/~1games~1%7bid%7d~1races/get/responses/200/content/application~1json/schema/items)¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» role|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|» teams|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|none|
|» social_media_accounts|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[SocialMediaAccount/allOf/0](#schemasocialmediaaccount/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» platform|[SocialMediaAccount/allOf/1/properties/platform](#schemasocialmediaaccount/allof/1/properties/platform)|true|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» deleted_at|string(date-time)¦null|true|none|none|

<h2 id="tocS_PlayerPatchFirstName">PlayerPatchFirstName</h2>

<a id="schemaplayerpatchfirstname"></a>
<a id="schema_PlayerPatchFirstName"></a>
<a id="tocSplayerpatchfirstname"></a>
<a id="tocsplayerpatchfirstname"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_PlayerPatchLastName">PlayerPatchLastName</h2>

<a id="schemaplayerpatchlastname"></a>
<a id="schema_PlayerPatchLastName"></a>
<a id="tocSplayerpatchlastname"></a>
<a id="tocsplayerpatchlastname"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_PlayerPatchNickName">PlayerPatchNickName</h2>

<a id="schemaplayerpatchnickname"></a>
<a id="schema_PlayerPatchNickName"></a>
<a id="tocSplayerpatchnickname"></a>
<a id="tocsplayerpatchnickname"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_PlayerPatchActive">PlayerPatchActive</h2>

<a id="schemaplayerpatchactive"></a>
<a id="schema_PlayerPatchActive"></a>
<a id="tocSplayerpatchactive"></a>
<a id="tocsplayerpatchactive"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": true
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|boolean|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_PlayerPatchImages">PlayerPatchImages</h2>

<a id="schemaplayerpatchimages"></a>
<a id="schema_PlayerPatchImages"></a>
<a id="tocSplayerpatchimages"></a>
<a id="tocsplayerpatchimages"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": [
    {
      "id": 0
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_PlayerPatchRegion">PlayerPatchRegion</h2>

<a id="schemaplayerpatchregion"></a>
<a id="schema_PlayerPatchRegion"></a>
<a id="tocSplayerpatchregion"></a>
<a id="tocsplayerpatchregion"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0,
    "country": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[CasterPatchRegion/allOf/1/properties/value/allOf/0](#schemacasterpatchregion/allof/1/properties/value/allof/0)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_PlayerPatchRace">PlayerPatchRace</h2>

<a id="schemaplayerpatchrace"></a>
<a id="schema_PlayerPatchRace"></a>
<a id="tocSplayerpatchrace"></a>
<a id="tocsplayerpatchrace"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_PlayerPatchSocialmedia">PlayerPatchSocialmedia</h2>

<a id="schemaplayerpatchsocialmedia"></a>
<a id="schema_PlayerPatchSocialmedia"></a>
<a id="tocSplayerpatchsocialmedia"></a>
<a id="tocsplayerpatchsocialmedia"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "handle": "string",
    "url": "string",
    "platform": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|any|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_Prizepool">Prizepool</h2>

<a id="schemaprizepool"></a>
<a id="schema_Prizepool"></a>
<a id="tocSprizepool"></a>
<a id="tocsprizepool"></a>

```json
{
  "total": "string",
  "first": "string",
  "second": "string",
  "third": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|total|string¦null|true|none|none|
|first|string¦null|true|none|none|
|second|string¦null|true|none|none|
|third|string¦null|true|none|none|

<h2 id="tocS_Race">Race</h2>

<a id="schemarace"></a>
<a id="schema_Race"></a>
<a id="tocSrace"></a>
<a id="tocsrace"></a>

```json
{
  "id": 0,
  "name": "string",
  "game": {
    "id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

<h2 id="tocS_Region">Region</h2>

<a id="schemaregion"></a>
<a id="schema_Region"></a>
<a id="tocSregion"></a>
<a id="tocsregion"></a>

```json
{
  "id": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|

<h2 id="tocS_Role">Role</h2>

<a id="schemarole"></a>
<a id="schema_Role"></a>
<a id="tocSrole"></a>
<a id="tocsrole"></a>

```json
{
  "id": 0,
  "name": "string",
  "game": {
    "id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

<h2 id="tocS_RoleHistory">RoleHistory</h2>

<a id="schemarolehistory"></a>
<a id="schema_RoleHistory"></a>
<a id="tocSrolehistory"></a>
<a id="tocsrolehistory"></a>

```json
{
  "role": {
    "id": 0
  },
  "from": "2020-06-24T09:20:48Z",
  "to": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» role|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» from|string(date-time)|false|none|none|
|» to|string(date-time)¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|

<h2 id="tocS_Roster">Roster</h2>

<a id="schemaroster"></a>
<a id="schema_Roster"></a>
<a id="tocSroster"></a>
<a id="tocsroster"></a>

```json
{
  "id": 0,
  "team": {
    "id": 0
  },
  "line_up": {
    "id": 0,
    "players": [
      {
        "id": 0
      }
    ]
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» team|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|false|none|none|
|» line_up|[#/paths/~1lineups~1%7Bid%7D/get/responses/200/content/application~1json/schema](#schema#/paths/~1lineups~1%7bid%7d/get/responses/200/content/application~1json/schema)¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|

<h2 id="tocS_Series">Series</h2>

<a id="schemaseries"></a>
<a id="schema_Series"></a>
<a id="tocSseries"></a>
<a id="tocsseries"></a>

```json
{
  "id": 0,
  "title": "string",
  "start": "2020-06-24T09:20:48Z",
  "end": "2020-06-24T09:20:48Z",
  "tier": 0,
  "best_of": 0,
  "chain": [
    {
      "id": 0
    }
  ],
  "streamed": true,
  "bracket_position": {
    "part": "UB",
    "col": 0,
    "offset": 0
  },
  "tournament": {
    "id": 0
  },
  "substage": {
    "id": 0
  },
  "game": {
    "id": 0
  },
  "postponed_from": "2020-06-24T09:20:48Z",
  "deleted_at": "2020-06-24T09:20:48Z",
  "coverage": {
    "full_postgame": "available",
    "light_postgame": "available",
    "light_live": "available"
  },
  "participants": [
    {
      "seed": 1,
      "score": 0,
      "forfeit": true,
      "roster": {
        "id": 0
      },
      "winner": true,
      "stats": {
        "kills": 0,
        "placement": 0
      }
    }
  ],
  "matches": [
    {
      "id": 0
    }
  ],
  "casters": [
    {
      "primary": true,
      "caster": {
        "id": 0
      }
    }
  ],
  "has_incident_report": true
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» title|string|false|none|none|
|» start|string(date-time)¦null|false|none|none|
|» end|string(date-time)¦null|false|none|none|
|» tier|integer|false|none|none|
|» best_of|integer|false|none|none|
|» chain|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|Array of series id's|
|» streamed|boolean|false|none|none|
|» bracket_position|object¦null|false|none|none|
|»» part|[BracketPosition/properties/part](#schemabracketposition/properties/part)|true|none|none|
|»» col|integer|true|none|none|
|»» offset|integer|true|none|none|
|» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» substage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» postponed_from|string(date-time)¦null|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|
|» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|» participants|[[Match/allOf/1/properties/participants/items](#schemamatch/allof/1/properties/participants/items)]|true|none|none|
|» matches|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|» casters|[object]|true|none|none|
|»» primary|boolean|true|none|none|
|»» caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» has_incident_report|boolean|true|none|none|

<h2 id="tocS_SeriesPatchTitle">SeriesPatchTitle</h2>

<a id="schemaseriespatchtitle"></a>
<a id="schema_SeriesPatchTitle"></a>
<a id="tocSseriespatchtitle"></a>
<a id="tocsseriespatchtitle"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_SeriesPatchStart">SeriesPatchStart</h2>

<a id="schemaseriespatchstart"></a>
<a id="schema_SeriesPatchStart"></a>
<a id="tocSseriespatchstart"></a>
<a id="tocsseriespatchstart"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string(date-time)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_SeriesPatchEnd">SeriesPatchEnd</h2>

<a id="schemaseriespatchend"></a>
<a id="schema_SeriesPatchEnd"></a>
<a id="tocSseriespatchend"></a>
<a id="tocsseriespatchend"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string(date-time)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_SeriesPatchPostponedFrom">SeriesPatchPostponedFrom</h2>

<a id="schemaseriespatchpostponedfrom"></a>
<a id="schema_SeriesPatchPostponedFrom"></a>
<a id="tocSseriespatchpostponedfrom"></a>
<a id="tocsseriespatchpostponedfrom"></a>

```json
{
  "path": "string",
  "op": "add",
  "value": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string(date-time)|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|add|

<h2 id="tocS_SeriesPatchTier">SeriesPatchTier</h2>

<a id="schemaseriespatchtier"></a>
<a id="schema_SeriesPatchTier"></a>
<a id="tocSseriespatchtier"></a>
<a id="tocsseriespatchtier"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SeriesPatchBestOf">SeriesPatchBestOf</h2>

<a id="schemaseriespatchbestof"></a>
<a id="schema_SeriesPatchBestOf"></a>
<a id="tocSseriespatchbestof"></a>
<a id="tocsseriespatchbestof"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SeriesPatchChain">SeriesPatchChain</h2>

<a id="schemaseriespatchchain"></a>
<a id="schema_SeriesPatchChain"></a>
<a id="tocSseriespatchchain"></a>
<a id="tocsseriespatchchain"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": [
    {
      "id": 0
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SeriesPatchStreamed">SeriesPatchStreamed</h2>

<a id="schemaseriespatchstreamed"></a>
<a id="schema_SeriesPatchStreamed"></a>
<a id="tocSseriespatchstreamed"></a>
<a id="tocsseriespatchstreamed"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": true
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|boolean|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SeriesCaster">SeriesCaster</h2>

<a id="schemaseriescaster"></a>
<a id="schema_SeriesCaster"></a>
<a id="tocSseriescaster"></a>
<a id="tocsseriescaster"></a>

```json
{
  "primary": true,
  "caster": {
    "id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|primary|boolean|true|none|none|
|caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

<h2 id="tocS_SocialMediaAccount">SocialMediaAccount</h2>

<a id="schemasocialmediaaccount"></a>
<a id="schema_SocialMediaAccount"></a>
<a id="tocSsocialmediaaccount"></a>
<a id="tocssocialmediaaccount"></a>

```json
{
  "handle": "string",
  "url": "string",
  "platform": {
    "id": 0,
    "name": "string",
    "slug": "string"
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» handle|string|false|none|none|
|» url|string|true|read-only|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» platform|object|true|none|none|
|»» id|integer|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|

<h2 id="tocS_SocialMediaPlatform">SocialMediaPlatform</h2>

<a id="schemasocialmediaplatform"></a>
<a id="schema_SocialMediaPlatform"></a>
<a id="tocSsocialmediaplatform"></a>
<a id="tocssocialmediaplatform"></a>

```json
{
  "id": 0,
  "name": "string",
  "slug": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|name|string|true|none|none|
|slug|string|true|none|none|

<h2 id="tocS_Stage">Stage</h2>

<a id="schemastage"></a>
<a id="schema_Stage"></a>
<a id="tocSstage"></a>
<a id="tocsstage"></a>

```json
{
  "id": 0,
  "title": "string",
  "tournament": {
    "id": 0
  },
  "order": 0,
  "substages": [
    {
      "id": 0,
      "stage": {
        "id": 0
      },
      "title": "string",
      "tier": 0,
      "type": 0,
      "phase": "qualifier",
      "tournament": {
        "id": 0
      },
      "order": 0,
      "start": "2020-06-24T09:20:48Z",
      "deleted_at": "2020-06-24T09:20:48Z"
    }
  ],
  "deleted_at": "2020-06-24T09:20:48Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» title|string|false|none|none|
|» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» order|integer|true|none|none|
|» substages|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Substage/allOf/0](#schemasubstage/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|»»» order|integer|true|none|none|
|»»» start|string(date-time)¦null|true|none|none|
|»»» deleted_at|string(date-time)¦null|true|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» deleted_at|string(date-time)¦null|true|none|none|

<h2 id="tocS_StagePatchTitle">StagePatchTitle</h2>

<a id="schemastagepatchtitle"></a>
<a id="schema_StagePatchTitle"></a>
<a id="tocSstagepatchtitle"></a>
<a id="tocsstagepatchtitle"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_StagePatchOrder">StagePatchOrder</h2>

<a id="schemastagepatchorder"></a>
<a id="schema_StagePatchOrder"></a>
<a id="tocSstagepatchorder"></a>
<a id="tocsstagepatchorder"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_StandingRoster">StandingRoster</h2>

<a id="schemastandingroster"></a>
<a id="schema_StandingRoster"></a>
<a id="tocSstandingroster"></a>
<a id="tocsstandingroster"></a>

```json
{
  "id": 0,
  "from": "2020-06-24T09:20:49Z",
  "to": "2020-06-24T09:20:49Z",
  "roster": {
    "id": 0
  },
  "deleted_at": "2020-06-24T09:20:49Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» from|string(date-time)|false|none|none|
|» to|string(date-time)¦null|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» roster|object|true|none|none|
|»» id|integer|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|

<h2 id="tocS_Stream">Stream</h2>

<a id="schemastream"></a>
<a id="schema_Stream"></a>
<a id="tocSstream"></a>
<a id="tocsstream"></a>

```json
{
  "id": 0,
  "username": "string",
  "display_name": "string",
  "status_text": "string",
  "viewer_count": 0,
  "online": true,
  "last_online": "2020-06-24T09:20:49Z",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "external"
    }
  ],
  "platform": {
    "id": 0,
    "name": "string",
    "color": "string",
    "images": [
      {
        "id": 0,
        "url": "string",
        "thumbnail": "string",
        "fallback": true,
        "type": "default"
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|none|
|username|string¦null|true|none|none|
|display_name|string|true|none|none|
|status_text|string¦null|true|none|none|
|viewer_count|integer|true|none|none|
|online|boolean|true|none|none|
|last_online|string(date-time)¦null|true|none|none|
|images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» type|string|true|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|platform|[Caster/allOf/1/properties/platform/allOf/0](#schemacaster/allof/1/properties/platform/allof/0)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|external|

<h2 id="tocS_Substage">Substage</h2>

<a id="schemasubstage"></a>
<a id="schema_Substage"></a>
<a id="tocSsubstage"></a>
<a id="tocssubstage"></a>

```json
{
  "id": 0,
  "stage": {
    "id": 0
  },
  "title": "string",
  "tier": 0,
  "type": 0,
  "phase": "qualifier",
  "tournament": {
    "id": 0
  },
  "order": 0,
  "start": "2020-06-24T09:20:49Z",
  "deleted_at": "2020-06-24T09:20:49Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|none|none|
|» stage|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|» title|string|false|none|none|
|» tier|integer|false|none|none|
|» type|integer|false|none|none|
|» phase|string|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» tournament|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|
|» order|integer|true|none|none|
|» start|string(date-time)¦null|true|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|phase|qualifier|
|phase|regular|
|phase|final|
|phase|other|

<h2 id="tocS_SubstagePatchTitle">SubstagePatchTitle</h2>

<a id="schemasubstagepatchtitle"></a>
<a id="schema_SubstagePatchTitle"></a>
<a id="tocSsubstagepatchtitle"></a>
<a id="tocssubstagepatchtitle"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SubstagePatchTier">SubstagePatchTier</h2>

<a id="schemasubstagepatchtier"></a>
<a id="schema_SubstagePatchTier"></a>
<a id="tocSsubstagepatchtier"></a>
<a id="tocssubstagepatchtier"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SubstagePatchType">SubstagePatchType</h2>

<a id="schemasubstagepatchtype"></a>
<a id="schema_SubstagePatchType"></a>
<a id="tocSsubstagepatchtype"></a>
<a id="tocssubstagepatchtype"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|A JSONPatch document as defined by RFC 6902|
|» path|string|true|none|A JSON-Pointer|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_SubstagePatchPhase">SubstagePatchPhase</h2>

<a id="schemasubstagepatchphase"></a>
<a id="schema_SubstagePatchPhase"></a>
<a id="tocSsubstagepatchphase"></a>
<a id="tocssubstagepatchphase"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "qualifier"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|value|qualifier|
|value|regular|
|value|final|
|value|other|

<h2 id="tocS_SubstagePatchOrder">SubstagePatchOrder</h2>

<a id="schemasubstagepatchorder"></a>
<a id="schema_SubstagePatchOrder"></a>
<a id="tocSsubstagepatchorder"></a>
<a id="tocssubstagepatchorder"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_Team">Team</h2>

<a id="schemateam"></a>
<a id="schema_Team"></a>
<a id="tocSteam"></a>
<a id="tocsteam"></a>

```json
{
  "id": 0,
  "name": "string",
  "abbreviation": "string",
  "active": true,
  "region": {
    "name": "string",
    "abbreviation": "string",
    "country": {
      "id": 0,
      "name": "string",
      "abbreviation": "strin",
      "images": [
        {
          "id": 0,
          "url": "string",
          "thumbnail": "string",
          "fallback": true,
          "type": "default"
        }
      ]
    }
  },
  "game": {
    "id": 0
  },
  "deleted_at": "2020-06-24T09:20:49Z",
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "default"
    }
  ],
  "social_media_accounts": [
    {
      "handle": "string",
      "url": "string",
      "platform": {
        "id": 0,
        "name": "string",
        "slug": "string"
      }
    }
  ],
  "standing_roster": {
    "id": 0,
    "from": "2020-06-24T09:20:49Z",
    "to": "2020-06-24T09:20:49Z",
    "roster": {
      "id": 0
    },
    "deleted_at": "2020-06-24T09:20:49Z"
  },
  "organisation": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» id|integer|true|read-only|none|
|» name|string|false|none|none|
|» abbreviation|string|false|none|none|
|» active|boolean|false|none|none|
|» region|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)¦null|false|none|none|
|» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» deleted_at|string(date-time)¦null|true|none|none|
|» images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[Country/properties/images/items/allOf/1](#schemacountry/properties/images/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» social_media_accounts|[[Player/allOf/1/properties/social_media_accounts/items](#schemaplayer/allof/1/properties/social_media_accounts/items)]|true|none|none|
|» standing_roster|any|true|none|none|
|» organisation|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)¦null|true|none|none|

<h2 id="tocS_TeamPatchName">TeamPatchName</h2>

<a id="schemateampatchname"></a>
<a id="schema_TeamPatchName"></a>
<a id="tocSteampatchname"></a>
<a id="tocsteampatchname"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TeamPatchAbbreviation">TeamPatchAbbreviation</h2>

<a id="schemateampatchabbreviation"></a>
<a id="schema_TeamPatchAbbreviation"></a>
<a id="tocSteampatchabbreviation"></a>
<a id="tocsteampatchabbreviation"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TeamPatchActive">TeamPatchActive</h2>

<a id="schemateampatchactive"></a>
<a id="schema_TeamPatchActive"></a>
<a id="tocSteampatchactive"></a>
<a id="tocsteampatchactive"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": true
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|boolean|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TeamPatchImages">TeamPatchImages</h2>

<a id="schemateampatchimages"></a>
<a id="schema_TeamPatchImages"></a>
<a id="tocSteampatchimages"></a>
<a id="tocsteampatchimages"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": [
    {
      "id": 0
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TeamPatchRegion">TeamPatchRegion</h2>

<a id="schemateampatchregion"></a>
<a id="schema_TeamPatchRegion"></a>
<a id="tocSteampatchregion"></a>
<a id="tocsteampatchregion"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0,
    "country": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[CasterPatchRegion/allOf/1/properties/value/allOf/0](#schemacasterpatchregion/allof/1/properties/value/allof/0)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TeamPatchOrganisation">TeamPatchOrganisation</h2>

<a id="schemateampatchorganisation"></a>
<a id="schema_TeamPatchOrganisation"></a>
<a id="tocSteampatchorganisation"></a>
<a id="tocsteampatchorganisation"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TeamPatchSocialmedia">TeamPatchSocialmedia</h2>

<a id="schemateampatchsocialmedia"></a>
<a id="schema_TeamPatchSocialmedia"></a>
<a id="tocSteampatchsocialmedia"></a>
<a id="tocsteampatchsocialmedia"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "handle": "string",
    "url": "string",
    "platform": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[PlayerPatchSocialmedia/allOf/1/properties/value/allOf/0](#schemaplayerpatchsocialmedia/allof/1/properties/value/allof/0)|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_Tournament">Tournament</h2>

<a id="schematournament"></a>
<a id="schema_Tournament"></a>
<a id="tocStournament"></a>
<a id="tocstournament"></a>

```json
{
  "id": 0,
  "title": "string",
  "short_title": "string",
  "tier": 0,
  "copy": {
    "general_description": "string",
    "short_description": "string",
    "format_description": "string"
  },
  "links": {
    "website": "string",
    "wiki": "string"
  },
  "start": "2020-06-24T09:20:49Z",
  "end": "2020-06-24T09:20:49Z",
  "game": {
    "id": 0
  },
  "string_prize_pool": {
    "total": "string",
    "first": "string",
    "second": "string",
    "third": "string"
  },
  "location": {
    "host": {
      "name": "string",
      "abbreviation": "string",
      "country": {
        "id": 0,
        "name": "string",
        "abbreviation": "strin",
        "images": [
          {
            "id": 0,
            "url": "string",
            "thumbnail": "string",
            "fallback": true,
            "type": "default"
          }
        ]
      }
    },
    "participants": [
      {
        "name": "string",
        "abbreviation": "string",
        "country": {
          "id": 0,
          "name": "string",
          "abbreviation": "strin",
          "images": [
            {
              "id": 0,
              "url": "string",
              "thumbnail": "string",
              "fallback": true,
              "type": "default"
            }
          ]
        }
      }
    ]
  },
  "deleted_at": "2020-06-24T09:20:49Z",
  "coverage": {
    "full_postgame": "available",
    "light_postgame": "available",
    "light_live": "available"
  },
  "images": [
    {
      "id": 0,
      "url": "string",
      "thumbnail": "string",
      "fallback": true,
      "type": "small"
    }
  ],
  "stages": [
    {
      "id": 0
    }
  ],
  "casters": [
    {
      "primary": true,
      "default": true,
      "caster": {
        "id": 0
      }
    }
  ],
  "series": [
    {
      "id": 0
    }
  ],
  "rosters": [
    {
      "id": 0
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» id|integer|true|read-only|none|
|»» title|string|false|none|none|
|»» short_title|string|false|none|none|
|»» tier|integer|false|none|none|
|»» copy|object|false|none|none|
|»»» general_description|string|true|none|none|
|»»» short_description|string|true|none|none|
|»»» format_description|string|true|none|none|
|»» links|object|false|none|none|
|»»» website|string¦null|true|none|none|
|»»» wiki|string¦null|true|none|none|
|»» start|string(date-time)¦null|false|none|none|
|»» end|string(date-time)¦null|false|none|none|
|»» game|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|
|»» string_prize_pool|object|false|none|none|
|»»» total|string¦null|true|none|none|
|»»» first|string¦null|true|none|none|
|»»» second|string¦null|true|none|none|
|»»» third|string¦null|true|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|
|»» location|object|true|none|none|
|»»» host|[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)|true|none|none|
|»»» participants|[[Caster/allOf/1/properties/region/allOf/0](#schemacaster/allof/1/properties/region/allof/0)]|true|none|none|
|»» deleted_at|string(date-time)¦null|true|none|none|
|»» coverage|[Match/allOf/1/properties/coverage](#schemamatch/allof/1/properties/coverage)|true|none|none|
|»» images|[allOf]|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[Dota2GameAssets/properties/heroes/items/allOf/1/properties/images/allOf/0](#schemadota2gameassets/properties/heroes/items/allof/1/properties/images/allof/0)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[TournamentPatchImages/allOf/1/properties/value/items/allOf/1](#schematournamentpatchimages/allof/1/properties/value/items/allof/1)|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» stages|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|true|none|none|
|»» casters|[[#/paths/~1tournaments~1%7Bid%7D~1casters/put/requestBody/content/application~1json/schema/items](#schema#/paths/~1tournaments~1%7bid%7d~1casters/put/requestbody/content/application~1json/schema/items)]|true|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» series|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|none|
|» stages|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|none|
|» rosters|[[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)]|false|none|none|

<h2 id="tocS_TournamentPatchTitle">TournamentPatchTitle</h2>

<a id="schematournamentpatchtitle"></a>
<a id="schema_TournamentPatchTitle"></a>
<a id="tocStournamentpatchtitle"></a>
<a id="tocstournamentpatchtitle"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchShortTitle">TournamentPatchShortTitle</h2>

<a id="schematournamentpatchshorttitle"></a>
<a id="schema_TournamentPatchShortTitle"></a>
<a id="tocStournamentpatchshorttitle"></a>
<a id="tocstournamentpatchshorttitle"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchLocation@Host">TournamentPatchLocation@Host</h2>

<a id="schematournamentpatchlocation@host"></a>
<a id="schema_TournamentPatchLocation@Host"></a>
<a id="tocStournamentpatchlocation@host"></a>
<a id="tocstournamentpatchlocation@host"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0,
    "country": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[CasterPatchRegion/allOf/1/properties/value/allOf/0](#schemacasterpatchregion/allof/1/properties/value/allof/0)|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchLocation@Participants">TournamentPatchLocation@Participants</h2>

<a id="schematournamentpatchlocation@participants"></a>
<a id="schema_TournamentPatchLocation@Participants"></a>
<a id="tocStournamentpatchlocation@participants"></a>
<a id="tocstournamentpatchlocation@participants"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": {
    "id": 0,
    "country": {
      "id": 0
    }
  }
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[CasterPatchRegion/allOf/1/properties/value/allOf/0](#schemacasterpatchregion/allof/1/properties/value/allof/0)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchTier">TournamentPatchTier</h2>

<a id="schematournamentpatchtier"></a>
<a id="schema_TournamentPatchTier"></a>
<a id="tocStournamentpatchtier"></a>
<a id="tocstournamentpatchtier"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": 0
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|integer|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchCopy@GeneralDescription">TournamentPatchCopy@GeneralDescription</h2>

<a id="schematournamentpatchcopy@generaldescription"></a>
<a id="schema_TournamentPatchCopy@GeneralDescription"></a>
<a id="tocStournamentpatchcopy@generaldescription"></a>
<a id="tocstournamentpatchcopy@generaldescription"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchCopy@ShortDescription">TournamentPatchCopy@ShortDescription</h2>

<a id="schematournamentpatchcopy@shortdescription"></a>
<a id="schema_TournamentPatchCopy@ShortDescription"></a>
<a id="tocStournamentpatchcopy@shortdescription"></a>
<a id="tocstournamentpatchcopy@shortdescription"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchCopy@FormatDescription">TournamentPatchCopy@FormatDescription</h2>

<a id="schematournamentpatchcopy@formatdescription"></a>
<a id="schema_TournamentPatchCopy@FormatDescription"></a>
<a id="tocStournamentpatchcopy@formatdescription"></a>
<a id="tocstournamentpatchcopy@formatdescription"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|true|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|

<h2 id="tocS_TournamentPatchLinks@Website">TournamentPatchLinks@Website</h2>

<a id="schematournamentpatchlinks@website"></a>
<a id="schema_TournamentPatchLinks@Website"></a>
<a id="tocStournamentpatchlinks@website"></a>
<a id="tocstournamentpatchlinks@website"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchLinks@Wiki">TournamentPatchLinks@Wiki</h2>

<a id="schematournamentpatchlinks@wiki"></a>
<a id="schema_TournamentPatchLinks@Wiki"></a>
<a id="tocStournamentpatchlinks@wiki"></a>
<a id="tocstournamentpatchlinks@wiki"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchStart">TournamentPatchStart</h2>

<a id="schematournamentpatchstart"></a>
<a id="schema_TournamentPatchStart"></a>
<a id="tocStournamentpatchstart"></a>
<a id="tocstournamentpatchstart"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "2020-06-24T09:20:49Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string(date-time)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchEnd">TournamentPatchEnd</h2>

<a id="schematournamentpatchend"></a>
<a id="schema_TournamentPatchEnd"></a>
<a id="tocStournamentpatchend"></a>
<a id="tocstournamentpatchend"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "2020-06-24T09:20:49Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string(date-time)|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchImages">TournamentPatchImages</h2>

<a id="schematournamentpatchimages"></a>
<a id="schema_TournamentPatchImages"></a>
<a id="tocStournamentpatchimages"></a>
<a id="tocstournamentpatchimages"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": [
    {
      "id": 0,
      "type": "small"
    }
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|[allOf]|true|none|The value to be used within the operations.|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|type|small|
|type|large|
|type|square|

<h2 id="tocS_TournamentPatchStringPrizePool@Total">TournamentPatchStringPrizePool@Total</h2>

<a id="schematournamentpatchstringprizepool@total"></a>
<a id="schema_TournamentPatchStringPrizePool@Total"></a>
<a id="tocStournamentpatchstringprizepool@total"></a>
<a id="tocstournamentpatchstringprizepool@total"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchStringPrizePool@First">TournamentPatchStringPrizePool@First</h2>

<a id="schematournamentpatchstringprizepool@first"></a>
<a id="schema_TournamentPatchStringPrizePool@First"></a>
<a id="tocStournamentpatchstringprizepool@first"></a>
<a id="tocstournamentpatchstringprizepool@first"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchStringPrizePool@Second">TournamentPatchStringPrizePool@Second</h2>

<a id="schematournamentpatchstringprizepool@second"></a>
<a id="schema_TournamentPatchStringPrizePool@Second"></a>
<a id="tocStournamentpatchstringprizepool@second"></a>
<a id="tocstournamentpatchstringprizepool@second"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentPatchStringPrizePool@Third">TournamentPatchStringPrizePool@Third</h2>

<a id="schematournamentpatchstringprizepool@third"></a>
<a id="schema_TournamentPatchStringPrizePool@Third"></a>
<a id="tocStournamentpatchstringprizepool@third"></a>
<a id="tocstournamentpatchstringprizepool@third"></a>

```json
{
  "path": "string",
  "op": "replace",
  "value": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[SubstagePatchType/allOf/0](#schemasubstagepatchtype/allof/0)|false|none|A JSONPatch document as defined by RFC 6902|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» op|string|false|none|The operation to be performed|
|» value|string|false|none|The value to be used within the operations.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|replace|
|op|remove|

<h2 id="tocS_TournamentCaster">TournamentCaster</h2>

<a id="schematournamentcaster"></a>
<a id="schema_TournamentCaster"></a>
<a id="tocStournamentcaster"></a>
<a id="tocstournamentcaster"></a>

```json
{
  "primary": true,
  "default": true,
  "caster": {
    "id": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|primary|boolean|true|none|none|
|default|boolean|true|none|none|
|caster|[StandingRoster/allOf/1/properties/roster](#schemastandingroster/allof/1/properties/roster)|true|none|none|

