---
source_url: "https://www.palantir.com/docs/defense-osdk/api/common/interfaceTypes/com-palantir-ontology-defense-types-report/"
title: "Report \u2022 API Reference"
---
# Report

Palantir Defense OSDK

[Palantir Defense Ontology] A generic Report which captures observations about entities.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Timestamp | timestampType |  | True | [Palantir Defense Ontology] The timestamp a report was created. |

## Ontology Entity Type Content

### Interface Type

#### Extended By Interfaces

**displayName:** Intelligence Report

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-intelligenceReport

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One Report can link to many Report Observations |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One Report Observation can link to many Reports |

## Code Snippets

### Load pages of Report

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.report>>>
    = await client(com.palantir.ontology.defense-types.report).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.report>>
    = await client(com.palantir.ontology.defense-types.report).fetchPage({ $pageSize: 30 });
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.report>>> = await client(com.palantir.ontology.defense-types.report)
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

### Load Report metadata

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.report);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all Report

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.report>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.report).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.report.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.report).subscribe(         {
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
        { properties: [ "timestamp", ]}
    );

subscription.unsubscribe();
```

### Load ordered Report

```javascript
import { com.palantir.ontology.defense-types.report } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.report>>> = await client(com.palantir.ontology.defense-types.report)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```
