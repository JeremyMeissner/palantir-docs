---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/organizations/create-organization/"
parquet_url: "/foundry/api/v2/admin-v2-resources/organizations/create-organization/"
title: "Create Organization"
fetched_at: "2026-05-12T19:34:37.717Z"
---
Create Organization. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Creates a new Organization. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Query parameters. Enables the use of preview functionality. Request body. The initial administrators of the Organization. At least one principal must be provided. The RID of the Enrollment that this Organization belongs to. This must be provided. The primary host name of the Organization. This should be used when constructing URLs for users of this Organization. Response body. The created Organization. The ID of this Organization's underlying marking. Organization guest access can be managed by updating the membership of this Marking. The primary host name of the Organization. This should be used when constructing URLs for users of this Organization. Examples. Error responses.
