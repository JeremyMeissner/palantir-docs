---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/transform-media-item/"
title: "Transform Media Item"
---
# Transform Media Item

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Initiates a transformation on a media item. Returns a job ID that can be used to check the status and retrieve the result of the transformation. Transforming a media item requires that you are able to read the media item, either via api:mediasets-read or via a MediaItemReadToken. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-transform. Path parameters. The RID of the media set. The RID of the media item. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Request body. Request to transform a media item. A transformation to apply to a media item. Each variant specifies the type of transformation and any parameters required for the operation. Response body. The transformation was initiated successfully. The status of a transformation job. Enum values: PENDING, FAILED, SUCCESSFUL. An identifier for a media item transformation job. Examples.
