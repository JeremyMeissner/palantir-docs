---
source_url: "https://www.palantir.com/docs/foundry/api/third-party-applications-v2-resources/versions/get-version/"
title: "Get Version \u2022 API Reference"
---
# Get Version

## Endpoint

Get the Version with the specified version.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `third-party-application:deploy-application-website`.

**operationId:** v2.getVersion

**path:** /api/v2/thirdPartyApplications/{thirdPartyApplicationRid}/website/versions/{versionVersion}

### Operation Type

### Scopes

| name |
| --- |
| third-party-application:deploy-application-website |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| thirdPartyApplicationRid | stringType | True | An RID identifying a third-party application created in Developer Console. |
| versionVersion | stringType | True | The semantic version of the Website. |

### Response

#### Body

**name:** Version

**example:** {"version":"1.2.0"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| version | stringType | True | The semantic version of the Website. |

**example:** {"version":"1.2.0"}

### Error Responses

| name | description |
| --- | --- |
| VersionNotFound | The given Version could not be found. |
