---
source_url: "https://www.palantir.com/docs/foundry/api/v2/orchestration-v2-resources/jobs/get-job/"
parquet_url: "/foundry/api/v2/orchestration-v2-resources/jobs/get-job/"
title: "Get Job"
fetched_at: "2026-05-12T19:34:37.592Z"
---
Get Job. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the Job with the specified rid. Users are allowed to make a maximum of 4 requests per second and 25 concurrent requests. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:orchestration-read. Path parameters. The RID of a Job. Query parameters. Enables the use of preview functionality. Response body. The RID of a Job. The RID of the Build that the Job belongs to. The time this job started waiting for the dependencies to be resolved. The time this job's latest attempt started running. This field may be empty or outdated if the job failed to start. The time this job was finished. The status of the job. Enum values: WAITING, RUNNING, SUCCEEDED, FAILED, CANCELED, DID_NOT_RUN. Outputs of the Job. Only outputs with supported types are listed here; unsupported types are omitted. Currently supported types are Dataset and Media Set outputs. Examples. Error responses.
