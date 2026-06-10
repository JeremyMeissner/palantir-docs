---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-target/"
title: "Target \u2022 API Reference"
---
# Target

Palantir Defense OSDK

[Palantir Defense Ontology] A task representing a single combined attempt to impose an effect on a targetable entity.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Target Number | stringType |  | True | [Palantir Defense Ontology] A shorthand alphanumeric identifier for the target. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] A target must link to one targetable entity. |
| False | [Palantir Defense Ontology] One target may have many target assessments. |
| False | [Palantir Defense Ontology] The Targeting Operation leveraged by this target. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A targetable entity may have many attempts to target it. |
| True | [Palantir Defense Ontology] The set of targets leveraging this operation for their targeting guidance. |
| True | [Palantir Defense Ontology] One target assessment has one target. |

## Code Snippets

### Load all Target

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.target>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.target).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.target>>> = await client(com.palantir.ontology.defense-types.target)
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

### Load Target metadata

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.target);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.target.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.target).subscribe(         {
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
        { properties: [ "targetNumber", ]}
    );

subscription.unsubscribe();
```

### Load ordered Target

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.target>>> = await client(com.palantir.ontology.defense-types.target)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Target

```javascript
import { com.palantir.ontology.defense-types.target } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.target>>>
    = await client(com.palantir.ontology.defense-types.target).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.target>>
    = await client(com.palantir.ontology.defense-types.target).fetchPage({ $pageSize: 30 });
```
