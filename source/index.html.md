---
title: bbox

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript
  - yaml

toc_footers:
  - <a href='#'>Bbox</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

# includes:
#   - errors

search: true

code_clipboard: true

meta:
  - name: bbox parameter
    content: Description of the bbox buidling block
---

# Overview

The bbox query parameter provides a simple mechanism for filtering resources based on their location. It selects all resources that intersect a rectangle (map view) or box (including height information).


# Examples

> Using a bounding box parameter in a request:

```shell
curl \
"https://demo.pygeoapi.io/master/collections/lakes/items?\
bbox=-124.7844079,24.7433195,-66.9513812,49.3457868"
```

```python
import urllib.parse
import urllib.request

params = {'bbox': '-124.7844079,24.7433195,-66.9513812,49.3457868'}

url = 'https://demo.pygeoapi.io/master/collections/lakes/items?' \
    + urllib.parse.urlencode(params)

contents = urllib.request.urlopen(url)

print(contents.read())
```

```javascript
bbox = [-124.7844079,24.7433195,-66.9513812,49.3457868];

url = 'https://demo.pygeoapi.io/master/collections/lakes/items?';

fetch(url + `bbox=${bbox.toString()}`)
.then((response) => response.json())
.then((json) => console.log(json));
```

The following bounding box parameter includes the 48 contiguous states of the United States of America.

`bbox=-124.7844079,24.7433195,-66.9513812,49.3457868`


![Bounding box example](/images/bbox_map.png "© OpenStreetMap contributors, CC-BY-SA; https://www.openstreetmap.org/copyright")


<!-- <aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->

# Description

bbox is a query parameter that may be applied in GET requests on a collection of resources.

The parameter, if provided, selects the resources with a spatial extent that intersects the specified bounding box.

The coordinates of the bounding box are in longitude, latitude and optionally ellipsoidal height unless a different coordinate reference system is specified in the query parameter bbox-crs.

The bbox parameter matches all resources in the collection that are not associated with a spatial geometry, too.

If a resource has multiple spatial geometry properties, it is the decision of the server whether only a single spatial geometry property is used to determine the spatial extent or all relevant geometries.


# OpenAPI 3.0 specification

```yaml
name: bbox
in: query
required: false
style: form
explode: false
schema:
  type: array
  oneOf:
  - minItems: 4
    maxItems: 4
  - minItems: 6
    maxItems: 6
  items:
    type: number
```
schemas/parameter-bbox.yaml

# Source Reference

[OGC API - Features, Part 1, 7.15.3: Parameter bbox](https://docs.ogc.org/is/17-069r3/17-069r3.html#_parameter_bboxm).


<!-- This endpoint retrieves all kittens.

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
 -->
