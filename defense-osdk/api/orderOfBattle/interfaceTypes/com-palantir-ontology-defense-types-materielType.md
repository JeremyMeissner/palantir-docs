---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-materielType/"
title: "Materiel Type \u2022 API Reference"
---
# Materiel Type

Palantir Defense OSDK

[Palantir Defense Ontology] A type or category of materiel.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Nomenclature | stringType |  | True | Nomenclature of a materiel type. |

## Ontology Entity Type Content

### Interface Type

#### Extended By Interfaces

**displayName:** Ammunition Type

**relativeDocsLink:** orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-ammunitionType

**displayName:** Equipment Type

**relativeDocsLink:** orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-equipmentType

## Code Snippets

### Load ordered Materiel Type

```javascript
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.materielType>>> = await client(com.palantir.ontology.defense-types.materielType)
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
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.materielType>>> = await client(com.palantir.ontology.defense-types.materielType)
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

### Load pages of Materiel Type

```javascript
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.materielType>>>
    = await client(com.palantir.ontology.defense-types.materielType).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.materielType>>
    = await client(com.palantir.ontology.defense-types.materielType).fetchPage({ $pageSize: 30 });
```

### Load Materiel Type metadata

```javascript
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.materielType);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.materielType.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.materielType).subscribe(         {
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
        { properties: [ "nomenclature", ]}
    );

subscription.unsubscribe();
```

### Load all Materiel Type

```javascript
import { com.palantir.ontology.defense-types.materielType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.materielType>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.materielType).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
