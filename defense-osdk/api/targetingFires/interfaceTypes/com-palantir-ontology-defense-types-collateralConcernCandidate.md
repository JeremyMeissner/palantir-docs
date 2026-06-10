---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-collateralConcernCandidate/"
title: "Collateral Concern Candidate \u2022 API Reference"
---
# Collateral Concern Candidate

Palantir Defense OSDK

[Palantir Defense Ontology] Interface which indicates entities may be identified as collateral concerns.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Extended By Interfaces

**displayName:** Geometry-Based Collateral Concern Candidate

**relativeDocsLink:** targetingFires/interfaceTypes/com-palantir-ontology-defense-types-collateralConcernCandidateWithGeometry

**displayName:** Point-Based Collateral Concern Candidate

**relativeDocsLink:** targetingFires/interfaceTypes/com-palantir-ontology-defense-types-collateralConcernCandidatePoint

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] Links a collateral concern entity to all lists it is a member of. Collateral concern entities have a many-to-many relationship with collateral concern lists. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] Links a collateral concern list to all entities that are a member of that list. Collateral concern lists have a many-to-many relationship with collateral concern entities. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernCandidate>>> = await client(com.palantir.ontology.defense-types.collateralConcernCandidate)
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
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.collateralConcernCandidate.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.collateralConcernCandidate).subscribe(         {
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

### Load Collateral Concern Candidate metadata

```javascript
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.collateralConcernCandidate);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Collateral Concern Candidate

```javascript
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernCandidate>>> = await client(com.palantir.ontology.defense-types.collateralConcernCandidate)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Collateral Concern Candidate

```javascript
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.collateralConcernCandidate>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.collateralConcernCandidate).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load pages of Collateral Concern Candidate

```javascript
import { com.palantir.ontology.defense-types.collateralConcernCandidate } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernCandidate>>>
    = await client(com.palantir.ontology.defense-types.collateralConcernCandidate).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernCandidate>>
    = await client(com.palantir.ontology.defense-types.collateralConcernCandidate).fetchPage({ $pageSize: 30 });
```
