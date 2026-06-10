---
source_url: "https://www.palantir.com/docs/foundry/api/third-party-applications-v2-resources/versions/upload-version/"
title: "Upload Version \u2022 API Reference"
---
# Upload Version

## Endpoint

Upload a new version of the Website.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `third-party-application:deploy-application-website`.

**operationId:** v2.uploadVersion

**path:** /api/v2/thirdPartyApplications/{thirdPartyApplicationRid}/website/versions/upload

### Operation Type

### Scopes

| name |
| --- |
| third-party-application:deploy-application-website |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| thirdPartyApplicationRid | stringType | True | An RID identifying a third-party application created in Developer Console. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| version | stringType | True | The semantic version of the Website. |

### Request

#### Body

The zip file that contains the contents of your application. For more information, 
refer to the [documentation](/docs/foundry/ontology-sdk/deploy-osdk-application-on-foundry/) user documentation.

**name:** body

##### Format

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
| UploadVersionPermissionDenied | Could not upload the Version. |
