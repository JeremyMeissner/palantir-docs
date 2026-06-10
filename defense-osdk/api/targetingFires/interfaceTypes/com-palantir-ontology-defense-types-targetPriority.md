---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetPriority/"
title: "Target Priority \u2022 API Reference"
---
# Target Priority

Palantir Defense OSDK

[Palantir Defense Ontology] A number indicating the relative level of priority with which to engage a given target type.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Priority | integerType |  | True | The priority level of the target type |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The High Payoff Target List that this target priority belongs to. |
| False | [Palantir Defense Ontology] The targeting area associated with this target priority. |
| True | [Palantir Defense Ontology] The target type associated with this target priority. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The target priorities associated with this target type. |
| False | [Palantir Defense Ontology] The target priorities associated with this targeting area. |
| True | [Palantir Defense Ontology] The set of target priorities for a High Payoff Target List. |

## Code Snippets

### Load ordered Target Priority

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetPriority>>> = await client(com.palantir.ontology.defense-types.targetPriority)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Target Priority

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetPriority>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetPriority).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetPriority>>> = await client(com.palantir.ontology.defense-types.targetPriority)
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

### Load pages of Target Priority

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetPriority>>>
    = await client(com.palantir.ontology.defense-types.targetPriority).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetPriority>>
    = await client(com.palantir.ontology.defense-types.targetPriority).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetPriority.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetPriority).subscribe(         {
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
        { properties: [ "priority", ]}
    );

subscription.unsubscribe();
```

### Load Target Priority metadata

```javascript
import { com.palantir.ontology.defense-types.targetPriority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetPriority);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
