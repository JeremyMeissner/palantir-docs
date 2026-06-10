---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/linked-objects/get-linked-object/"
title: "Get Linked Object \u2022 API Reference"
---
# Get Linked Object

## Endpoint

Get a specific linked object that originates from another object.

If there is no link between the two objects, `LinkedObjectNotFound` is thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getLinkedObjectV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/links/{linkType}/{linkedObjectPrimaryKey}

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
| primaryKey | stringType | True | The primary key of the object from which the links originate. To look up the expected primary key for your object type, use the `Get object type` endpoint or the **Ontology Manager**. |
| linkType | stringType | True | The API name of the link that exists between the object and the requested objects. To find the API name for your link type, check the **Ontology Manager**. |
| linkedObjectPrimaryKey | stringType | True | The primary key of the requested linked object. To look up the expected primary key for your object type, use the `Get object type` endpoint (passing the linked object type) or the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| select | listType | False | The properties of the object type that should be included in the response. Omit this parameter to get all the properties. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| excludeRid | booleanType | False | A flag to exclude the retrieval of the `__rid` property.  Setting this to true may improve performance of this endpoint for object types in OSV2. |
| branch | stringType | False | The Foundry branch to load the object set for multiple object types. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** OntologyObjectV2

**example:** {"__rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","__primaryKey":50030,"__apiName":"Employee","id":50030,"firstName":"John","lastName":"Doe"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| PropertyApiName | stringType | True | The name of the property in the API. To find the API name for your property, use the `Get object type` endpoint or check the **Ontology Manager**. |
| PropertyValue | anyType | True | Represents the value of a property in the following format.  \| Type                                                                                                                      \| JSON encoding                                               \| Example                                                                                            \| \|---------------------------------------------------------------------------------------------------------------------------\|-------------------------------------------------------------\|----------------------------------------------------------------------------------------------------\| \| Array                                                                                                                     \| array                                                       \| `["alpha", "bravo", "charlie"]`                                                                    \| \| [Attachment](/docs/foundry/api/v2/ontologies-v2-resources/attachment-properties/attachment-property-basics/)              \| JSON encoded `AttachmentProperty` object                    \| `{"rid":"ri.blobster.main.attachment.2f944bae-5851-4204-8615-920c969a9f2e"}`                       \| \| Boolean                                                                                                                   \| boolean                                                     \| `true`                                                                                             \| \| Byte                                                                                                                      \| number                                                      \| `31`                                                                                               \| \| CipherText                                                                                                                \| string                                                      \| `"CIPHER::ri.bellaso.main.cipher-channel.e414ab9e-b606-499a-a0e1-844fa296ba7e::unzjs3VifsTxuIpf1fH1CJ7OaPBr2bzMMdozPaZJtCii8vVG60yXIEmzoOJaEl9mfFFe::CIPHER"`                                                                                                                                                                                        \|         \| Date                                                                                                                      \| ISO 8601 extended local date string                         \| `"2021-05-01"`                                                                                     \| \| Decimal                                                                                                                   \| string                                                      \| `"2.718281828"`                                                                                    \| \| Double                                                                                                                    \| number                                                      \| `3.14159265`                                                                                       \| \| Float                                                                                                                     \| number                                                      \| `3.14159265`                                                                                       \| \| GeoPoint                                                                                                                  \| geojson                                                     \| `{"type":"Point","coordinates":[102.0,0.5]}`                                                       \| \| GeoShape                                                                                                                  \| geojson                                                     \| `{"type":"LineString","coordinates":[[102.0,0.0],[103.0,1.0],[104.0,0.0],[105.0,1.0]]}`            \| \| Integer                                                                                                                   \| number                                                      \| `238940`                                                                                           \| \| Long                                                                                                                      \| string                                                      \| `"58319870951433"`                                                                                 \| \| [MediaReference](/docs/foundry/api/v2/ontologies-v2-resources/media-reference-properties/media-reference-property-basics/)\| JSON encoded `MediaReference` object                        \| `{"mimeType":"application/pdf","reference":{"type":"mediaSetViewItem","mediaSetViewItem":{"mediaSetRid":"ri.mio.main.media-set.4153d42f-ca4b-4e42-8ca5-8e6aa7edb642","mediaSetViewRid":"ri.mio.main.view.82a798ad-d637-4595-acc6-987bcf16629b","mediaItemRid":"ri.mio.main.media-item.001ec98b-1620-4814-9e17-8e9c4e536225"}}}`                       \| \| Secured Property Value                                                                                                    \| JSON encoded `SecuredPropertyValue` object                  \| `{"value": 10, "propertySecurityIndex" : 5}`                                                       \| \| Short                                                                                                                     \| number                                                      \| `8739`                                                                                             \| \| String                                                                                                                    \| string                                                      \| `"Call me Ishmael"`                                                                                \| \| Struct                                                                                                                    \| JSON object of struct field API name -> value               \| {"firstName": "Alex", "lastName": "Karp"}                                                          \| \| Timestamp                                                                                                                 \| ISO 8601 extended offset date-time string in UTC zone       \| `"2021-01-04T05:00:00Z"`                                                                           \| \| [Timeseries](/docs/foundry/api/v2/ontologies-v2-resources/time-series-properties/time-series-property-basics/)            \| JSON encoded `TimeseriesProperty` object or seriesId string \| `{"seriesId": "wellPressureSeriesId", "syncRid": ri.time-series-catalog.main.sync.04f5ac1f-91bf-44f9-a51f-4f34e06e42df"}` or `{"templateRid": "ri.codex-emu.main.template.367cac64-e53b-4653-b111-f61856a63df9", "templateVersion": "0.0.0"}` or `"wellPressureSeriesId"`\|                                                                           \| \| Vector                                                                                                                    \| array                                                       \| `[0.1, 0.3, 0.02, 0.05 , 0.8, 0.4]`                                                                \|  Note that for backwards compatibility, the Boolean, Byte, Double, Float, Integer, and Short types can also be encoded as JSON strings. |

**example:** {"__rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","__primaryKey":50030,"__apiName":"Employee","id":50030,"firstName":"John","lastName":"Doe"}
