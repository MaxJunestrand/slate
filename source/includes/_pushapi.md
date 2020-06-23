---
title: " v1.0.0"
language_tabs:
  - javascript--nodejs: Node.JS
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
headingLevel: 3
toc_footers: []
includes: []
search: true
highlight_theme: darkula

---

# AsyncAPI Sample v1.0.0

> Scroll down for code samples, example headers and payloads. Select a language for code samples from the tabs above or the mobile navigation menu.

This is a simple example of an _AsyncAPI_ document.

Base URLs:

* <a href="mqtt://api.company.com:{port}/{app-id}">mqtt://api.company.com:{port}/{app-id}</a>

    * **app-id** - You can find your `app-id` in our control panel, under the auth tab. Default: demo

    * **port** -  Default: 5676

        * 5676
        * 5677

* <a href="amqp://api.company.com:{port}/{app-id}">amqp://api.company.com:{port}/{app-id}</a>

    * **app-id** - You can find your `app-id` in our control panel, under the auth tab. Default: demo

    * **port** -  Default: 5676

        * 5676
        * 5677

Base Topic: **hitch**

<a href="https://api.company.com/terms">Terms of service</a>

# user

## accounts.1.0.action.user.signup

<h3 id="accounts-1-0-action-user-signup-publish">publish</h3>

Note: **Deprecated**

> Example headers

```json

{
  "qos": 1,
  "retainFlag": false
}
```

> Example payload

```json

{
  "user": {
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
}
```

> Code Samples

```javascript--nodejs
const hermes = require('hermesjs');
const app = hermes();

app.from.client.send({
  topic: 'accounts.1.0.action.user.signup',
  payload: {
  "user": {
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
}
});

```

```javascript
//Coming soon...

```

```ruby
# Coming soon...

```

```python
//Coming soon...

```

```java
/* asyncapi-java-tools */
try (JmsServer client = builder.build()) {

  client.accounts.1.0.action.user.signup()
    .publish({
  "user": {
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
})
    .toCompletableFuture()
    .get();
}

```

```go
//Coming soon...

```

*Action to sign a user up.*

Multiline description of what this action does. **It allows Markdown.**

#### Headers

##### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|» qos|[MQTTQoSHeader](#schemamqttqosheader)(int32)|false|Quality of Service|
|» retainFlag|[MQTTRetainHeader](#schemamqttretainheader)|false|This flag determines if the message will be saved by the broker for the specified<br>topic as last known good value. New clients that subscribe to that topic will receive<br>the last retained message on that topic instantly after subscribing. More on retained messages<br>and best practices in one of the next posts.|

#### Payload

##### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|» user|[userCreate](#schemausercreate)|false|No description|
|»» full_name|string|false|User full name|
|»» username|[username](#schemausername)|true|User handle|
|» signup|[signup](#schemasignup)|false|No description|
|»» method|string|true|Signup method|
|»» datetime|[datetime](#schemadatetime)(date-time)|true|Date and Time of the message|

<aside class="success">
This operation does not require authentication
</aside>

# Default

## accounts.1.0.event.user.signup

<h3 id="accounts-1-0-event-user-signup-subscribe">subscribe</h3>

> Example payload

```json

{
  "test": [
    {
      "key1": "string",
      "key2": 0
    }
  ],
  "user": {
    "id": "string",
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
}
```

> Code Samples

```javascript--nodejs
const hermes = require('hermesjs');
const app = hermes();

app.from.client.send({
  topic: 'accounts.1.0.event.user.signup',
  payload: {
  "test": [
    {
      "key1": "string",
      "key2": 0
    }
  ],
  "user": {
    "id": "string",
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
}
});

```

```javascript
//Coming soon...

```

```ruby
# Coming soon...

```

```python
//Coming soon...

```

```java
/* asyncapi-java-tools */
try (JmsServer client = builder.build()) {

  client.accounts.1.0.event.user.signup()
    .publish({
  "test": [
    {
      "key1": "string",
      "key2": 0
    }
  ],
  "user": {
    "id": "string",
    "full_name": "string",
    "username": "string"
  },
  "signup": {
    "method": "email",
    "datetime": "2020-06-03T09:47:56Z"
  }
})
    .toCompletableFuture()
    .get();
}

```

```go
//Coming soon...

```

#### Payload

##### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|» test|[object]|false|No description|
|»» key1|string|false|No description|
|»» key2|integer|false|No description|
|» user|[user](#schemauser)|false|No description|
|»» id|[id](#schemaid)|true|Resource identifier|
|»» full_name|string|false|User full name|
|»» username|[username](#schemausername)|true|User handle|
|» signup|[signup](#schemasignup)|false|No description|
|»» method|string|true|Signup method|
|»» datetime|[datetime](#schemadatetime)(date-time)|true|Date and Time of the message|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## id

<a name="schemaid"></a>

```json
"string"

```

<h3 id="id-properties">Properties</h3>

*id*

|Name|Type|Required|Description|
|---|---|---|---|
|id|[id](#schemaid)|false|Resource identifier|

## username

<a name="schemausername"></a>

```json
"string"

```

<h3 id="username-properties">Properties</h3>

*username*

|Name|Type|Required|Description|
|---|---|---|---|
|username|[username](#schemausername)|false|User handle|

## datetime

<a name="schemadatetime"></a>

```json
"2020-06-03T09:47:56Z"

```

<h3 id="datetime-properties">Properties</h3>

*datetime*

|Name|Type|Required|Description|
|---|---|---|---|
|datetime|[datetime](#schemadatetime)(date-time)|false|Date and Time of the message|

## MQTTQoSHeader

<a name="schemamqttqosheader"></a>

```json
1

```

<h3 id="mqttqosheader-properties">Properties</h3>

*qos*

|Name|Type|Required|Description|
|---|---|---|---|
|qos|[MQTTQoSHeader](#schemamqttqosheader)(int32)|false|Quality of Service|

#### Enumerated Values

|Property|Value|
|---|---|
|qos|0|
|qos|2|

## MQTTRetainHeader

<a name="schemamqttretainheader"></a>

```json
false

```

<h3 id="mqttretainheader-properties">Properties</h3>

*retainFlag*

|Name|Type|Required|Description|
|---|---|---|---|
|retainFlag|[MQTTRetainHeader](#schemamqttretainheader)|false|This flag determines if the message will be saved by the broker for the specified<br>topic as last known good value. New clients that subscribe to that topic will receive<br>the last retained message on that topic instantly after subscribing. More on retained messages<br>and best practices in one of the next posts.|

## user

<a name="schemauser"></a>

```json
{
  "id": "string",
  "full_name": "string",
  "username": "string"
}

```

<h3 id="user-properties">Properties</h3>

|Name|Type|Required|Description|
|---|---|---|---|
|» id|[id](#schemaid)|true|Resource identifier|
|» full_name|string|false|User full name|
|» username|[username](#schemausername)|true|User handle|

## userCreate

<a name="schemausercreate"></a>

```json
{
  "full_name": "string",
  "username": "string"
}

```

<h3 id="usercreate-properties">Properties</h3>

|Name|Type|Required|Description|
|---|---|---|---|
|» full_name|string|false|User full name|
|» username|[username](#schemausername)|true|User handle|

## signup

<a name="schemasignup"></a>

```json
{
  "method": "email",
  "datetime": "2020-06-03T09:47:56Z"
}

```

<h3 id="signup-properties">Properties</h3>

|Name|Type|Required|Description|
|---|---|---|---|
|» method|string|true|Signup method|
|» datetime|[datetime](#schemadatetime)(date-time)|true|Date and Time of the message|

#### Enumerated Values

|Property|Value|
|---|---|
|method|email|
|method|facebook|
|method|twitter|
|method|github|
|method|google|
