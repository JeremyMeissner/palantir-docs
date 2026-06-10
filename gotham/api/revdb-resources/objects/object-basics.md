---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/object-basics/"
title: "Object basics \u2022 API Reference"
---
An Object is a data container for a specific instance of an Object Type. For instance, the `com.palantir.object.employee` object type may contain data about several employees, and each one is represented as a single Object.

## Searching objects

The [search objects endpoint](/docs/gotham/api/revdb-resources/objects/search-objects/) allows searching by properties and other attributes of objects of a given type. The search query is provided as a JSON request body.

## Search Query types

| Query type                        | Description                                                           |
|-----------------------------------|-----------------------------------------------------------------------|
| [empty](#empty)                   | Apply no filter (i.e., list all objects of type objectType).          |
| [eq](#eq)                         | The provided property is exactly equal to the provided value.         |
| [and](#and)                       | All the sub-queries match.                                            |
| [or](#or)                         | At least one of the sub-queries matches.                              |
| [keyword](#keyword)               | The objects' contents match the specified keyword query.              |
| [lt](#lt)                         | The provided property is less than the provided value.                |
| [gt](#gt)                         | The provided property is greater than the provided value.             |
| [lte](#lte)                       | The provided property is less than or equal to the provided value.    |
| [gte](#gte)                       | The provided property is greater than or equal to the provided value. |
| [not](#not)                       | The sub-query does not match.                                         |
| [geoPointWithin](#geoPointWithin) | Filter objects whose intrinsic coordinates are within the provided polygon |

## Example queries

### <a name="eq"></a> Equality query (`eq`)

**Description**

The provided property is exactly equal to the provided value.

**Example**

```json
{
  "query": {
    "type": "eq",
    "field": "com.palantir.property.name:FIRST_NAME",
    "value": "John"
  }
}
```

**Case-sensitive:** yes

-------

### <a name="and"></a> And query (`and`)

**Description**

All the sub-queries match.

**Example**

```json
{
  "query": {
    "type": "and",
    "value": [
      {
        "type": "eq",
        "field": "com.palantir.property.name:FIRST_NAME",
        "value": "John"
      },
      {
        "type": "eq",
        "field": "com.palantir.property.name:LAST_NAME",
        "value": "Smith"
      }
    ]
  }
}
```

-------

### <a name="or"></a> Or query (`or`)

**Description**

At least one of the sub-queries matches.

**Example**

```json
{
  "query": {
    "type": "or",
    "value": [
      {
        "type": "eq",
        "field": "com.palantir.property.name:FIRST_NAME",
        "value": "John"
      },
      {
        "type": "eq",
        "field": "com.palantir.property.name:FIRST_NAME",
        "value": "Jane"
      }
    ]
  }
}
```

-------

### <a name="keyword"></a> Keyword query (`keyword`)

**Description**

The objects' contents match the specified keyword query. Keyword queries support flexible, advanced syntax.

**Example**

```json
{
  "query": {
    "type": "keyword",
    "query": "quick brown fox"
  }
}
```

-------

### <a name="empty"></a> Empty query (`empty`)

**Description**

A query that matches all objects for the specified object type.

**Example**

```json
{
  "query": {
    "type": "empty"
  }
}
```

### <a name="lt"></a> Less than query (`lt`)

**Description**

The provided property is less than the provided value.

**Example**

```json
{
  "query": {
    "type": "lt",
    "field": "com.palantir.property.age",
    "value": 10
  }
}
```

-------

### <a name="gt"></a> Greater than query (`gt`)

**Description**

The provided property is greater than the provided value.

**Example**

```json
{
  "query": {
    "type": "gt",
    "field": "com.palantir.property.age",
    "value": 10
  }
}
```

-------

### <a name="lte"></a> Less than or equal query (`lte`)

**Description**

The provided property is less than or equal to the provided value.

**Example**

```json
{
  "query": {
    "type": "lte",
    "field": "com.palantir.property.age",
    "value": 10
  }
}
```

-------

### <a name="gte"></a> Greater than or equal query (`gte`)

**Description**

The provided property is greater than or equal to the provided value.

**Example**

```json
{
  "query": {
    "type": "gte",
    "field": "com.palantir.property.age",
    "value": 10
  }
}
```

-------

### <a name="not"></a> Not query (`not`)

**Description**

The sub-query does not match.

**Example**

```json
{
  "query": {
    "type": "not",
    "value": {
      "type": "eq",
      "field": "com.palantir.property.name:FIRST_NAME",
      "value": "John"
    }
  }
}
```

-------

### <a name="geoPointWithin"></a> GeoPoint Within Polygon query (`geoPointWithin`)

**Description**

The objects' intrinsic coordinates are within the provided polygon.

**Example**

```json
{
  "query": {
    "type": "geoPointWithin",
    "polygon": [
      {"longitude":-77.05974824713265,"latitude":38.903335277742656},
      {"longitude":-77.06130631105295,"latitude":38.90278989613124},
      {"longitude":-77.0628268311872,"latitude":38.905175909773085},
      {"longitude":-77.06011742685993,"latitude":38.905195387105344},
      {"longitude":-77.05974824713265,"latitude":38.903335277742656}
    ]
  }
}
```
