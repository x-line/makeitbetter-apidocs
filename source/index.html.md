---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript
  - typescript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - privacy

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Make It Better Studio

> Sample Code!
>
> Choose your preferred language using the tabs above.

Tell us which features you love, or when a feature could be better.

  - Stay up to date on new and upcoming features.
  - See what others are talking about and add your voice to the conversation.
  - Search and see if someone gave similar feedback.
  - Upvote or comment to tell us if you agree or are experiencing the same feedback.
  - Give us new feedback that others can find and discuss.

# Introduction

Welcome to the MakeItBetter(Studio) API! You can use our API to access MIBS API endpoints, which can be used to store, retrieve, and do analysis on user feedback ideas!

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'makeitbetterstudio'

api = MakeItBetterStudio::APIClient.authorize!('your-api-key')
```

```python
import makeitbetterstudio

api = makeitbetterstudio.authorize('your-api-key')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: your-api-key"
```

```javascript
const MIBS = require('MakeItBetterStudio');

let api = MIBS.authorize('your-api-key');
```

```typescript
import { MIBS } from 'MakeItBetterStudio';

let api = MIBS.authorize('your-api-key');
```

> Make sure to replace `your-api-key` with your API key.

You will need an API key to allow access to the API. You can register for a new API key at our [developer portal](http://makeitbetter.studio/developers).

The API key must be included in all API requests to the server in a header that looks like the following:

`Authorization: your-api-key`

<aside class="notice">
You must replace <code>your-api-key</code> with your personal API key.
</aside>

# Ideas

## Get All Ideas

```ruby
require 'makeitbetterstudio'

api = MakeItBetterStudio::APIClient.authorize!('your-api-key')
api.ideas.get
```

```python
import makeitbetterstudio

api = makeitbetterstudio.authorize('your-api-key')
api.ideas.get()
```

```shell
curl "http://api.makeitbetter.studio/ideas" \
  -H "Authorization: your-api-key"
```

```javascript
const MIBS = require('MakeItBetterStudio');

let api = makeitbetterstudio.authorize('your-api-key');
let ideas = api.ideas.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "title": "Example Title Text",
    "utcCreated": "2022-01-01",
    "upvotes": 10,
    "comments": 20,
    "officialResponse": "Example Response",
    "utcOfficialResponse": "2022-01-02",
  },
  ...
]
```

This endpoint retrieves all ideas.

### HTTP Request

`GET http://api.makeitbetter.studio/ideas`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
start | 0 | Paging: If included, will skip that many records.
page_size  | 1000 | Paging: If included, use the specified value for page size.
search | empty | If included, can be used to search ideas by text.
status | empty | If included, will search ideas by status.
status_op | "or" | If multiple statuses are specified in the 'status' search, then using "or" will return ideas matching any of the statuses, while "and" will return ideas matching all of the statuses.
category | empty | If included, will search ideas by category.
category_op | "or" | If multiple categories are specified in the 'category' search, then using "or" will return ideas matching any of the categories, while "and" will return ideas matching all of the categories.

<aside class="success">
Remember — use paging to keep queries fast!
</aside>

## Get a Specific Idea

```ruby
require 'makeitbetterstudio'

api = MakeItBetterStudio::APIClient.authorize!('your-api-key')
api.ideas.get("c1dff617-7db1-4ca6-9bbb-65f40f7893ad")
```

```python
import makeitbetterstudio

api = makeitbetterstudio.authorize('your-api-key')
api.ideas.get("c1dff617-7db1-4ca6-9bbb-65f40f7893ad")
```

```shell
curl "http://api.makeitbetter.studio/ideas/2" \
  -H "Authorization: your-api-key"
```

```javascript
const makeitbetterstudio = require('MakeItBetterStudio');

let api = makeitbetterstudio.authorize('your-api-key');
let idea = api.ideas.get("c1dff617-7db1-4ca6-9bbb-65f40f7893ad");
```

> The above command returns JSON structured like this:

```json
  {
    "id": "c1dff617-7db1-4ca6-9bbb-65f40f7893ad",
    "title": "Example Title Text",
    "utcCreated": "2022-01-01",
    "upvotes": 10,
    "officialResponse": "Example Response",
    "utcOfficialResponse": "2022-01-02",
    "status": [
      { "id": "7471f94e-648d-4f02-9de9-f010a8697192", "name": "Open" }
    ]
    "comments": [],
  },
```

This endpoint retrieves a specific idea.

### HTTP Request

`GET http://api.makeitbetter.studio/ideas/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the idea to retrieve

## Delete a Specific Idea

```ruby
require 'makeitbetterstudio'

api = MakeItBetterStudio::APIClient.authorize!('your-api-key')
api.ideas.delete(2)
```

```python
import makeitbetterstudio

api = makeitbetterstudio.authorize('your-api-key')
api.ideas.delete(2)
```

```shell
curl "http://api.makeitbetter.studio/ideas/2" \
  -X DELETE \
  -H "Authorization: your-api-key"
```

```javascript
const MIBS = require('MakeItBetterStudio');

let api = makeitbetterstudio.authorize('your-api-key');
let idea = api.ideas.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific idea.

### HTTP Request

`DELETE http://api.makeitbetter.studio/ideas/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the idea to delete
