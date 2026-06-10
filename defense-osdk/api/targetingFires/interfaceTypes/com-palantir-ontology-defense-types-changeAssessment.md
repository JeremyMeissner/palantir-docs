---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-changeAssessment/"
title: "Change Assessment \u2022 API Reference"
---
# Change Assessment

Palantir Defense OSDK

[Palantir Defense Ontology] The change assessment interface defines information needed to identify measurable change of a target resulting from the application of lethal or nonlethal military force

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Change Effect Level | stringType | Change Effect Level | True | [Palantir Defense Ontology] Effect level for change assessments |
| Time | timestampType |  | True | [Palantir Defense Ontology] The time a change assessment occurred |
| Confidence Level | stringType | Assessment Confidence Level | True | [Palantir Defense Ontology] Confidence level for a change assessment |
| Location | geohashType |  | False | [Palantir Defense Ontology] Location of a change assessment |
| Notes | stringType |  | False | [Palantir Defense Ontology] Notes for a change assessment |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A change assessment may have supporting intelligence. |
| False | [Palantir Defense Ontology] One change assessment may be linked to many target assessments. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many change assessments. |
| False | [Palantir Defense Ontology] One target assessment has one change assessment. |

## Code Snippets

### Load ordered Change Assessment

```javascript
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.changeAssessment>>> = await client(com.palantir.ontology.defense-types.changeAssessment)
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
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.changeAssessment>>> = await client(com.palantir.ontology.defense-types.changeAssessment)
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

### Load all Change Assessment

```javascript
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.changeAssessment>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.changeAssessment).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Change Assessment metadata

```javascript
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.changeAssessment);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Change Assessment

```javascript
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.changeAssessment>>>
    = await client(com.palantir.ontology.defense-types.changeAssessment).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.changeAssessment>>
    = await client(com.palantir.ontology.defense-types.changeAssessment).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.changeAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.changeAssessment.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.changeAssessment).subscribe(         {
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
        { properties: [ "changeEffectLevel", "time", "confidenceLevel", "location", "notes", ]}
    );

subscription.unsubscribe();
```
