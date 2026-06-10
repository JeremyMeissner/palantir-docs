---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-unitHierarchyNodeRelationshipType/"
title: "Unit Hierarchy Node Relationship Type \u2022 API Reference"
---
# Unit Hierarchy Node Relationship Type

Palantir Defense OSDK

[Palantir Defense Ontology] Describes the types of relationships that can exist between units within a hierarchy, such as Organic, Assigned, Attached, OPCON (Operational Control), or TACON (Tactical Control).

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Relationship Type | stringType |  | True | [Palantir Defense Ontology] Captures the unit relationship type (e.g., Organic, Assigned, OPCON) |
| Definition | stringType |  | True | [Palantir Defense Ontology] Captures doctrinal definition information for a unit relationship type |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit hierarchy relationship type can link to many unit hierarchy relationships. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit hierarchy relationship can link to one unit hierarchy relationship type. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType>>> = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType)
    .where({
        $and:[
            { $not: { someProperty: { $isNull: true }}},
            { someProperty: { $eq: "foo" }}
        ]
    })
    .fetchPageWithErrors({
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load Unit Hierarchy Node Relationship Type metadata

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Unit Hierarchy Node Relationship Type

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType>>>
    = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType>>
    = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType).subscribe(         {
            onChange(update) {
                if (update.state === "ADDED_OR_UPDATED") {
                    // An object has received an update or an object was added to the object set
                    const currentObject = objects[update.object.$primaryKey];
                    if (currentObject !== undefined) {
                        currentObject["<propertyName>"] = update.object["<propertyName>"] ?? currentObject["<propertyName>"];
                    }
                }
                else if (update.state === "REMOVED") {
                    // The object was removed from the object set, which could mean it was deleted or no longer meets the filter criteria
                    delete objects[update.object.$primaryKey];
                }
            },
            onSuccessfulSubscription() {
                // The subscription was successful and you can expect to receive updates
            },
            onError(err) {
                // There was an error with the subscription and you will not receive any more updates
                console.error(err);
            },
            onOutOfDate() {
                // We could not keep track of all changes. Please reload the objects in your set.
            },
        },
        { properties: [ "relationshipType", "definition", ]}
    );

subscription.unsubscribe();
```

### Load ordered Unit Hierarchy Node Relationship Type

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType>>> = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Unit Hierarchy Node Relationship Type

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationshipType).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
