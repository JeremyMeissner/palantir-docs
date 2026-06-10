---
source_url: "https://www.palantir.com/docs/defense-osdk/api/common/interfaceTypes/com-palantir-ontology-defense-types-mil2525CSymbol/"
title: "MILSTD 2525C Symbol \u2022 API Reference"
---
# MILSTD 2525C Symbol

Palantir Defense OSDK

[Palantir Defense Ontology] Tactical Symbols and Tactical Graphics as described by MIL-STD 2525C. Tactical Symbols consist of point objects that present information that can be pinpointed in one location at a particular point in time. Tactical Graphics consist of point, line, and area objects that are necessary for battlefield planning and management.

## Properties

| name | type | valueType | required | description |
| --- | --- | --- | --- | --- |
| SIDC | stringType |  | True | [Palantir Defense Ontology] A Symbol Identification Code is an alphanumeric identifier that uniquely identifies and displays a military symbol. Its format depends on the standard used, such as MIL-STD 2525C or MIL-STD 2525D. |
| Symbol Anchor Points | listType |  | True | [Palantir Defense Ontology] The list of points that define the placement and/or shape of the symbol. A single-point graphic will be represented by a list containing one geopoint. |
| Quantity Modifier (C) | integerType |  | False | [Palantir Defense Ontology] A text modifier that identifies the number of items present. |
| Reinforced or Reduced Modifier (F) | stringType | MIL2525 Reinforced or Reduced | False | [Palantir Defense Ontology] A text modifier in a unit symbol that displays (+) for reinforced, (-) for reduced, (+/-) reinforced and reduced. R = reinforced, D = reduced, RD = reinforced and reduced. |
| Staff Comments Modifier (G) | stringType |  | False | [Palantir Defense Ontology] A text modifier for units, equipment, and installations; content is implementation-specific. |
| Additional Information Modifier 1 (H) | stringType |  | False | [Palantir Defense Ontology] A text modifier for tactical graphics, units, equipment, and installations; content is implementation-specific. |
| Additional Information Modifier 2 (H1) | stringType |  | False | [Palantir Defense Ontology] A text modifier for tactical graphics, units, equipment, and installations; content is implementation-specific. |
| Additional Information Modifier 3 (H2) | stringType |  | False | [Palantir Defense Ontology] A text modifier for tactical graphics, units, equipment, and installations; content is implementation-specific. |
| Evaluation Rating Modifier (J) | stringType | MIL2525 Evaluation Rating | False | [Palantir Defense Ontology] A text modifier for units, equipment, and installations that consists of a one-letter reliability rating and a one-number credibility rating. Reliability Ratings: A-completely reliable, B-usually reliable, C-fairly reliable, D-not usually reliable, E-unreliable, F-reliability cannot be judged. Credibility Ratings: 1-confirmed by other sources, 2-probably true, 3-possibly true, 4-doubtfully true, 5-improbable, 6-truth cannot be judged. |
| Combat Effectiveness Modifier (K) | stringType |  | False | [Palantir Defense Ontology] A text modifier for units and installations that indicates unit effectiveness or installation capability. |
| Signature Equipment Modifier (L) | stringType | MIL2525 Signature Equipment | False | [Palantir Defense Ontology] A text modifier for hostile equipment; "!" indicates detectable electronic signatures. |
| Higher Formation Modifier (M) | stringType |  | False | [Palantir Defense Ontology] A text modifier for units that indicates number or title of higher echelon command. Corps are designated by Roman numerals. |
| IFF/SIF Modifier (P) | stringType |  | False | [Palantir Defense Ontology] A text modifier displaying IFF/SIF Identification modes and codes. |
| Direction of Movement Indicator Modifier (Q) | doubleType |  | False | [Palantir Defense Ontology] A graphic modifier for units, equipment, and CBRNE events that identifies the direction of movement or intended movement of an object. This property type expects degrees. |
| SIGINT Mobility Indicator Modifier (R2) | stringType | MIL2525 SIGINT Mobility Indicator | False | [Palantir Defense Ontology] M = Mobile, S = Static, or U = Uncertain. |
| Unique Designation Modifier 1 (T) | stringType |  | False | [Palantir Defense Ontology] A text modifier that uniquely identifies a particular tactical graphic, unit, equipment, or installation; track number. |
| Unique Designation Modifier 2 (T1) | stringType |  | False | [Palantir Defense Ontology] A text modifier that uniquely identifies a particular tactical graphic, unit, equipment, or installation; track number. |
| Type Modifier (V) | stringType |  | False | [Palantir Defense Ontology] A text modifier that indicates nuclear weapon type or type of equipment. |
| Date-Time Group Modifier 1/Effective Time (W) | timestampType |  | False | [Palantir Defense Ontology] Date-Time Group (DTG) indicating the effective time (often the 'start' time) of the graphic. |
| Date-Time Group Modifier 2/Expiration Time (W1) | timestampType |  | False | [Palantir Defense Ontology] Date-Time Group (DTG) indicating the expiration time (often the 'end' time) of the graphic. |
| Altitude/Depth Modifier (X) | listType |  | False | [Palantir Defense Ontology] A text modifier that displays the minimum, maximum, and/or specific altitude (in feet or meters in relation to a reference datum), flight level, or depth (for submerged objects in feet below sea level). Examples of valid values are 'GL' for Ground Level, 'MSL' for Mean Sea Level, '1250 FT AGL', '1000 FT AMSL', '1524 M HAE', '35760 FT BMSL', 'FL 250'. An example of multiple values is 'FL 250; FL 950' |
| Location Modifier (Y) | geohashType |  | False | [Palantir Defense Ontology] A text modifier that displays a graphic's location in degrees, minutes, and seconds (or in UTM or other applicable display format). Primarily used for offset locations, not to be confused with Anchor Points which actually holds the full specification of the graphic. |
| Speed Modifier (Z) | structType |  | False | [Palantir Defense Ontology] A text modifier for units and equipment that displays velocity as set forth in MIL-STD-6040. Struct includes a numeric field (double) and a unit of measurement field. |
| Special C2 Headquarters Modifier (AA) | stringType |  | False | [Palantir Defense Ontology] A text modifier for units; indicator is contained inside the frame; contains the name of the special C2 Headquarters. |
| Platform Type Modifier (AD) | stringType |  | False | [Palantir Defense Ontology] ELNOT or CENOT |
| Equipment Teardown Time Modifier (AE) | doubleType |  | False | [Palantir Defense Ontology] Captures equipment teardown time in minutes. |
| Common Identifier Modifier (AF) | stringType |  | False | [Palantir Defense Ontology] Example: 'Hawk' for Hawk SAM system. |
| Distance Modifier (AM) | listType |  | False | [Palantir Defense Ontology] A numeric modifier that displays a minimum, maximum, or a specific distance (range, radius, width, length, etc.). All distances are in meters. |
| Azimuth Modifier (AN) | listType |  | False | [Palantir Defense Ontology] A numeric amplifier that displays an angle measured from true north to any other line in degrees. |
| Engagement Bar Modifier (AO) | stringType |  | False | [Palantir Defense Ontology] A graphic amplifier placed immediately atop the symbol. May denote: 1) local/remote status; 2) engagement status; or 3) weapon type. |

## Ontology Entity Type Content

### Interface Type

## Code Snippets

### Filtering

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.mil2525CSymbol>>> = await client(com.palantir.ontology.defense-types.mil2525CSymbol)
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

### Load ordered MILSTD 2525C Symbol

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { isOk, type Osdk, type PageResult, type Result } from "@osdk/client";

const page: Result<PageResult<Osdk<com.palantir.ontology.defense-types.mil2525CSymbol>>> = await client(com.palantir.ontology.defense-types.mil2525CSymbol)
    .fetchPageWithErrors({
        $orderBy: {"someProperty": "asc"},
        $pageSize: 30
    });

if (isOk(page)) {
    const interfaces = page.value.data;
    const interface1 = interfaces[0];
}
```

### Load pages of MILSTD 2525C Symbol

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import { type Osdk, type PageResult, type Result } from "@osdk/client";

const response:  Result<PageResult<Osdk<com.palantir.ontology.defense-types.mil2525CSymbol>>>
    = await client(com.palantir.ontology.defense-types.mil2525CSymbol).fetchPageWithErrors({ $pageSize: 30 });

// To fetch a page without a result wrapper, use fetchPage instead
const responseNoErrorWrapper: PageResult<Osdk<com.palantir.ontology.defense-types.mil2525CSymbol>>
    = await client(com.palantir.ontology.defense-types.mil2525CSymbol).fetchPage({ $pageSize: 30 });
```

### Subscribe to object sets

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

// A map of primary keys to objects loaded through the SDK
const objects: { [key: string]: com.palantir.ontology.defense-types.mil2525CSymbol.OsdkInstance } = ...

const subscription = client(com.palantir.ontology.defense-types.mil2525CSymbol).subscribe(         {
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
        { properties: [ "sidc", "symbolAnchorPoints", "quantity", "reinforcedOrReduced", "staffComments", "additionalInformation1", "additionalInformation2", "additionalInformation3", "evaluationRating", "combatEffectiveness", "signatureEquipment", "higherFormation", "iffSif", "directionOfMovementIndicator", "sigintMobilityIndicator", "uniqueDesignation1", "uniqueDesignation2", "type", "dateTimeGroup1", "dateTimeGroup2", "altitudeDepth", "location", "speed", "specialC2Headquarters", "platformType", "equipmentTeardownTime", "commonIdentifier", "distance", "azimuth", "engagementBar", ]}
    );

subscription.unsubscribe();
```

### Load MILSTD 2525C Symbol metadata

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";

const interfaceTypeMetadata = await client.fetchMetadata(com.palantir.ontology.defense-types.mil2525CSymbol);

const implementingObjectTypes = interfaceTypeMetadata.implementedBy;
const interfaceRid = interfaceTypeMetadata.rid;
```

### Load all MILSTD 2525C Symbol

```javascript
import { com.palantir.ontology.defense-types.mil2525CSymbol } from "@defense-ontology/sdk";
// Edit this import if your client location differs
import { client } from "./client";
import type { Osdk } from "@osdk/client";

const interfaces: Osdk<com.palantir.ontology.defense-types.mil2525CSymbol>[] = [];

for await(const int of client(com.palantir.ontology.defense-types.mil2525CSymbol).asyncIter()) {
    interfaces.push(int);
}
const interface1 = interfaces[0];
```
