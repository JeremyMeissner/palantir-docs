---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/com-palantir-ontology-defense-types-comint/"
title: "COMINT \u2022 API Reference"
---
# COMINT

Palantir Defense OSDK

[Palantir Defense Ontology] The communications signals intelligence (COMINT) interface defines the shape of COMINT objects and extends the SIGINT and Intelligence interfaces

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| CENOT | stringType |  | False | [Palantir Defense Ontology] Communications emitter notation. |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** SIGINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-sigint

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.comint>>> = await client(com.palantir.ontology.defense-types.comint)
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

### Load pages of COMINT

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.comint>>>
    = await client(com.palantir.ontology.defense-types.comint).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.comint>>
    = await client(com.palantir.ontology.defense-types.comint).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.comint.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.comint).subscribe(         {
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
        { properties: [ "cenot", ]}
    );

subscription.unsubscribe();
```

### Load ordered COMINT

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.comint>>> = await client(com.palantir.ontology.defense-types.comint)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load COMINT metadata

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.comint);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all COMINT

```javascript
import { com.palantir.ontology.defense-types.comint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.comint>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.comint).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
