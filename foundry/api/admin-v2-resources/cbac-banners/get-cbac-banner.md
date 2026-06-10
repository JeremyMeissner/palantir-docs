---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/cbac-banners/get-cbac-banner/"
title: "Get Cbac Banner \u2022 API Reference"
---
# Get Cbac Banner

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns a classification banner string and colors for the given set of marking IDs.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getCbacBanner

**path:** /api/v2/admin/cbacBanner

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| displayType | enumType | False | The display type of the banner. Defaults to PORTION_MARKING. BANNER_LINE is the long classification string used in the header of a document; PORTION_MARKING is a short classification string used for individual paragraphs |
| markingIds | listType | False | The marking IDs for which to generate a banner. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** CbacBanner

**example:** {"markings":["MTS","MNF"],"backgroundColors":["#FFFFFF"],"classificationString":"MTS//MNF","textColor":"#FFFFFF"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| classificationString | stringType | True |  |
| markings | listType | False |  |
| textColor | stringType | True | The hex value of a color. |
| backgroundColors | listType | False |  |

**example:** {"markings":["MTS","MNF"],"backgroundColors":["#FFFFFF"],"classificationString":"MTS//MNF","textColor":"#FFFFFF"}

### Error Responses

| name | description |
| --- | --- |
| GetCbacBannerPermissionDenied | The provided token does not have permission to get the CBAC banner for the markings. |
| CbacUnavailable | CBAC is not available. |
| UnknownClassificationBannerDisplayType | The provided classification banner display type is not recognized. |
| CbacBannerNotFound | The given CbacBanner could not be found. |
