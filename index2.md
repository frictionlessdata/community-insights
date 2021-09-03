# Frictionless Community at a Glance

Have you ever wondered who uses Frictionless Data? Where are the contributors located? What do they really care about? Well, the core team has been wondering and so we asked our community to let us know via our 2021 Community Survey. Here are some of the things we learned!

## Where in the world can you find the Frictionless community?
{% for row in frictionless.extract('comm_test_responses.csv', layout={"limitRows": 5}) %}
- {{ row.WhereAreYouLocated }}
{% endfor %}

## How long have people been using Frictionless?
```yaml chart
{
  "data": {"url": "comm_test_responses.csv"},
  "mark": "bar",
  "encoding": {
    "x": {"field": "HowLong", "title": "How Long?"},
    "y": {"aggregate": "count", "field": "ID", "title": "Number of Users"},
  },
  "width": 500
}
```
## What programming languages do community members use the most?
```yaml chart
{
  "data": {"url": "comm_test_responses.csv"},
  "mark": "bar",
  "encoding": {
    "x": {"field": "WhatProgMost", "title": "Language?"},
    "y": {"aggregate": "count", "field": "ID", "title": "Number of Users"},
  },
  "width": 500
}
```

## What is one problem you’d like to see Frictionless work on?
{% for row in frictionless.extract('comm_test_responses.csv', layout={"limitRows": 5}) %}
{% if row.WhatOneProb!=None %}
- *"{{ row.WhatOneProb }}"*
{% endif %}
{% endfor %}

## What is the schema for this dataset?
```python script
from pprint import pprint
from frictionless import describe

resource = describe('comm_test_responses.csv')
pprint(resource)
```