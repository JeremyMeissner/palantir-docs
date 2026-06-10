---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-unitHierarchy/"
title: "Unit Hierarchy \u2022 API Reference"
---
# Unit Hierarchy

Palantir Defense OSDK

[Palantir Defense Ontology] The structured representation of the relationships between a set of units.

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
| False | [Palantir Defense Ontology] A unit hierarchy contains many unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] The operations associated with this unit hierarchy. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The unit hierarchy associated with this operation. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship belongs to one unit hierarchy. |

## Code Snippets

### Load ordered Unit Hierarchy

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchy>>> = await client(com.palantir.ontology.defense-types.unitHierarchy)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load Unit Hierarchy metadata

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.unitHierarchy);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchy>>> = await client(com.palantir.ontology.defense-types.unitHierarchy)
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

### Load all Unit Hierarchy

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.unitHierarchy>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.unitHierarchy).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load pages of Unit Hierarchy

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchy>>>
    = await client(com.palantir.ontology.defense-types.unitHierarchy).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.unitHierarchy>>
    = await client(com.palantir.ontology.defense-types.unitHierarchy).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.unitHierarchy } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.unitHierarchy.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.unitHierarchy).subscribe(         {
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
