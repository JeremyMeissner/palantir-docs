---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/time-series-value-bank-properties/stream-values/"
title: "Stream Values \u2022 API Reference"
---
# Stream Values

## Endpoint

Stream all of the points of a time series property (this includes geotime series references).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.streamValues

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/timeseries/{property}/streamValues

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
| property | stringType | True | The API name of the time series backed property. To find the API name, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Request

#### Body

**name:** StreamTimeSeriesValuesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| range | unionType | False | An absolute or relative range for a time series query. |

**example:** {"range":{"type":"relative","startTime":{"when":"BEFORE","value":5,"unit":"MONTHS"},"endTime":{"when":"BEFORE","value":1,"unit":"MONTHS"}}}

### Response

#### Body

Success response.

**name:** body

##### Format
