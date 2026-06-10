---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/com-palantir-ontology-defense-types-geoint/"
title: "GEOINT \u2022 API Reference"
---
# GEOINT

Palantir Defense OSDK

[Palantir Defense Ontology] Represents GEOINT which extends the Intelligence interface

## Properties

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Intelligence

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-intelligence

#### Extended By Interfaces

**displayName:** OPIR

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-opir

**displayName:** MTI

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-mti

**displayName:** IMINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-imint

## Code Snippets

### Load GEOINT metadata

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.geoint);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.geoint>>> = await client(com.palantir.ontology.defense-types.geoint)
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

### Load ordered GEOINT

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.geoint>>> = await client(com.palantir.ontology.defense-types.geoint)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all GEOINT

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.geoint>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.geoint).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.geoint.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.geoint).subscribe(         {
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

### Load pages of GEOINT

```javascript
import { com.palantir.ontology.defense-types.geoint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.geoint>>>
    = await client(com.palantir.ontology.defense-types.geoint).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.geoint>>
    = await client(com.palantir.ontology.defense-types.geoint).fetchPage({ $pageSize: 30 });
```
