---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/time-series-properties/stream-points/"
title: "Stream Points \u2022 API Reference"
---
# Stream Points

## Endpoint

Stream all of the points of a time series property.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.streamPoints

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/timeseries/{property}/streamPoints

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
| format | enumType | False | The output format to serialize the output binary stream in. Default is JSON. ARROW is more efficient than JSON at streaming a large sized response. |

### Request

#### Body

**name:** StreamTimeSeriesPointsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| range | unionType | False | An absolute or relative range for a time series query. |
| aggregate | objectType | False |  |

**example:** {"range":{"type":"relative","startTime":{"when":"BEFORE","value":5,"unit":"MONTHS"},"endTime":{"when":"BEFORE","value":1,"unit":"MONTHS"}}}

### Response

#### Body

Success response.

**name:** body

##### Format
