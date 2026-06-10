---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontologies/get-ontology-full-metadata/"
title: "Get Ontology Full Metadata \u2022 API Reference"
---
# Get Ontology Full Metadata

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the full Ontology metadata. This includes the objects, links, actions, queries, and interfaces.
This endpoint is designed to return as much metadata as possible in a single request to support OSDK workflows.
It may omit certain entities rather than fail the request.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getOntologyFullMetadata

**path:** /api/v2/ontologies/{ontology}/fullMetadata

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to load metadata from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

Success response.

**name:** OntologyFullMetadata

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | objectType | True | Metadata about an Ontology. |
| objectTypes | mapType | False |  |
| actionTypes | mapType | False |  |
| queryTypes | mapType | False |  |
| interfaceTypes | mapType | False |  |
| sharedPropertyTypes | mapType | False |  |
| branch | objectType | False | Metadata about a Foundry branch. |
| valueTypes | mapType | False |  |
