---
source_url: "https://www.palantir.com/docs/foundry/api/notepad-v2-resources/templates/generate-template/"
title: "Generate Template \u2022 API Reference"
---
# Generate Template

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new GenerationJob. The template generation job will produce new document content by applying 
template parameters to an existing template. If the GenerationJob succeeds, the resulting contents can
be saved as a new Document or exported to a File.

The user must have the api:notepad-write scope to create GenerationJobs. Once created a GenerationJob
is only accessible to the user that created it.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:notepad-write`.

**operationId:** v2.generateTemplate

**path:** /api/v2/notepad/templates/{templateRid}/generate

### Operation Type

### Scopes

| name |
| --- |
| api:notepad-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| templateRid | stringType | True | The unique identifier for a Template |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** GenerateTemplateRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| templateVersion | stringType | False | The published version of the template to use. If not provided, the latest published version will be used. |
| templateParameters | mapType | False | The parameters to apply to the template during generation. |

**example:** {"templateParameters":{"customerName":{"type":"string","value":"John Doe"}},"templateVersion":42}

### Response

#### Body

The unique identifier for a GenerationJob

**name:** GenerationJobRid

##### Format

**example:** ri.notepad.main.generation-job.ab12c039-353c-4555-9704-eacfdfaa2c1c

**example:** ri.notepad.main.generation-job.ab12c039-353c-4555-9704-eacfdfaa2c1c

### Error Responses

| name | description |
| --- | --- |
| TemplateNotFound | The requested template was not found. |
| InvalidTimezone | The provided timezone is not valid. |
| InvalidGenerationJobTemplateVersion | The provided template version doesn't exist or the template has no published versions. |
| MissingGenerationJobTemplateParameters | One or more template parameters are missing. |
| InvalidGenerationJobTemplateParameter | A template parameter value is invalid (for example, is of the wrong type). |
| GenerateTemplatePermissionDenied | Could not generate the Template. |
