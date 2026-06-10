---
source_url: "https://www.palantir.com/docs/foundry/api/v2/notepad-v2-resources/generation-jobs/save-document-generation-job/"
parquet_url: "/foundry/api/v2/notepad-v2-resources/generation-jobs/save-document-generation-job/"
title: "Save Document Generation Job"
fetched_at: "2026-05-12T19:34:37.700Z"
---
Save Document Generation Job. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Save generated content as a new notepad document. This is only possible if the GenerationJob succeeded. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:notepad-write. Path parameters. The unique identifier for a Template. The unique identifier for a GenerationJob. Query parameters. Enables the use of preview functionality. Request body. The name of the document to save. If not provided, a name will be generated. The parent folder to save the document in. Response body. Response for saving a document. The RID of the newly created document. Examples. Error responses.
