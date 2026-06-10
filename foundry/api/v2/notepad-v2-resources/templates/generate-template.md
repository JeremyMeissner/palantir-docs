---
source_url: "https://www.palantir.com/docs/foundry/api/v2/notepad-v2-resources/templates/generate-template/"
title: "Generate Template"
---
# Generate Template

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Creates a new GenerationJob. The template generation job will produce new document content by applying template parameters to an existing template. If the GenerationJob succeeds, the resulting contents can be saved as a new Document or exported to a File. The user must have the api scope to create GenerationJobs. Once created a GenerationJob is only accessible to the user that created it. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:notepad-write. Path parameters. The unique identifier for a Template. Query parameters. Enables the use of preview functionality. Request body. The published version of the template to use. If not provided, the latest published version will be used. The parameters to apply to the template during generation. Response body. The unique identifier for a GenerationJob. Examples. Error responses.
