---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/connections/get-configuration-connections-batch/"
title: "Get Configuration Connections Batch \u2022 API Reference"
---
# Get Configuration Connections Batch

## Endpoint

Returns a map of Connection RIDs to their corresponding configurations.
Connections are filtered from the response if they don't exist or the requesting token lacks the required permissions.

The maximum batch size for this endpoint is 200.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-connection-read`.

**operationId:** v2.getConfigurationConnectionsBatch

**path:** /api/v2/connectivity/connections/getConfigurationBatch

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-connection-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetConfigurationConnectionsBatchRequestElement | objectType | True |  |

**example:** [{"connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b"}]

### Response

#### Body

**name:** GetConfigurationConnectionsBatchResponse

**example:** {"data":{"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b":{"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b":{"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"}}}
