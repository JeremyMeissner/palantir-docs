---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-highPayoffTargetList/"
title: "High Payoff Target List \u2022 API Reference"
---
# High Payoff Target List

Palantir Defense OSDK

[Palantir Defense Ontology] A grouping of target priorities for an operation.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The set of target priorities for a High Payoff Target List. |
| True | [Palantir Defense Ontology] The targeting operations that use this High Payoff Target List. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The High Payoff Target List that this target priority belongs to. |
| True | [Palantir Defense Ontology] The High Payoff Target List associated with this operation. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.highPayoffTargetList>>> = await client(com.palantir.ontology.defense-types.highPayoffTargetList)
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

### Load ordered High Payoff Target List

```javascript
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.highPayoffTargetList>>> = await client(com.palantir.ontology.defense-types.highPayoffTargetList)
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
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.highPayoffTargetList.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.highPayoffTargetList).subscribe(         {
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

### Load all High Payoff Target List

```javascript
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.highPayoffTargetList>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.highPayoffTargetList).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load High Payoff Target List metadata

```javascript
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.highPayoffTargetList);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of High Payoff Target List

```javascript
import { com.palantir.ontology.defense-types.highPayoffTargetList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.highPayoffTargetList>>>
    = await client(com.palantir.ontology.defense-types.highPayoffTargetList).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.highPayoffTargetList>>
    = await client(com.palantir.ontology.defense-types.highPayoffTargetList).fetchPage({ $pageSize: 30 });
```
