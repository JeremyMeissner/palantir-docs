---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/user-provider-infos/replace-user-provider-info/"
title: "Replace User Provider Info"
---
# Replace User Provider Info

Replace the UserProviderInfo. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. A Foundry User ID. Request body. The ID of the User in the external authentication provider. This value is determined by the authentication provider. At most one User can have a given provider ID in a given Realm. Response body. The replaced UserProviderInfo. The ID of the User in the external authentication provider. This value is determined by the authentication provider. At most one User can have a given provider ID in a given Realm. Examples. Error responses.
