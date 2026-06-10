---
source_url: "https://www.palantir.com/docs/gotham/api/v2/target-workbench-v2-resources/targets/load-target/"
parquet_url: "/gotham/api/v2/target-workbench-v2-resources/targets/load-target/"
title: "Load Target"
fetched_at: "2026-05-12T19:34:35.770Z"
---
Load Target. Load Target by RID. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:target-read. Path parameters. The unique identifier for a Target. Response body. Success response with the requested Target. The objectRid is the RID of the object being targeted. The current version of the Target retrieved. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. Examples. Error responses.
