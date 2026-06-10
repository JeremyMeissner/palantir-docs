---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/cbac-marking-restrictions-objects/get-cbac-marking-restrictions/"
title: "Get Cbac Marking Restrictions \u2022 API Reference"
---
# Get Cbac Marking Restrictions

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns disallowed, implied, and required markings for the given set of marking IDs.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getCbacMarkingRestrictions

**path:** /api/v2/admin/cbacMarkingRestrictions

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingIds | listType | False | The marking IDs for which to get restrictions. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** CbacMarkingRestrictions

**example:** {"disallowedMarkings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"requiredMarkings":[["18212f9a-0e63-4b79-96a0-aae04df23336"]],"userSatisfiesMarkings":true,"isValid":true,"impliedMarkings":["18212f9a-0e63-4b79-96a0-aae04df23336"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| disallowedMarkings | listType | False | Markings that cannot appear in conjunction with the provided markings. This includes all such markings, not just those present in the provided set. |
| impliedMarkings | listType | False | Markings that are automatically granted when a user has membership in any of the provided markings. |
| requiredMarkings | listType | False | Markings that must appear in conjunction with the provided markings. Each list contains the requirements for one of the provided markings, and at least one marking from each must be included in the provided markingIds to constitute a valid classification. |
| userSatisfiesMarkings | booleanType | True | True if the current user satisfies the provided markings. The user must be a member of all conjunctive markings. The provided disjunctive markings are grouped by category, and the user must be a member of at least one marking in each group. |
| isValid | booleanType | True | True if the provided markings constitute a valid classification, containing no disallowed markings and satisfying all required marking constraints. |

**example:** {"disallowedMarkings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"requiredMarkings":[["18212f9a-0e63-4b79-96a0-aae04df23336"]],"userSatisfiesMarkings":true,"isValid":true,"impliedMarkings":["18212f9a-0e63-4b79-96a0-aae04df23336"]}

### Error Responses

| name | description |
| --- | --- |
| GetCbacMarkingRestrictionInfoPermissionDenied | The provided token does not have permission to get the CBAC marking restrictions for the markings. |
| CbacUnavailable | CBAC is not available. |
| CbacMarkingRestrictionsNotFound | The given CbacMarkingRestrictions could not be found. |
