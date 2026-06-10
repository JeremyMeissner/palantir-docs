---
source_url: "https://www.palantir.com/docs/foundry/api/third-party-applications-v2-resources/websites/get-website/"
title: "Get Website \u2022 API Reference"
---
# Get Website

## Endpoint

Get the Website.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `third-party-application:deploy-application-website`.

**operationId:** v2.getWebsite

**path:** /api/v2/thirdPartyApplications/{thirdPartyApplicationRid}/website

### Operation Type

### Scopes

| name |
| --- |
| third-party-application:deploy-application-website |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| thirdPartyApplicationRid | stringType | True | An RID identifying a third-party application created in Developer Console. |

### Response

#### Body

**name:** Website

**example:** {"subdomains":["myapp.example.com"],"deployedVersion":"1.2.0"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| deployedVersion | stringType | False | The version of the Website that is currently deployed. |
| subdomains | listType | False | The subdomains from which the Website is currently served. |

**example:** {"subdomains":["myapp.example.com"],"deployedVersion":"1.2.0"}

### Error Responses

| name | description |
| --- | --- |
| WebsiteNotFound | The given Website could not be found. |
