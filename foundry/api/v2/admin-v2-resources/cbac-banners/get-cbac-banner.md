---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/cbac-banners/get-cbac-banner/"
title: "Get Cbac Banner"
---
# Get Cbac Banner

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Returns a classification banner string and colors for the given set of marking IDs. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Query parameters. The display type of the banner. Defaults to PORTION_MARKING. BANNER_LINE is the long classification string used in the header of a document; PORTION_MARKING is a short classification string used for individual paragraphs. Enum values: BANNER_LINE, PORTION_MARKING. The marking IDs for which to generate a banner. Enables the use of preview functionality. Response body. The hex value of a color. Examples. Error responses.
