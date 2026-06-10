---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetingArea/"
title: "Targeting Area \u2022 API Reference"
---
# Targeting Area

Palantir Defense OSDK

[Palantir Defense Ontology] A portion physical space divided for the purpose of managing and delegating targeting responsibilities.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Area | geoshapeType |  | True | The geoshape representing this targeting area. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The target priorities associated with this targeting area. |
| False | [Palantir Defense Ontology] The attack guidances associated with this targeting area. |
| False | [Palantir Defense Ontology] The target selection standards associated with this targeting area. |
| False | [Palantir Defense Ontology] The target engagement authority associated with this targeting area. |
| False | [Palantir Defense Ontology] The targeting operations associated with this targeting area. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The targeting area associated with this attack guidance. |
| False | [Palantir Defense Ontology] The targeting area associated with this target priority. |
| True | [Palantir Defense Ontology] The targeting areas associated with this targeting operation. |
| False | [Palantir Defense Ontology] The targeting area associated with this target selection standard. |
| True | [Palantir Defense Ontology] The targeting area associated with this target engagement authority. |

## Code Snippets

### Load pages of Targeting Area

```javascript
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingArea>>>
    = await client(com.palantir.ontology.defense-types.targetingArea).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetingArea>>
    = await client(com.palantir.ontology.defense-types.targetingArea).fetchPage({ $pageSize: 30 });
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingArea>>> = await client(com.palantir.ontology.defense-types.targetingArea)
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

### Load ordered Targeting Area

```javascript
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetingArea>>> = await client(com.palantir.ontology.defense-types.targetingArea)
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
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetingArea.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetingArea).subscribe(         {
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
        { properties: [ "area", ]}
    );

subscription.unsubscribe();
```

### Load Targeting Area metadata

```javascript
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetingArea);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all Targeting Area

```javascript
import { com.palantir.ontology.defense-types.targetingArea } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetingArea>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetingArea).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
