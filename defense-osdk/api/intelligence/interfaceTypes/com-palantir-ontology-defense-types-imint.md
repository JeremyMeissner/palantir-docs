---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/com-palantir-ontology-defense-types-imint/"
title: "IMINT \u2022 API Reference"
---
# IMINT

Palantir Defense OSDK

[Palantir Defense Ontology] Represents IMINT which extends the GEOINT interface

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Image Media URL | stringType |  | False | [Palantir Defense Ontology] The media URL for the image associated with an IMINT observation |
| Image Media Reference | mediaReferenceType |  | False | [Palantir Defense Ontology] The media reference for the image associated with an IMINT observation |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** GEOINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-geoint

## Code Snippets

### Load pages of IMINT

```javascript
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.imint>>>
    = await client(com.palantir.ontology.defense-types.imint).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.imint>>
    = await client(com.palantir.ontology.defense-types.imint).fetchPage({ $pageSize: 30 });
```

### Load IMINT metadata

```javascript
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.imint);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.imint>>> = await client(com.palantir.ontology.defense-types.imint)
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

### Load ordered IMINT

```javascript
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.imint>>> = await client(com.palantir.ontology.defense-types.imint)
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
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.imint.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.imint).subscribe(         {
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
        { properties: [ "imageMediaUrl", "imageMediaReference", ]}
    );

subscription.unsubscribe();
```

### Load all IMINT

```javascript
import { com.palantir.ontology.defense-types.imint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.imint>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.imint).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
