---
source_url: "https://www.palantir.com/docs/foundry/api/third-party-applications-v2-resources/websites/deploy-website/"
title: "Deploy Website \u2022 API Reference"
---
# Deploy Website

## Endpoint

Deploy a version of the Website.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `third-party-application:deploy-application-website`.

**operationId:** v2.deployWebsite

**path:** /api/v2/thirdPartyApplications/{thirdPartyApplicationRid}/website/deploy

### Operation Type

### Scopes

| name |
| --- |
| third-party-application:deploy-application-website |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| thirdPartyApplicationRid | stringType | True | An RID identifying a third-party application created in Developer Console. |

### Request

#### Body

**name:** DeployWebsiteRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| version | stringType | True | The semantic version of the Website. |

**example:** {"version":"1.2.0"}

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
| DeployWebsitePermissionDenied | Could not deploy the Website. |
