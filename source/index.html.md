---
title: Stashy API Reference

language_tabs:
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Stashy API! You can use our API to access Stashy API endpoints, which can provide public and private endpoints for your data.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```python
import stashyio as stashy

api = stashy.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://stashy.io/api/endpoint"
  -H "Authorization: Bearer meowmeowmeow"
```

```javascript
const stashy = require('stashyio');

let api = stashy.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Stashy uses API keys to allow access to the API. You can register a new Stashy API key at your [pfile page](https://stashy.io/profile).

When required, stashy expects the API key to be included in a header that looks like the following:

`Authorization: Bearer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# User documents

## Get All User Documents

```python
import stashyio

api = stashyio.authorize('meowmeowmeow')
api.get('endpoint')
```

```shell
curl "https://stashy.io/api/d/{endpoint}"
  -H "Authorization: meowmeowmeow"
```

```javascript
const stashy = require('stashy');

let api = stashy.authorize('meowmeowmeow');
let kittens = api.get('endpoint')
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all user documents.

### HTTP Request

`GET http://stashy.io/api/d/{endpoint}`

### URL Parameters

URL Parameter | Required | Default | Description
--------- | ------- | ----------- | -----------
endpoint | true | N/A | The private data endpoint.


### Query Parameters

Parameter | Required | Default | Description
--------- | ------- | ----------- | -----------
filter | false | {} | JSON object to filter the results on. {"breed": "calico"}
st:sort | false | {id} | Field to sort the results on.
st:orderby | false | asc | Ascending (asc) or Descending (desc)



<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Document

```python
import stashyio

api = stashyio.authorize('meowmeowmeow')
api.get_by_id('kittens', 2)
```

```shell
curl "http://stashy.io/api/d/{endpoint}/{id}"
  -H "Authorization: Bearer meowmeowmeow"
```

```javascript
const stashy = require('stashy');

let api = stashy.authorize('meowmeowmeow');
let max = api.getById('kittens', 2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific document.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

