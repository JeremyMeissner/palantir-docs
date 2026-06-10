---
source_url: "https://www.palantir.com/docs/foundry/api/notepad-v2-resources/generation-jobs/save-document-generation-job/"
title: "Save Document Generation Job \u2022 API Reference"
---
# Save Document Generation Job

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Save generated content as a new notepad document. This is only possible if the GenerationJob succeeded.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:notepad-write`.

**operationId:** v2.saveDocumentGenerationJob

**path:** /api/v2/notepad/templates/{templateRid}/generationJobs/{generationJobRid}/saveDocument

### Operation Type

### Scopes

| name |
| --- |
| api:notepad-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| templateRid | stringType | True | The unique identifier for a Template |
| generationJobRid | stringType | True | The unique identifier for a GenerationJob |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** SaveDocumentGenerationJobRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| documentName | stringType | False | The name of the document to save. If not provided, a name will be generated. |
| parentFolderRid | stringType | True | The parent folder to save the document in. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791"}

### Response

#### Body

Response for saving a document

**name:** SaveDocumentResponse

**example:** {"documentRid":"ri.notepad.main.notepad.ef32c039-353c-4555-9704-eacfdfaa2c1c"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| documentRid | stringType | True | The RID of the newly created document |

**example:** {"documentRid":"ri.notepad.main.notepad.ef32c039-353c-4555-9704-eacfdfaa2c1c"}

### Error Responses

| name | description |
| --- | --- |
| GenerationJobStatusFailed | The operation cannot be completed because the generation job has failed status. |
| GenerationJobStatusRunning | The operation cannot be completed because the generation job has running status. |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| InvalidFolder | The given Resource is not a Folder. |
| SaveDocumentGenerationJobPermissionDenied | Could not saveDocument the GenerationJob. |
| FolderNotFound | The given Folder could not be found. |
