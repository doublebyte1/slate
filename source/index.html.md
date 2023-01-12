---
title: bbox

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Bbox</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: bbox parameter
    content: Description of the bbox buidling block
---

# Overview

The bbox query parameter provides a simple mechanism for filtering resources based on their location. It selects all resources that intersect a rectangle (map view) or box (including height information).


# Examples

> Using a bounding box:

```shell
curl \
"https://demo.pygeoapi.io/master/collections/lakes/items?\
bbox=-124.7844079,24.7433195,-66.9513812,49.3457868"
```

```python
class Bbox:
  def __init__(self,x1,y1,x2,y2):
    self.x1 = x1
    self.y1 = y1
    self.x2 = x2
    self.y2 = y2
    self.min = [x1,y1]
    self.max = [x2,y2]

  def getMin(self):
    return self.min
  def getMax(self):
    return self.max
  def getLowerLon(self):
    return self.x1
  def getLowerLat(self):
    return self.y1
  def getUpperLon(self):
    return self.x2
  def getUpperLat(self):
    return self.y2
  def getBounds(self):
    return [self.x1,self.y1,self.x2,self.y2]

bbox = Bbox(-124.7844079,24.7433195,-66.9513812,49.3457868)

bbox.getLowerLat()
```

```javascript
console.log("Hello World!")
```

The following bounding box parameter includes the 48 contiguous states of the United States of America.

`bbox=-124.7844079,24.7433195,-66.9513812,49.3457868`


![Bounding box example](/images/bbox_map.png "© OpenStreetMap contributors, CC-BY-SA; https://www.openstreetmap.org/copyright")


<!-- <aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->

# Description


# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python


```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

