---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/time-series-properties/get-last-point/"
title: "Get Last Point \u2022 API Reference"
---
# Get Last Point

## Endpoint

Get the last point of a time series property.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getLastPoint

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/timeseries/{property}/lastPoint

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| primaryKey | stringType | True | The primary key of the object with the time series property. |
| property | stringType | True | The API name of the time series property. To find the API name for your time series property, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** TimeSeriesPoint

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| time | stringType | True | An ISO 8601 timestamp |
| value | anyType | True | An object which is either an enum String or a double number. |
