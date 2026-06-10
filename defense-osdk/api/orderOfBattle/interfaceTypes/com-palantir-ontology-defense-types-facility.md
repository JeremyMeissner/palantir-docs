---
source_url: "https://www.palantir.com/docs/defense-osdk/api/orderOfBattle/interfaceTypes/com-palantir-ontology-defense-types-facility/"
title: "Facility \u2022 API Reference"
---
# Facility

Palantir Defense OSDK

[Palantir Defense Ontology] Defines the shape of static military structures inclusive of all affiliations.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| BE Number | stringType |  | False | [Palantir Defense Ontology] Basic Encyclopedia Numbers are used to track individual military installations. They are alphanumeric, unique, unclassified, and can be shared over open telephone and computer networks when not associated with specific information about a given installation. |
| O-Suffix | stringType |  | False | [Palantir Defense Ontology] A machine-generated alphanumeric identifier used to distinguish facilities within the same military installation. |
| Location | geohashType |  | True | [Palantir Defense Ontology] The simple location of the facility |
| HAE Elevation (meters) | doubleType |  | False | [Palantir Defense Ontology] The facility HAE elevation in meters |
| HAE Linear Error (meters) | doubleType |  | False | [Palantir Defense Ontology] The facility HAE error in meters |
| MSL Elevation (meters) | doubleType |  | False | [Palantir Defense Ontology] The facility MSL elevation in meters |
| MSL Linear Error (meters) | doubleType |  | False | [Palantir Defense Ontology] The facility MSL error in meters |
| Affliation | stringType | MIL2525 Affiliation | True | [Palantir Defense Ontology] Defines the affliation of a facility such as HOSTILE or FRIENDLY. |
| Allegiance | stringType |  | True | [Palantir Defense Ontology] Defines the country of allegiance of a facility. |
| Operational Status | stringType |  | True | [Palantir Defense Ontology] Defines the operating status of an enemy or friendly facility. |
| Function | stringType |  | False | [Palantir Defense Ontology] Describes the function of the facility |
| SIDC | stringType |  | False | [Palantir Defense Ontology] A Symbol Identification Code is an alphanumeric identifier that uniquely identifies and displays a military symbol. Its format depends on the standard used, such as MIL-STD 2525C or MIL-STD 2525D. |

## Ontology Entity Type Content

### Interface Type

## Code Snippets

### Load Facility metadata

```javascript
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.facility);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load ordered Facility

```javascript
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.facility>>> = await client(com.palantir.ontology.defense-types.facility)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of Facility

```javascript
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.facility>>>
    = await client(com.palantir.ontology.defense-types.facility).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.facility>>
    = await client(com.palantir.ontology.defense-types.facility).fetchPage({ $pageSize: 30 });
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.facility>>> = await client(com.palantir.ontology.defense-types.facility)
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
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.facility.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.facility).subscribe(         {
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
        { properties: [ "beNumber", "oSuffix", "location", "haeElevation", "haeLinearError", "mslElevation", "mslLinearError", "affiliation", "allegiance", "operationalStatus", "function", "sidc", ]}
    );

subscription.unsubscribe();
```

### Load all Facility

```javascript
import { com.palantir.ontology.defense-types.facility } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.facility>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.facility).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
