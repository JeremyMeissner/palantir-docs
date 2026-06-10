---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/group-membership-expiration-policies/get-group-membership-expiration-policy/"
parquet_url: "/foundry/api/v2/admin-v2-resources/group-membership-expiration-policies/get-group-membership-expiration-policy/"
title: "Get Group Membership Expiration Policy"
fetched_at: "2026-05-12T19:34:37.724Z"
---
Get Group Membership Expiration Policy. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the GroupMembershipExpirationPolicy. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. A Foundry Group ID. Query parameters. Enables the use of preview functionality. Response body. Members in this group must be added with expiration times that occur before this value. Members in this group must be added with expirations that are less than this duration in seconds into the future from the time they are added. Examples. Error responses.
