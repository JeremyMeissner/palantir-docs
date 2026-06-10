---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetEngagementAuthority/"
title: "Target Engagement Authority \u2022 API Reference"
---
# Target Engagement Authority

Palantir Defense OSDK

[Palantir Defense Ontology] A mandate given by a commander to a unit to direct target engagement on approved targets within an operational area.

## Properties

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The targeting area associated with this target engagement authority. |
| True | [Palantir Defense Ontology] The unit that owns and has authority over this target engagement authority. |
| False | [Palantir Defense Ontology] The targeting operations associated with this target engagement authority. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The set of target engagement authorities for a targeting guidance. |
| False | [Palantir Defense Ontology] The target engagement authority associated with this targeting area. |
| False | [Palantir Defense Ontology] The target engagement authorities owned by this unit. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetEngagementAuthority>>> = await client(com.palantir.ontology.defense-types.targetEngagementAuthority)
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

### Load pages of Target Engagement Authority

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetEngagementAuthority>>>
    = await client(com.palantir.ontology.defense-types.targetEngagementAuthority).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetEngagementAuthority>>
    = await client(com.palantir.ontology.defense-types.targetEngagementAuthority).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetEngagementAuthority.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetEngagementAuthority).subscribe(         {
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

### Load ordered Target Engagement Authority

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetEngagementAuthority>>> = await client(com.palantir.ontology.defense-types.targetEngagementAuthority)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load Target Engagement Authority metadata

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetEngagementAuthority);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all Target Engagement Authority

```javascript
import { com.palantir.ontology.defense-types.targetEngagementAuthority } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetEngagementAuthority>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetEngagementAuthority).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
