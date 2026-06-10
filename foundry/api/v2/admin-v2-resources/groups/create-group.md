---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/groups/create-group/"
parquet_url: "/foundry/api/v2/admin-v2-resources/groups/create-group/"
title: "Create Group"
fetched_at: "2026-05-12T19:34:37.734Z"
---
Create Group. Creates a new Group. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Request body. The name of the Group. The RIDs of the Organizations whose members can see this group. At least one Organization RID must be listed. A description of the Group. A map of the Group's attributes. Attributes prefixed with "multipass:" are reserved for internal use by Foundry and are subject to change. Response body. The created Group. A Foundry Group ID. The name of the Group. A description of the Group. Identifies which Realm a User or Group is a member of. The palantir-internal-realm is used for Users or Groups that are created in Foundry by administrators and not associated with any SSO provider. The RIDs of the Organizations whose members can see this group. At least one Organization RID must be listed. A map of the Group's attributes. Attributes prefixed with "multipass:" are reserved for internal use by Foundry and are subject to change. Examples. Error responses.
