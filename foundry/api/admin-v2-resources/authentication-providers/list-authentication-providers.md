---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/authentication-providers/list-authentication-providers/"
title: "List Authentication Providers \u2022 API Reference"
---
# List Authentication Providers

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Lists all AuthenticationProviders.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listAuthenticationProviders

**path:** /api/v2/admin/enrollments/{enrollmentRid}/authenticationProviders

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| enrollmentRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ListAuthenticationProvidersResponse

**example:** {"data":[{"supportedHosts":["example.palantirfoundry.com"],"name":"Example SAML Provider","realm":"1bd3813a-ef8b-4211-bfbd-8b6485d0eb83","rid":"ri.control-panel.main.saml.3faf689c-eaa1-4137-851f-81d58afe4c86","enabled":true,"supportedUsernamePatterns":[".*@example.com",".*@palantir.com"]}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"supportedHosts":["example.palantirfoundry.com"],"name":"Example SAML Provider","realm":"1bd3813a-ef8b-4211-bfbd-8b6485d0eb83","rid":"ri.control-panel.main.saml.3faf689c-eaa1-4137-851f-81d58afe4c86","enabled":true,"supportedUsernamePatterns":[".*@example.com",".*@palantir.com"]}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| EnrollmentNotFound | The given Enrollment could not be found. |
