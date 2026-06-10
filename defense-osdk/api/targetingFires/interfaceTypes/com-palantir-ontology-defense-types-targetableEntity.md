---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetableEntity/"
title: "Targetable Entity \u2022 API Reference"
---
# Targetable Entity

Palantir Defense OSDK

[Palantir Defense Ontology] A non-fungible representation of a corporeal asset with military significance.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Location | geohashType |  | False | [Palantir Defense Ontology] The geospatial position of the targetable entity. |

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Intelligence Subject

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-intelligenceSubject

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A targetable entity may have many attempts to target it. |
| False | [Palantir Defense Ontology] A targetable entity may have a target type. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A target type may be referenced by many targetable entitites. |
| True | [Palantir Defense Ontology] A target must link to one targetable entity. |

## Code Snippets

### Load Targetable Entity metadata

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetableEntity);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetableEntity>>> = await client(com.palantir.ontology.defense-types.targetableEntity)
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

### Load ordered Targetable Entity

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetableEntity>>> = await client(com.palantir.ontology.defense-types.targetableEntity)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Targetable Entity

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetableEntity>>>
    = await client(com.palantir.ontology.defense-types.targetableEntity).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetableEntity>>
    = await client(com.palantir.ontology.defense-types.targetableEntity).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetableEntity.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetableEntity).subscribe(         {
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
        { properties: [ "location", ]}
    );

subscription.unsubscribe();
```

### Load all Targetable Entity

```javascript
import { com.palantir.ontology.defense-types.targetableEntity } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetableEntity>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetableEntity).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
