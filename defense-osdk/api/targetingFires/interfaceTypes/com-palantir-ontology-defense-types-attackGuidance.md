---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-attackGuidance/"
title: "Attack Guidance \u2022 API Reference"
---
# Attack Guidance

Palantir Defense OSDK

[Palantir Defense Ontology] Outlines the prioritized desired effects on target types and the methods with which those effects are approved to be carried out.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| effectPriority | integerType |  | True | The relative priority level of the attack guidance. |
| Desired Effect | stringType | Kinetic Effect | True | Desired effect outcome |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The Attack Guidance Matrix that this attack guidance belongs to. |
| False | [Palantir Defense Ontology] The targeting area associated with this attack guidance. |
| True | [Palantir Defense Ontology] The target type associated with this attack guidance. |
| False | [Palantir Defense Ontology] The ammunition type associated with this attack guidance. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The attack guidances associated with this target type. |
| False | [Palantir Defense Ontology] The attack guidances associated with this ammunition type. |
| False | [Palantir Defense Ontology] The attack guidances associated with this targeting area. |
| True | [Palantir Defense Ontology] The set of target attack guidelines for an Attack Guidance Matrix. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidance>>> = await client(com.palantir.ontology.defense-types.attackGuidance)
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

### Load Attack Guidance metadata

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.attackGuidance);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Attack Guidance

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidance>>> = await client(com.palantir.ontology.defense-types.attackGuidance)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Attack Guidance

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidance>>>
    = await client(com.palantir.ontology.defense-types.attackGuidance).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.attackGuidance>>
    = await client(com.palantir.ontology.defense-types.attackGuidance).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.attackGuidance.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.attackGuidance).subscribe(         {
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
        { properties: [ "effectPriority", "desiredEffect", ]}
    );

subscription.unsubscribe();
```

### Load all Attack Guidance

```javascript
import { com.palantir.ontology.defense-types.attackGuidance } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.attackGuidance>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.attackGuidance).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
