---
source_url: "https://www.palantir.com/docs/defense-osdk/api/targetingFires/interfaceTypes/com-palantir-ontology-defense-types-fireSupportCoordinationMeasure/"
title: "Fire Support Coordination Measure \u2022 API Reference"
---
# Fire Support Coordination Measure

Palantir Defense OSDK

[Palantir Defense Ontology] Represents the entity of a Fire Support Coordination Measure.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| Valid From | timestampType |  | False | [Palantir Defense Ontology] Start date of the FSCM being valid |
| Valid To | timestampType |  | False | [Palantir Defense Ontology] End date of the FSCM being valid |
| Active | booleanType |  | True | [Palantir Defense Ontology] Represents the FSCM being active |
| Description | stringType |  | False | [Palantir Defense Ontology] Description of the FSCM |
| Type | stringType | FSCM Type | True | [Palantir Defense Ontology] Type of FSCM |
| Shape | stringType | FSCM Shape | True | [Palantir Defense Ontology] Shape of the FSCM. This, along with anchor points and distance, define the correct geometry. |
| Identity | stringType | FSCM Identity | True | [Palantir Defense Ontology] Standard identity/exercise amplifying descriptor for FSCMs. |
| Floor Altitude (meters) | doubleType |  | False | [Palantir Defense Ontology] Lower bound of Killbox or Airspace Control Area as Height Above Ellipsoid (HAE) in meters |
| Ceiling Altitude (meters) | doubleType |  | False | [Palantir Defense Ontology] Upper bound of Killbox or Airspace Control Area as Height Above Ellipsoid (HAE) in meters |
| Anchor Points | listType |  | True | [Palantir Defense Ontology] The list of points that define the placement and/or shape of the FSCM. This property, with the FSCM Distance Modifier (AM) property, should defined the area that FSCMs are rendered on a map. A single-point graphic will be represented by a list containing one geopoint. To render this FSCM as a tactical graphic on maps, fulfill this property with the MIL2525 Symbol Anchor Points shared property type. |
| Unique Designation Modifier 1 (T) | stringType |  | True | [Palantir Defense Ontology] A text modifier that uniquely identifies a particular FSCM. To render this FSCM as a tactical graphic on maps, fulfill this property with the MIL2525 Unique Designation Modifier 1 (T) shared property type. |
| Distance Modifier (AM) | listType |  | True | [Palantir Defense Ontology] A numeric modifier that displays a minimum, maximum, or a specific distance (range, radius, width, length, etc.) related to the FSCM Anchor Points. All distances are in meters. This property, with the FSCM Anchor Points property, should defined the area that FSCMs are rendered on a map. To render this FSCM as a tactical graphic on maps, fulfill this property with the MIL2525 Distance Modifier (AM) shared property type. |
| Intersection Geometry | geoshapeType |  | True | [Palantir Defense Ontology] The boundaries of the FSCM defined by a geoshape. This property should be used to define the area at which the target and its firing location will intersect with the FSCM. |

## Ontology Entity Type Content

### Interface Type

#### Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] An FSCM must contain a link to the unit that created/owns this FSCM |
| False | [Palantir Defense Ontology] An FSCM must contain a link to the unit responsible for the deconfliction of this FSCM |
| False | [Palantir Defense Ontology] An FSCM may contain many links to units exempt from their restrictions. |

#### Incoming Link Constraints

| required | description |
| --- | --- |
| False | [Palantir Defense Ontology] A unit can create/own many FSCMs |
| False | [Palantir Defense Ontology] A unit may be responsible for the deconfliction of many FSCMs. |
| False | [Palantir Defense Ontology] A unit may be exempt from many FSCM restrictions. |

## Code Snippets

### Load all Fire Support Coordination Measure

```javascript
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.fireSupportCoordinationMeasure>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```

### Load Fire Support Coordination Measure metadata

```javascript
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Filtering

```javascript
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.fireSupportCoordinationMeasure>>> = await client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure)
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

### Load ordered Fire Support Coordination Measure

```javascript
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.fireSupportCoordinationMeasure>>> = await client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure)
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
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.fireSupportCoordinationMeasure.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure).subscribe(         {
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
        { properties: [ "validFrom", "validTo", "active", "description", "type", "shape", "identity", "floorAltitude", "ceilingAltitude", "anchorPoints", "uniqueDesignation", "distance", "intersectionGeometry", ]}
    );

subscription.unsubscribe();
```

### Load pages of Fire Support Coordination Measure

```javascript
import { com.palantir.ontology.defense-types.fireSupportCoordinationMeasure } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.fireSupportCoordinationMeasure>>>
    = await client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.fireSupportCoordinationMeasure>>
    = await client(com.palantir.ontology.defense-types.fireSupportCoordinationMeasure).fetchPage({ $pageSize: 30 });
```
