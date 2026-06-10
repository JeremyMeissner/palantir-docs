---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-munitionEffectivenessAssessment/"
title: "Munition Effectiveness Assessment \u2022 API Reference"
---
# Munition Effectiveness Assessment

Palantir Defense OSDK

[Palantir Defense Ontology] The munition effectiveness assessment interface defines information needed to identify unintended or incidental damage to civilian persons, property, and the environment that may result from military operations, particularly the use of force

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Confidence Level | stringType | Assessment Confidence Level | True | [Palantir Defense Ontology] Confidence level for a munition effectiveness assessment |
| Time | timestampType |  | True | [Palantir Defense Ontology] The time a munition effectiveness assessment occurred |
| Scope | stringType |  | True | [Palantir Defense Ontology] Identifies the focus of the evaluation |
| Estimated Location | geohashType |  | False | [Palantir Defense Ontology] Location of a munition effectiveness assessment |
| Did Weapon Strike | stringType | Assessment Outcome | False | [Palantir Defense Ontology] Determines if the weapon struck |
| Was Weapon Effective | stringType | Assessment Outcome | False | [Palantir Defense Ontology] Determines if the weapon was effective |
| Notes | stringType |  | False | [Palantir Defense Ontology] Notes for a munition effectiveness assessment |

## Ontology Entity Type Content

### Interface Type

## Code Snippets

### Load all Munition Effectiveness Assessment

```javascript
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.munitionEffectivenessAssessment>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.munitionEffectivenessAssessment>>> = await client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment)
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
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.munitionEffectivenessAssessment.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment).subscribe(         {
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
        { properties: [ "confidenceLevel", "time", "scope", "estimatedLocation", "didWeaponStrike", "wasWeaponEffective", "notes", ]}
    );

subscription.unsubscribe();
```

### Load ordered Munition Effectiveness Assessment

```javascript
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.munitionEffectivenessAssessment>>> = await client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load Munition Effectiveness Assessment metadata

```javascript
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.munitionEffectivenessAssessment);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Munition Effectiveness Assessment

```javascript
import { com.palantir.ontology.defense-types.munitionEffectivenessAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.munitionEffectivenessAssessment>>>
    = await client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.munitionEffectivenessAssessment>>
    = await client(com.palantir.ontology.defense-types.munitionEffectivenessAssessment).fetchPage({ $pageSize: 30 });
```
