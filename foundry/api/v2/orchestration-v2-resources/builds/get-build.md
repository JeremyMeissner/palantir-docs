---
source_url: "https://www.palantir.com/docs/foundry/api/v2/orchestration-v2-resources/builds/get-build/"
title: "Get Build"
---
# Get Build

Get the Build with the specified rid. Users are allowed to make a maximum of 4 requests per second and 25 concurrent requests. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:orchestration-read. Path parameters. The RID of a Build. Response body. The RID of a Build. The branch that the build is running on. The timestamp that the build was created. The user who created the build. The branches to retrieve JobSpecs from if no JobSpec is found on the target branch. The number of retry attempts for failed Jobs within the Build. A Job's failure is not considered final until all retries have been attempted or an error occurs indicating that retries cannot be performed. Be aware, not all types of failures can be retried. The duration to wait before retrying after a Job fails. If any job in the build is unsuccessful, immediately finish the build by cancelling all other jobs. The status of the build. Enum values: RUNNING, SUCCEEDED, FAILED, CANCELED. The time the build finished processing. Will be empty while the build is still running. Schedule RID of the Schedule that triggered this build. If a user triggered the build, Schedule RID will be empty. Examples. Error responses.
