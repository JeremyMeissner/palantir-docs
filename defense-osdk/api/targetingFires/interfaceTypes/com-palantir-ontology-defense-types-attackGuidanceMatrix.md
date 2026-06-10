---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-attackGuidanceMatrix/"
title: "Attack Guidance Matrix \u2022 API Reference"
---
# Attack Guidance Matrix

Palantir Defense OSDK

[Palantir Defense Ontology] A grouping of attack guidances for an operation.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The set of target attack guidelines for an Attack Guidance Matrix. |
| True | [Palantir Defense Ontology] The targeting operations that use this Attack Guidance Matrix. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The Attack Guidance Matrix that this attack guidance belongs to. |
| True | [Palantir Defense Ontology] The Attack Guidance Matrix associated with this operation. |

## Code Snippets

### Load pages of Attack Guidance Matrix

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidanceMatrix>>>
    = await client(com.palantir.ontology.defense-types.attackGuidanceMatrix).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidanceMatrix>>
    = await client(com.palantir.ontology.defense-types.attackGuidanceMatrix).fetchPage({ $pageSize: 30 });
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidanceMatrix>>> = await client(com.palantir.ontology.defense-types.attackGuidanceMatrix)
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

### Load ordered Attack Guidance Matrix

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidanceMatrix>>> = await client(com.palantir.ontology.defense-types.attackGuidanceMatrix)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.attackGuidanceMatrix.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.attackGuidanceMatrix).subscribe(         {
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

### Load all Attack Guidance Matrix

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.attackGuidanceMatrix>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.attackGuidanceMatrix).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Attack Guidance Matrix metadata

```javascript
import { com.palantir.ontology.defense-types.attackGuidanceMatrix } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.attackGuidanceMatrix);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
