---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/authentication-providers/get-authentication-provider/"
title: "Get Authentication Provider \u2022 API Reference"
---
# Get Authentication Provider

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the AuthenticationProvider with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getAuthenticationProvider

**path:** /api/v2/admin/enrollments/{enrollmentRid}/authenticationProviders/{authenticationProviderRid}

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| enrollmentRid | stringType | True |  |
| authenticationProviderRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** AuthenticationProvider

**example:** {"supportedHosts":["example.palantirfoundry.com"],"name":"Example SAML Provider","realm":"1bd3813a-ef8b-4211-bfbd-8b6485d0eb83","rid":"ri.control-panel.main.saml.3faf689c-eaa1-4137-851f-81d58afe4c86","enabled":true,"supportedUsernamePatterns":[".*@example.com",".*@palantir.com"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True |  |
| name | stringType | True |  |
| realm | stringType | True | Identifies which Realm a User or Group is a member of. The `palantir-internal-realm` is used for Users or Groups that are created in Foundry by administrators and not associated with any SSO provider. |
| enabled | booleanType | True | Whether users can log in using this provider. |
| supportedHosts | listType | False | This provider can only be utilized from these hosts. |
| supportedUsernamePatterns | listType | False | Users who enter usernames that match these patterns will be redirected to this authentication provider. |
| protocol | unionType | True |  |

**example:** {"supportedHosts":["example.palantirfoundry.com"],"name":"Example SAML Provider","realm":"1bd3813a-ef8b-4211-bfbd-8b6485d0eb83","rid":"ri.control-panel.main.saml.3faf689c-eaa1-4137-851f-81d58afe4c86","enabled":true,"supportedUsernamePatterns":[".*@example.com",".*@palantir.com"]}

### Error Responses

| name | description |
| --- | --- |
| AuthenticationProviderNotFound | The given AuthenticationProvider could not be found. |
