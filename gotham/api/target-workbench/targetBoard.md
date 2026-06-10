---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/targetBoard/"
title: "Create a Target Board \u2022 API Reference"
---
# Create a Target Board

## Endpoint

By default, create a TargetBoard with default columns: IDENTIFIED TARGET, PRIORITIZED TARGET, IN COORDINATION, IN EXECUTION, COMPLETE.
Returns the RID of the created TargetBoard.

**operationId:** v1.createTargetBoardV2

**path:** /api/gotham/v1/twb/targetBoard

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to create a Target Board

**name:** CreateTargetBoardRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| highPriorityTargetList | stringType | False |  |
| configuration | objectType | False | Configuration for the target board. If present, must have at least one column |
| security | objectType | True | Security mutation details for a target, target board, or hptl. Specifying security overrides the system's default security when creating and updating data. This model may evolve over time for other security features. |

**example:** {"name":"Example target board name.","description":"Example description.","highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"id12345","name":"DONE","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"security":{"portionMarkings":["SENSITIVE"]}}

### Response

#### Body

Success response with the ID of the created Target Board.

**name:** CreateTargetBoardResponseV2

**example:** ri.gotham-artifact.0-0.target-collection.example

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoardRid | stringType | True | The unique resource identifier of a Target Board. This is equivalent to a collection RID. |

**example:** ri.gotham-artifact.0-0.target-collection.example
