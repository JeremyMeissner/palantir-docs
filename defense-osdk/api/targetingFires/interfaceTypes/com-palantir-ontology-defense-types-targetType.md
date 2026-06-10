---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-targetType/"
title: "Target Type \u2022 API Reference"
---
# Target Type

Palantir Defense OSDK

[Palantir Defense Ontology] The categorization of equipment, building, organization, or other strategic asset.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Target Type | stringType |  | True | [Palantir Defense Ontology] The most specific and common designation of the target type. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A target type may be referenced by many targetable entitites. |
| False | [Palantir Defense Ontology] The target priorities associated with this target type. |
| False | [Palantir Defense Ontology] The attack guidances associated with this target type. |
| False | [Palantir Defense Ontology] The target selection standards associated with this target type. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| True | [Palantir Defense Ontology] The target type associated with this attack guidance. |
| True | [Palantir Defense Ontology] The target type associated with this target priority. |
| False | [Palantir Defense Ontology] A targetable entity may have a target type. |
| True | [Palantir Defense Ontology] The target type associated with this target selection standard. |

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetType>>> = await client(com.palantir.ontology.defense-types.targetType)
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

### Load ordered Target Type

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetType>>> = await client(com.palantir.ontology.defense-types.targetType)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.targetType.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.targetType).subscribe(         {
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
        { properties: [ "targetType", ]}
    );

subscription.unsubscribe();
```

### Load all Target Type

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.targetType>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.targetType).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Target Type metadata

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.targetType);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load pages of Target Type

```javascript
import { com.palantir.ontology.defense-types.targetType } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.targetType>>>
    = await client(com.palantir.ontology.defense-types.targetType).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.targetType>>
    = await client(com.palantir.ontology.defense-types.targetType).fetchPage({ $pageSize: 30 });
```
