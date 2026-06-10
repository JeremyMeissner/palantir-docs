---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-unitHierarchyNodeRelationship/"
title: "Unit Hierarchy Node Relationship \u2022 API Reference"
---
# Unit Hierarchy Node Relationship

Palantir Defense OSDK

[Palantir Defense Ontology] Serves as an intermediary relationship object type to traverse different hierarchies for the same unit. This flexibility is required as there is not a single hierarchy within the DoD. For example, the Army has one hierarchy when at rest, but when deployed that hierarchy can be modified. Units won't necessarily be deployed together or have the same parent/child units when deployed.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Valid From | dateType |  | False | [Palantir Defense Ontology] Used to capture the start date of when a unit relationship or unit hierarchy is valid. |
| Valid To | dateType |  | False | [Palantir Defense Ontology] Used to capture the end date of when a unit relationship or unit hierarchy is valid. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit hierarchy relationship can link to one unit hierarchy relationship type. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship links to one child unit. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship links to one parent unit. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship belongs to one unit hierarchy. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit hierarchy contains many unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] A unit can link to many parent units via unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] A unit can link to many child units via unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] A unit hierarchy relationship type can link to many unit hierarchy relationships. |

## Code Snippets

### Load Unit Hierarchy Node Relationship metadata

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationship>>> = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship)
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

### Load pages of Unit Hierarchy Node Relationship

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationship>>>
    = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationship>>
    = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.unitHierarchyNodeRelationship.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship).subscribe(         {
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
        { properties: [ "validFrom", "validTo", ]}
    );

subscription.unsubscribe();
```

### Load ordered Unit Hierarchy Node Relationship

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationship>>> = await client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Unit Hierarchy Node Relationship

```javascript
import { com.palantir.ontology.defense-types.unitHierarchyNodeRelationship } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.unitHierarchyNodeRelationship>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.unitHierarchyNodeRelationship).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
