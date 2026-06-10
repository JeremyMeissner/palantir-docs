---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/builds/create-build/"
title: "Create Build \u2022 API Reference"
---
# Create Build

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.createBuild

**path:** /api/v2/orchestration/builds/create

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-write |

### Request

#### Body

**name:** CreateBuildRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| target | unionType | True | The targets of the schedule. |
| branchName | stringType | False | The target branch the build should run on. |
| fallbackBranches | listType | False | The branches to retrieve JobSpecs from if no JobSpec is found on the target branch. |
| forceBuild | booleanType | False | Whether to ignore staleness information when running the build. |
| retryCount | integerType | False | The number of retry attempts for failed jobs. |
| retryBackoffDuration | objectType | False | The duration to wait before retrying after a Job fails. |
| abortOnFailure | booleanType | False | If any job in the build is unsuccessful, immediately finish the build by cancelling all other jobs. |
| notificationsEnabled | booleanType | False | Whether to receive a notification at the end of the build. The notification will be sent to the user that has most recently edited the schedule. No notification will be sent if the schedule has `scopeMode` set to `ProjectScope`. |

**example:** {"abortOnFailure":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","target":{"type":"manual","targetRids":["ri.foundry.main.dataset.4263bdd9-d6bc-4244-9cca-893c1a2aef62","ri.foundry.main.dataset.86939c1e-4256-41db-9fe7-e7ee9e0f752a"]}}

### Response

#### Body

**name:** Build

**example:** {"abortOnFailure":false,"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","branchName":"master","createdTime":"2003-05-06T12:34:56.789Z","jobRids":["ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"],"finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","status":"RUNNING"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of a Build. |
| branchName | stringType | True | The branch that the build is running on. |
| createdTime | stringType | True | The timestamp that the build was created. |
| createdBy | stringType | True | The user who created the build. |
| fallbackBranches | listType | False | The branches to retrieve JobSpecs from if no JobSpec is found on the target branch. |
| jobRids | listType | False |  |
| retryCount | integerType | True | The number of retry attempts for failed Jobs within the Build. A Job's failure is not considered final until all retries have been attempted or an error occurs indicating that retries cannot be performed. Be aware, not all types of failures can be retried. |
| retryBackoffDuration | objectType | True | The duration to wait before retrying after a Job fails. |
| abortOnFailure | booleanType | True | If any job in the build is unsuccessful, immediately finish the build by cancelling all other jobs. |
| status | enumType | True | The status of the build. |
| finishedTime | stringType | False | The time the build finished processing. Will be empty while the build is still running. |
| scheduleRid | stringType | False | Schedule RID of the Schedule that triggered this build. If a user triggered the build, Schedule RID will be empty. |

**example:** {"abortOnFailure":false,"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","branchName":"master","createdTime":"2003-05-06T12:34:56.789Z","jobRids":["ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"],"finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","status":"RUNNING"}

### Error Responses

| name | description |
| --- | --- |
| CreateBuildPermissionDenied | Could not create the Build. |
