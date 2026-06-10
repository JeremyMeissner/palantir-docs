---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/com-palantir-ontology-defense-types-mti/"
title: "MTI \u2022 API Reference"
---
# MTI

Palantir Defense OSDK

[Palantir Defense Ontology] Represents MTI which extends the GEOINT interface

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Intelligence Ellipse Geometry | geoshapeType |  | False | [Palantir Defense Ontology] A geoshape property type used to capture the geometric coordinates of an ellipse. |
| Semi-Major Axis (meters) | doubleType |  | False | [Palantir Defense Ontology] A double property type measuring the longest radius of an ellipse, or the distance from the center of the ellipse to its furthest edge. |
| Semi-Minor Axis (meters) | doubleType |  | False | [Palantir Defense Ontology] A double property type measuring the shortest radius of an ellipse, or the distance from the center of the ellipse to its closest edge. |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** GEOINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-geoint

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.mti>>> = await client(com.palantir.ontology.defense-types.mti)
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

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.mti.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.mti).subscribe(         {
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
        { properties: [ "intelligenceEllipseGeometry", "semiMajorAxisMeters", "semiMinorAxisMeters", ]}
    );

subscription.unsubscribe();
```

### Load pages of MTI

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.mti>>>
    = await client(com.palantir.ontology.defense-types.mti).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.mti>>
    = await client(com.palantir.ontology.defense-types.mti).fetchPage({ $pageSize: 30 });
```

### Load ordered MTI

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.mti>>> = await client(com.palantir.ontology.defense-types.mti)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all MTI

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.mti>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.mti).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load MTI metadata

```javascript
import { com.palantir.ontology.defense-types.mti } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.mti);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
