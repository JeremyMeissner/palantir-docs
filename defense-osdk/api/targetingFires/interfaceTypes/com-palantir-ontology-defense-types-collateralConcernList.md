---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-collateralConcernList/"
title: "Collateral Concern List \u2022 API Reference"
---
# Collateral Concern List

Palantir Defense OSDK

[Palantir Defense Ontology] Defines a collection of collateral concerns that can be referenced during the target development process.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Description | stringType |  | False | [Palantir Defense Ontology] Human-readable description of a collateral concern list. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] Links a collateral concern list to all entities that are a member of that list. Collateral concern lists have a many-to-many relationship with collateral concern entities. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] Links a collateral concern entity to all lists it is a member of. Collateral concern entities have a many-to-many relationship with collateral concern lists. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernList>>> = await client(com.palantir.ontology.defense-types.collateralConcernList)
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

### Load Collateral Concern List metadata

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.collateralConcernList);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Collateral Concern List

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernList>>>
    = await client(com.palantir.ontology.defense-types.collateralConcernList).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernList>>
    = await client(com.palantir.ontology.defense-types.collateralConcernList).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.collateralConcernList.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.collateralConcernList).subscribe(         {
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
        { properties: [ "description", ]}
    );

subscription.unsubscribe();
```

### Load ordered Collateral Concern List

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralConcernList>>> = await client(com.palantir.ontology.defense-types.collateralConcernList)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Collateral Concern List

```javascript
import { com.palantir.ontology.defense-types.collateralConcernList } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.collateralConcernList>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.collateralConcernList).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
