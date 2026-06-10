---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-collateralDamageAssessment/"
title: "Collateral Damage Assessment \u2022 API Reference"
---
# Collateral Damage Assessment

Palantir Defense OSDK

[Palantir Defense Ontology] The collateral damage assessment interface defines information needed to identify unintended or incidental damage to civilian persons, property, and the environment that may result from military operations, particularly the use of force

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Has Collateral Damage | stringType | Assessment Outcome | True | [Palantir Defense Ontology] Determines if there is collateral damage |
| Damage Estimate | stringType |  | True | [Palantir Defense Ontology] Estimate the collateral damage |
| Timestamp | timestampType |  | True | [Palantir Defense Ontology] The time a collateral damage assessment occurred |
| Confidence Level | stringType | Assessment Confidence Level | True | [Palantir Defense Ontology] Confidence level for a collateral damage assessment |
| Notes | stringType |  | False | [Palantir Defense Ontology] Notes for a collateral damage assessment |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One collateral damage assessment may have supporting intelligence. |
| False | [Palantir Defense Ontology] One collateral damage assessment may be linked to many target assessments. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many collateral damage assessments. |
| False | [Palantir Defense Ontology] One target assessment has one collateral damage assessment. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralDamageAssessment>>> = await client(com.palantir.ontology.defense-types.collateralDamageAssessment)
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
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.collateralDamageAssessment.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.collateralDamageAssessment).subscribe(         {
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
        { properties: [ "hasCollateralDamage", "damageEstimate", "timestamp", "confidenceLevel", "notes", ]}
    );

subscription.unsubscribe();
```

### Load Collateral Damage Assessment metadata

```javascript
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.collateralDamageAssessment);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Collateral Damage Assessment

```javascript
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralDamageAssessment>>> = await client(com.palantir.ontology.defense-types.collateralDamageAssessment)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Collateral Damage Assessment

```javascript
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.collateralDamageAssessment>>>
    = await client(com.palantir.ontology.defense-types.collateralDamageAssessment).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.collateralDamageAssessment>>
    = await client(com.palantir.ontology.defense-types.collateralDamageAssessment).fetchPage({ $pageSize: 30 });
```

### Load all Collateral Damage Assessment

```javascript
import { com.palantir.ontology.defense-types.collateralDamageAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.collateralDamageAssessment>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.collateralDamageAssessment).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
