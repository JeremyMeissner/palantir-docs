---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/"
title: "Unit \u2022 API Reference"
---
# Unit

Palantir Defense OSDK

[Palantir Defense Ontology] Represents the entity that owns and is responsible for materiel and the relationship between organizations and their chain of command. An object type that implements this interface would be, for example, a Unit.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Unit Identifier | stringType |  | False | [Palantir Defense Ontology] A semantically meaningful identifier for the unit, such as a Unit Identification Code (UIC). |
| Military Service | stringType | Military Service | False | [Palantir Defense Ontology] Identifies the military branch of a friendly or enemy unit. |
| Echelon | stringType | Unit Echelon | False | [Palantir Defense Ontology] Identifies the echelon of a unit, such as Brigade or Corps. |
| SIDC | stringType |  | False | [Palantir Defense Ontology] A Symbol Identification Code is an alphanumeric identifier that uniquely identifies and displays a military symbol. Its format depends on the standard used, such as MIL-STD 2525C or MIL-STD 2525D. |
| Affiliation | stringType | MIL2525 Affiliation | False | [Palantir Defense Ontology] Describes the affiliation of the unit, such as Friend or Hostile. |
| Allegiance | stringType |  | False | [Palantir Defense Ontology] Captures the country of allegiance for the unit. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit can link to many parent units via unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] A unit can link to many child units via unit hierarchy node relationships. |
| False | [Palantir Defense Ontology] A unit can have one unit type. |
| False | [Palantir Defense Ontology] The operations owned by this unit. |
| False | [Palantir Defense Ontology] A unit can create/own many FSCMs |
| False | [Palantir Defense Ontology] A unit may be responsible for the deconfliction of many FSCMs. |
| False | [Palantir Defense Ontology] A unit may be exempt from many FSCM restrictions. |
| False | [Palantir Defense Ontology] The target engagement authorities owned by this unit. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit type can link to many units. |
| False | [Palantir Defense Ontology] The unit owning this operation. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship links to one child unit. |
| False | [Palantir Defense Ontology] A unit hierarchy node relationship links to one parent unit. |
| False | [Palantir Defense Ontology] An FSCM must contain a link to the unit that created/owns this FSCM |
| False | [Palantir Defense Ontology] An FSCM must contain a link to the unit responsible for the deconfliction of this FSCM |
| False | [Palantir Defense Ontology] An FSCM may contain many links to units exempt from their restrictions. |
| True | [Palantir Defense Ontology] The unit that owns and has authority over this target engagement authority. |

## Code Snippets

### Load Unit metadata

```javascript
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.unit);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all Unit

```javascript
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.unit>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.unit).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unit>>> = await client(com.palantir.ontology.defense-types.unit)
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
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.unit.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.unit).subscribe(         {
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
        { properties: [ "unitIdentifier", "militaryService", "echelon", "sidc", "affiliation", "allegiance", ]}
    );

subscription.unsubscribe();
```

### Load ordered Unit

```javascript
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.unit>>> = await client(com.palantir.ontology.defense-types.unit)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Unit

```javascript
import { com.palantir.ontology.defense-types.unit } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.unit>>>
    = await client(com.palantir.ontology.defense-types.unit).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.unit>>
    = await client(com.palantir.ontology.defense-types.unit).fetchPage({ $pageSize: 30 });
```
