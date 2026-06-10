---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetAssessment/"
title: "Target Assessment \u2022 API Reference"
---
# Target Assessment

Palantir Defense OSDK

[Palantir Defense Ontology] A analysis of the effects that a single targeting endeavor had on the corresponding entity.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Serviced | booleanType |  | True | [Palantir Defense Ontology] Indicates whether an attempt was made to effect this target. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] One target assessment has one target. |
| False | [Palantir Defense Ontology] One target assessment has one functional assessment. |
| False | [Palantir Defense Ontology] One target assessment has one change assessment. |
| False | [Palantir Defense Ontology] One target assessment has one collateral damage assessment. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One change assessment may be linked to many target assessments. |
| False | [Palantir Defense Ontology] One collateral damage assessment may be linked to many target assessments. |
| False | [Palantir Defense Ontology] One functional assessment may be linked to many target assessments. |
| False | [Palantir Defense Ontology] One target may have many target assessments. |

## Code Snippets

### Load Target Assessment metadata

```javascript
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetAssessment);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Target Assessment

```javascript
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetAssessment>>> = await client(com.palantir.ontology.defense-types.targetAssessment)
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
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetAssessment>>> = await client(com.palantir.ontology.defense-types.targetAssessment)
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

### Load all Target Assessment

```javascript
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetAssessment>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetAssessment).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetAssessment.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetAssessment).subscribe(         {
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
        { properties: [ "serviced", ]}
    );

subscription.unsubscribe();
```

### Load pages of Target Assessment

```javascript
import { com.palantir.ontology.defense-types.targetAssessment } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetAssessment>>>
    = await client(com.palantir.ontology.defense-types.targetAssessment).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetAssessment>>
    = await client(com.palantir.ontology.defense-types.targetAssessment).fetchPage({ $pageSize: 30 });
```
