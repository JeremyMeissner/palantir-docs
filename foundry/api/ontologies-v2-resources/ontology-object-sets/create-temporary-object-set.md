---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-object-sets/create-temporary-object-set/"
title: "Create Temporary Object Set \u2022 API Reference"
---
# Create Temporary Object Set

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a temporary `ObjectSet` from the given definition. This `ObjectSet` expires after one hour.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v2.createTemporaryObjectSetV2

**path:** /api/v2/ontologies/{ontology}/objectSets/createTemporary

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |
| api:ontologies-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to reference. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The package version of the generated SDK. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

**name:** CreateTemporaryObjectSetRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectSet | unionType | True | Represents the definition of an `ObjectSet` in the `Ontology`. |

**example:** {"objectSet":{"type":"base","objectType":"Employee"}}

### Response

#### Body

Success response.

**name:** CreateTemporaryObjectSetResponseV2

**example:** {"objectSetRid":"ri.object-set.main.object-set.c32ccba5-1a55-4cfe-ad71-160c4c77a053"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectSetRid | stringType | True |  |

**example:** {"objectSetRid":"ri.object-set.main.object-set.c32ccba5-1a55-4cfe-ad71-160c4c77a053"}
