---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-unitType/"
title: "Unit Type \u2022 API Reference"
---
# Unit Type

Palantir Defense OSDK

[Palantir Defense Ontology] Reference to the type of unit, such as Infantry, Artillery, or SOF.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Unit Type | stringType |  | True | [Palantir Defense Ontology] Captures a unit type. |
| Abbreviated Unit Type | stringType |  | True | [Palantir Defense Ontology] Used to capture the shortened name of a unit type, such as IN or AR. |
| Definition | stringType |  | True | [Palantir Defense Ontology] Captures doctrinal definition information for a unit type. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit type can link to many units. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit can have one unit type. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitType>>> = await client(com.palantir.ontology.defense-types.unitType)
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

### Load ordered Unit Type

```javascript
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitType>>> = await client(com.palantir.ontology.defense-types.unitType)
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
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.unitType.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.unitType).subscribe(         {
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
        { properties: [ "unitType", "abbreviatedUnitType", "definition", ]}
    );

subscription.unsubscribe();
```

### Load pages of Unit Type

```javascript
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.unitType>>>
    = await client(com.palantir.ontology.defense-types.unitType).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.unitType>>
    = await client(com.palantir.ontology.defense-types.unitType).fetchPage({ $pageSize: 30 });
```

### Load all Unit Type

```javascript
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.unitType>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.unitType).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Unit Type metadata

```javascript
import { com.palantir.ontology.defense-types.unitType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.unitType);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
