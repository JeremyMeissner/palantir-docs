---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetingOperation/"
title: "Targeting Operation \u2022 API Reference"
---
# Targeting Operation

Palantir Defense OSDK

[Palantir Defense Ontology] A military planning structure characterized as a source for targeting guidance.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Operation

**relativeDocsLink:** missionPlanning/interfaceTypes/com-palantir-ontology-defense-types-operation

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The set of targets leveraging this operation for their targeting guidance. |
| True | [Palantir Defense Ontology] The High Payoff Target List associated with this operation. |
| True | [Palantir Defense Ontology] The Attack Guidance Matrix associated with this operation. |
| True | [Palantir Defense Ontology] The Target Selection Standard Matrix associated with this operation. |
| False | [Palantir Defense Ontology] The set of target engagement authorities for a targeting guidance. |
| True | [Palantir Defense Ontology] The targeting areas associated with this targeting operation. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The targeting operations associated with this targeting area. |
| True | [Palantir Defense Ontology] The targeting operations that use this Attack Guidance Matrix. |
| True | [Palantir Defense Ontology] The targeting operations that use this Target Selection Standard Matrix. |
| True | [Palantir Defense Ontology] The targeting operations that use this High Payoff Target List. |
| False | [Palantir Defense Ontology] The Targeting Operation leveraged by this target. |
| False | [Palantir Defense Ontology] The targeting operations associated with this target engagement authority. |

## Code Snippets

### Load Targeting Operation metadata

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetingOperation);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingOperation>>> = await client(com.palantir.ontology.defense-types.targetingOperation)
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

### Load all Targeting Operation

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetingOperation>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetingOperation).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetingOperation.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetingOperation).subscribe(         {
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

### Load ordered Targeting Operation

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingOperation>>> = await client(com.palantir.ontology.defense-types.targetingOperation)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Targeting Operation

```javascript
import { com.palantir.ontology.defense-types.targetingOperation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingOperation>>>
    = await client(com.palantir.ontology.defense-types.targetingOperation).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetingOperation>>
    = await client(com.palantir.ontology.defense-types.targetingOperation).fetchPage({ $pageSize: 30 });
```
