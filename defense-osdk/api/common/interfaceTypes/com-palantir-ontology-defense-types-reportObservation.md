---
source_url: "https://www.palantir.com/docs/defense-osdk/api/common/interfaceTypes/com-palantir-ontology-defense-types-reportObservation/"
title: "Report Observation \u2022 API Reference"
---
# Report Observation

Palantir Defense OSDK

[Palantir Defense Ontology] An observation or line item in a Report.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One Report Observation can link to many Reports |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One Report can link to many Report Observations |

## Code Snippets

### Load ordered Report Observation

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.reportObservation>>> = await client(com.palantir.ontology.defense-types.reportObservation)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.reportObservation>>> = await client(com.palantir.ontology.defense-types.reportObservation)
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

### Load all Report Observation

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.reportObservation>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.reportObservation).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.reportObservation.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.reportObservation).subscribe(         {
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

### Load pages of Report Observation

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.reportObservation>>>
    = await client(com.palantir.ontology.defense-types.reportObservation).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.reportObservation>>
    = await client(com.palantir.ontology.defense-types.reportObservation).fetchPage({ $pageSize: 30 });
```

### Load Report Observation metadata

```javascript
import { com.palantir.ontology.defense-types.reportObservation } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.reportObservation);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
