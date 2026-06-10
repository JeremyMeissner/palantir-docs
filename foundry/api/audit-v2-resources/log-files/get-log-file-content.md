---
source_url: "https://www.palantir.com/docs/foundry/api/audit-v2-resources/log-files/get-log-file-content/"
title: "Get Log File Content \u2022 API Reference"
---
# Get Log File Content

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:audit-read`.

**operationId:** v2.getLogFileContent

**path:** /api/v2/audit/organizations/{organizationRid}/logFiles/{logFileId}/content

### Operation Type

### Scopes

| name |
| --- |
| api:audit-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |
| logFileId | stringType | True | The ID of an audit log file |

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| GetLogFileContentPermissionDenied | Could not content the LogFile. |
