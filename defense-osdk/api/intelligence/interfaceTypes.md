---
source_url: "https://www.palantir.com/docs/defense-osdk/api/intelligence/interfaceTypes/"
title: "Intelligence \u2022 API Reference"
---
# Intelligence

Palantir Defense OSDK

[Palantir Defense Ontology] Categorized intelligence alongside its most critical metadata, such as its originating source system, location, and last updated time.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Normalized Confidence | integerType | Normalized Confidence | False | [Palantir Defense Ontology] Used by intelligence-related object types to categorize the confidence of instances of intelligence as 1-5. Unique confidence systems must be normalized to fit the 1-5 numeric scale. |
| Reported Timestamp | timestampType |  | True | [Palantir Defense Ontology] Used by intelligence-related interfaces to capture reported timestamp. |
| Reported Position | geohashType |  | False | [Palantir Defense Ontology] Used by intelligence-related interfaces to capture reported position |

## Ontology Entity Type Content

### Interface Type

#### Extended By Interfaces

**displayName:** GEOINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-geoint

**displayName:** OSINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-osint

**displayName:** SIGINT

**relativeDocsLink:** intelligence/interfaceTypes/com-palantir-ontology-defense-types-sigint

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One intelligence object may link to many intelligence subjects. |
| False | [Palantir Defense Ontology] One intelligence object may link to many intelligence producers. |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many change assessments. |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many functional assessments. |
| False | [Palantir Defense Ontology] One intelligence object may be supporting evidence for many collateral damage assessments. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] One intelligence subject may link to many intelligence objects. |
| False | [Palantir Defense Ontology] A change assessment may have supporting intelligence. |
| False | [Palantir Defense Ontology] One intelligence producer may link to many intelligence objects. |
| False | [Palantir Defense Ontology] One collateral damage assessment may have supporting intelligence. |
| False | [Palantir Defense Ontology] One functional assessment may have supporting intelligence |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.intelligence>>> = await client(com.palantir.ontology.defense-types.intelligence)
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

### Load pages of Intelligence

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.intelligence>>>
    = await client(com.palantir.ontology.defense-types.intelligence).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.intelligence>>
    = await client(com.palantir.ontology.defense-types.intelligence).fetchPage({ $pageSize: 30 });
```

### Load ordered Intelligence

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.intelligence>>> = await client(com.palantir.ontology.defense-types.intelligence)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load all Intelligence

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.intelligence>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.intelligence).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.intelligence.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.intelligence).subscribe(         {
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
        { properties: [ "normalizedConfidence", "reportedTimestamp", "reportedPosition", ]}
    );

subscription.unsubscribe();
```

### Load Intelligence metadata

```javascript
import { com.palantir.ontology.defense-types.intelligence } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.intelligence);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```
