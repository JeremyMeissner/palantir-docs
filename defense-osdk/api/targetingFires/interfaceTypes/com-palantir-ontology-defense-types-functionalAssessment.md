---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-functionalAssessment/"
title: "Functional Assessment \u2022 API Reference"
---
# Functional Assessment

Palantir Defense OSDK

[Palantir Defense Ontology] The functional assessment interface defines information needed to estimate the effect of military force to degrade or destroy the functional or operational capability of a target

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Functional Effect Level | stringType | Functional Effect Level | True | [Palantir Defense Ontology] Effect level for functional assessments |
| Time | timestampType |  | True | [Palantir Defense Ontology] The time a functional assessment occurred |
| Confidence Level | stringType | Assessment Confidence Level | True | [Palantir Defense Ontology] Confidence level for a functional assessment |
| Location | geohashType |  | False | [Palantir Defense Ontology] Location of a functional assessment |
| Notes | stringType |  | False | [Palantir Defense Ontology] Notes for a functional assessment |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One functional assessment may have supporting intelligence |
| False | [Palantir Defense Ontology] One functional assessment may be linked to many target assessments. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many functional assessments. |
| False | [Palantir Defense Ontology] One target assessment has one functional assessment. |

## Code Snippets

### Load Functional Assessment metadata

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.functionalAssessment);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.functionalAssessment>>> = await client(com.palantir.ontology.defense-types.functionalAssessment)
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

### Load ordered Functional Assessment

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.functionalAssessment>>> = await client(com.palantir.ontology.defense-types.functionalAssessment)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Functional Assessment

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.functionalAssessment>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.functionalAssessment).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.functionalAssessment.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.functionalAssessment).subscribe(         {
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
        { properties: [ "functionalEffectLevel", "time", "confidenceLevel", "location", "notes", ]}
    );

subscription.unsubscribe();
```

### Load pages of Functional Assessment

```javascript
import { com.palantir.ontology.defense-types.functionalAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.functionalAssessment>>>
    = await client(com.palantir.ontology.defense-types.functionalAssessment).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.functionalAssessment>>
    = await client(com.palantir.ontology.defense-types.functionalAssessment).fetchPage({ $pageSize: 30 });
```
