---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observations/write-observations/"
title: "Write observations \u2022 API Reference"
---
# Write observations

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Writes Observations directly to Geotime. Returns the Observations that could not be written to Geotime with the
reason for why they could not be written. Any Observations not in the response are guaranteed to have been
written successfully to Geotime's backing data store.

**operationId:** v1.writeObservations

**path:** /api/gotham/v1/observations

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The list of Observations to write to Geotime.

**name:** WriteObservationsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| Observation | objectType | True | A geotemporal object along a Geotime Track (SSID, CID, SpecID, TrackID quadruplet). |

**example:** [{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":-122.16219,"latitude":37.44274},"timestamp":"2023-01-01T22:00:00Z","name":"name0","staticProperties":[],"liveProperties":[]},{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track1","position":{"longitude":-122.16165,"latitude":37.44215},"timestamp":"fakeInvalidTimestamp","name":"name1","staticProperties":[],"liveProperties":[]}]

### Response

#### Body

Response with information about any Observations that failed to be written.

**name:** WriteObservationsResponse

**example:** [{"observation":{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track1","position":{"longitude":-122.16165,"latitude":37.44215},"timestamp":"fakeInvalidTimestamp","name":"name1","staticProperties":[],"liveProperties":[],"style":{}},"reason":"Invalid timestamp."}]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| InvalidObservation | objectType | True |  |

**example:** [{"observation":{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track1","position":{"longitude":-122.16165,"latitude":37.44215},"timestamp":"fakeInvalidTimestamp","name":"name1","staticProperties":[],"liveProperties":[],"style":{}},"reason":"Invalid timestamp."}]
