---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/com-palantir-ontology-defense-types-sigint/"
title: "SIGINT \u2022 API Reference"
---
# SIGINT

Palantir Defense OSDK

[Palantir Defense Ontology] The signals intelligence (SIGINT) interface defines the shape of SIGINT objects and extends the Intelligence interface.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Intelligence Ellipse Geometry | geoshapeType |  | False | [Palantir Defense Ontology] A geoshape property type used to capture the geometric coordinates of an ellipse. |
| Frequency (MHz) | doubleType |  | False | [Palantir Defense Ontology] A double property type used to capture the frequency in megahertz. |
| Semi-Major Axis (meters) | doubleType |  | False | [Palantir Defense Ontology] A double property type measuring the semi-major axis of an ellipse: the longest radius, from the center to the perimeter along the major axis. |
| Semi-Minor Axis (meters) | doubleType |  | False | [Palantir Defense Ontology] A double property type measuring the semi-minor axis of an ellipse: the shortest radius, from the center to the perimeter along the minor axis. |
| Axis Orientation (degrees) | doubleType |  | False | [Palantir Defense Ontology] A double property type capturing the orientation of an axis measured in degrees clockwise from north. |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Intelligence

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-intelligence

#### Extended By Interfaces

**displayName:** ELINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-elint

**displayName:** COMINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-comint

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.sigint>>> = await client(com.palantir.ontology.defense-types.sigint)
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
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.sigint.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.sigint).subscribe(         {
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
        { properties: [ "intelligenceEllipseGeometry", "frequencyMHz", "semiMajorAxisMeters", "semiMinorAxisMeters", "axisOrientation", ]}
    );

subscription.unsubscribe();
```

### Load all SIGINT

```javascript
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.sigint>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.sigint).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load SIGINT metadata

```javascript
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.sigint);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of SIGINT

```javascript
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.sigint>>>
    = await client(com.palantir.ontology.defense-types.sigint).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.sigint>>
    = await client(com.palantir.ontology.defense-types.sigint).fetchPage({ $pageSize: 30 });
```

### Load ordered SIGINT

```javascript
import { com.palantir.ontology.defense-types.sigint } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.sigint>>> = await client(com.palantir.ontology.defense-types.sigint)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```
