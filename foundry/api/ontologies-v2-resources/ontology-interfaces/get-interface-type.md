---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-interfaces/get-interface-type/"
title: "Get Interface Type \u2022 API Reference"
---
# Get Interface Type

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets a specific interface type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getInterfaceType

**path:** /api/v2/ontologies/{ontology}/interfaceTypes/{interfaceType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| interfaceType | stringType | True | The API name of the interface type. To find the API name, use the **List interface types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
| branch | stringType | False | The Foundry branch to load the interface type definition from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** InterfaceType

**example:** {"apiName":"Athlete","displayName":"Athlete","description":"Good at sportsball","properties":{"name":{"rid":"com.palantir.property.d1abdbfe-0ce2-4fff-b0af-af21002c314b","apiName":"name","displayName":"Name","dataType":"string"}},"extendsInterfaces":["Human"],"rid":"ri.ontology.main.interface.bea1af8c-7d5c-4ec9-b845-8eeed6d77482"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier of an interface, useful for interacting with other Foundry APIs. |
| apiName | stringType | True | The name of the interface type in the API in UpperCamelCase format. To find the API name for your interface type, use the `List interface types` endpoint or check the **Ontology Manager**. |
| displayName | stringType | True | The display name of the entity. |
| description | stringType | False | The description of the interface. |
| properties | mapType | False | A map from a shared property type API name to the corresponding shared property type. The map describes the  set of properties the interface has. A shared property type must be unique across all of the properties. This field only includes properties on the interface that are backed by shared property types. |
| allProperties | mapType | False | A map from a shared property type API name to the corresponding shared property type. The map describes the  set of properties the interface has, including properties from all directly and indirectly extended  interfaces. This field only includes properties on the interface that are backed by shared property types. |
| propertiesV2 | mapType | False | A map from a interface property type API name to the corresponding interface property type. The map describes the set of properties the interface has. An interface property can either be backed by a shared property or it can be defined directly on the interface. |
| allPropertiesV2 | mapType | False | A map from a interface property type API name to the corresponding interface property type. The map describes the set of properties the interface has, including properties from all directly and indirectly extended interfaces. |
| extendsInterfaces | listType | False | A list of interface API names that this interface extends. An interface can extend other interfaces to  inherit their properties. |
| allExtendsInterfaces | listType | False | A list of interface API names that this interface extends, both directly and indirectly. |
| implementedByObjectTypes | listType | False | A list of object API names that implement this interface. |
| links | mapType | False | A map from an interface link type API name to the corresponding interface link type. The map describes the set of link types the interface has. |
| allLinks | mapType | False | A map from an interface link type API name to the corresponding interface link type. The map describes the set of link types the interface has, including links from all directly and indirectly extended interfaces. |

**example:** {"apiName":"Athlete","displayName":"Athlete","description":"Good at sportsball","properties":{"name":{"rid":"com.palantir.property.d1abdbfe-0ce2-4fff-b0af-af21002c314b","apiName":"name","displayName":"Name","dataType":"string"}},"extendsInterfaces":["Human"],"rid":"ri.ontology.main.interface.bea1af8c-7d5c-4ec9-b845-8eeed6d77482"}
