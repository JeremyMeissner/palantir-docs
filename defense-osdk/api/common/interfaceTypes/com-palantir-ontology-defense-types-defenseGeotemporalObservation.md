---
source_url: "https://www.palantir.com/docs/defense-osdk/api/common/interfaceTypes/com-palantir-ontology-defense-types-defenseGeotemporalObservation/"
title: "Defense Geotemporal Observation \u2022 API Reference"
---
# Defense Geotemporal Observation

Palantir Defense OSDK

[Palantir Defense Ontology] This interface defines an "observation" as a timestamped position, which may encode geotemporal data from sensors, tracked entities, and other defense specific sources.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Track Quality | integerType | Track Quality | False | [Palantir Defense Ontology] An integer from 1 to 15 that indicates the Track Quality of the Geotemporal Observation |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Geotemporal Observation

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.defenseGeotemporalObservation>>> = await client(com.palantir.ontology.defense-types.defenseGeotemporalObservation)
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

### Load pages of Defense Geotemporal Observation

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.defenseGeotemporalObservation>>>
    = await client(com.palantir.ontology.defense-types.defenseGeotemporalObservation).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.defenseGeotemporalObservation>>
    = await client(com.palantir.ontology.defense-types.defenseGeotemporalObservation).fetchPage({ $pageSize: 30 });
```

### Load Defense Geotemporal Observation metadata

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.defenseGeotemporalObservation);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.defenseGeotemporalObservation.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.defenseGeotemporalObservation).subscribe(         {
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
        { properties: [ "trackQuality", ]}
    );

subscription.unsubscribe();
```

### Load all Defense Geotemporal Observation

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.defenseGeotemporalObservation>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.defenseGeotemporalObservation).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load ordered Defense Geotemporal Observation

```javascript
import { com.palantir.ontology.defense-types.defenseGeotemporalObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.defenseGeotemporalObservation>>> = await client(com.palantir.ontology.defense-types.defenseGeotemporalObservation)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```
