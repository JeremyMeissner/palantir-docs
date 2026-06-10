---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetSelectionStandard/"
title: "Target Selection Standard \u2022 API Reference"
---
# Target Selection Standard

Palantir Defense OSDK

[Palantir Defense Ontology] The accuracy requirements and specific criteria that must be met before targets of a certain type can be engaged.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Accuracy (meters) | integerType |  | True | Maximum allowed circular geospatial error of the target intelligence in meters. |
| Timeliness (seconds) | integerType |  | True | Minimum recency of the target intelligence in seconds. |
| Mobility | stringType | Mobility | True | Indicates the specificity of the selection standards on mobile or immobile targets. Omitted if it should apply to both. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The Target Selection Standard Matrix that this standard belongs to. |
| False | [Palantir Defense Ontology] The targeting area associated with this target selection standard. |
| True | [Palantir Defense Ontology] The target type associated with this target selection standard. |
| False | [Palantir Defense Ontology] The ammunition type associated with this target selection standard. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] The target selection standards associated with this target type. |
| False | [Palantir Defense Ontology] The target selection standards associated with this ammunition type. |
| False | [Palantir Defense Ontology] The target selection standards associated with this targeting area. |
| True | [Palantir Defense Ontology] The set of target selection standards for a Target Selection Standard Matrix. |

## Code Snippets

### Load ordered Target Selection Standard

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandard>>> = await client(com.palantir.ontology.defense-types.targetSelectionStandard)
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
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandard>>> = await client(com.palantir.ontology.defense-types.targetSelectionStandard)
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
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetSelectionStandard.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetSelectionStandard).subscribe(         {
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
        { properties: [ "accuracy", "timeliness", "mobility", ]}
    );

subscription.unsubscribe();
```

### Load all Target Selection Standard

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetSelectionStandard>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetSelectionStandard).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Target Selection Standard metadata

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetSelectionStandard);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Target Selection Standard

```javascript
import { com.palantir.ontology.defense-types.targetSelectionStandard } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandard>>>
    = await client(com.palantir.ontology.defense-types.targetSelectionStandard).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetSelectionStandard>>
    = await client(com.palantir.ontology.defense-types.targetSelectionStandard).fetchPage({ $pageSize: 30 });
```
