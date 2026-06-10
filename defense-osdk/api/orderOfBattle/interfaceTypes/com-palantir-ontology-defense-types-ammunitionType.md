---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-ammunitionType/"
title: "Ammunition Type \u2022 API Reference"
---
# Ammunition Type

Palantir Defense OSDK

[Palantir Defense Ontology] A type or category of ammunition.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Extended Interfaces

**displayName:** Materiel Type

**relativeDocsLink:** orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-materielType

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The attack guidances associated with this ammunition type. |
| False | [Palantir Defense Ontology] The target selection standards associated with this ammunition type. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The ammunition type associated with this attack guidance. |
| False | [Palantir Defense Ontology] The ammunition type associated with this target selection standard. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.ammunitionType>>> = await client(com.palantir.ontology.defense-types.ammunitionType)
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

### Load Ammunition Type metadata

```javascript
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.ammunitionType);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Ammunition Type

```javascript
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.ammunitionType>>> = await client(com.palantir.ontology.defense-types.ammunitionType)
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
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.ammunitionType.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.ammunitionType).subscribe(         {
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

### Load pages of Ammunition Type

```javascript
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.ammunitionType>>>
    = await client(com.palantir.ontology.defense-types.ammunitionType).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.ammunitionType>>
    = await client(com.palantir.ontology.defense-types.ammunitionType).fetchPage({ $pageSize: 30 });
```

### Load all Ammunition Type

```javascript
import { com.palantir.ontology.defense-types.ammunitionType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.ammunitionType>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.ammunitionType).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
