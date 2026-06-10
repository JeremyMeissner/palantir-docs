---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/group-membership-expiration-policies/replace-group-membership-expiration-policy/"
title: "Replace Group Membership Expiration Policy"
---
# Replace Group Membership Expiration Policy

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Replace the GroupMembershipExpirationPolicy. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. A Foundry Group ID. Query parameters. Enables the use of preview functionality. Request body. Members in this group must be added with expirations that are less than this duration in seconds into the future from the time they are added. Members in this group must be added with expiration times that occur before this value. Response body. The replaced GroupMembershipExpirationPolicy. Members in this group must be added with expiration times that occur before this value. Members in this group must be added with expirations that are less than this duration in seconds into the future from the time they are added. Examples. Error responses.
