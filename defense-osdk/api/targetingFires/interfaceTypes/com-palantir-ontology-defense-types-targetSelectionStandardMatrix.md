---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetSelectionStandardMatrix/"
title: "Target Selection Standard Matrix \u2022 API Reference"
---
# Target Selection Standard Matrix

Palantir Defense OSDK

[Palantir Defense Ontology] A grouping of target selection standards for an operation.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The set of target selection standards for a Target Selection Standard Matrix. |
| True | [Palantir Defense Ontology] The targeting operations that use this Target Selection Standard Matrix. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The Target Selection Standard Matrix associated with this operation. |
| True | [Palantir Defense Ontology] The Target Selection Standard Matrix that this standard belongs to. |

## Code Snippets

### Load pages of Target Selection Standard Matrix

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandardMatrix>>>
    = await client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandardMatrix>>
    = await client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix).fetchPage({ $pageSize: 30 });
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandardMatrix>>> = await client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix)
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

### Load Target Selection Standard Matrix metadata

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetSelectionStandardMatrix);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetSelectionStandardMatrix.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix).subscribe(         {
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
        { properties: [ ]}
    );

subscription.unsubscribe();
```

### Load ordered Target Selection Standard Matrix

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandardMatrix>>> = await client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Target Selection Standard Matrix

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandardMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetSelectionStandardMatrix>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetSelectionStandardMatrix).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
