---
source_url: "https://www.palantir.com/docs/defense-osdk/api/missionPlanning/interfaceTypes/"
title: "Operation \u2022 API Reference"
---
# Operation

Palantir Defense OSDK

[Palantir Defense Ontology] A military planning structure.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Start Time | timestampType |  | True | The start time of the operation |
| End Time | timestampType |  | True | The end time of the operation |

## Ontology Entity Type Content

### Interface Type

#### Extended By Interfaces

**displayName:** Targeting Operation

**relativeDocsLink:** targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetingOperation

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The parent operation of an operation. |
| False | [Palantir Defense Ontology] The child operations of an operation. |
| False | [Palantir Defense Ontology] The unit owning this operation. |
| False | [Palantir Defense Ontology] The unit hierarchy associated with this operation. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The parent operation of an operation. |
| False | [Palantir Defense Ontology] The child operations of an operation. |
| False | [Palantir Defense Ontology] The operations associated with this unit hierarchy. |
| False | [Palantir Defense Ontology] The operations owned by this unit. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.operation>>> = await client(com.palantir.ontology.defense-types.operation)
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

### Load pages of Operation

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.operation>>>
    = await client(com.palantir.ontology.defense-types.operation).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.operation>>
    = await client(com.palantir.ontology.defense-types.operation).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.operation.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.operation).subscribe(         {
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
        { properties: [ "start", "end", ]}
    );

subscription.unsubscribe();
```

### Load all Operation

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.operation>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.operation).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Operation metadata

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.operation);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Operation

```javascript
import { com.palantir.ontology.defense-types.operation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.operation>>> = await client(com.palantir.ontology.defense-types.operation)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```
