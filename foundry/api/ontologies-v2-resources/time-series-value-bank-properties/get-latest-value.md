---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/time-series-value-bank-properties/get-latest-value/"
title: "Get Latest Value \u2022 API Reference"
---
# Get Latest Value

## Endpoint

Get the latest value of a property backed by a timeseries. If a specific geotime series integration has both a history and a live integration, we will give precedence to the live integration.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getLatestValue

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/timeseries/{propertyName}/latestValue

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
| primaryKey | stringType | True | The primary key of the object with the timeseries property. |
| propertyName | stringType | True | The API name of the timeseries property. To find the API name for your property value bank property, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** TimeseriesEntry

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| time | stringType | True | An ISO 8601 timestamp |
| value | anyType | True | An object which is either an enum String, double number, or a geopoint. |
