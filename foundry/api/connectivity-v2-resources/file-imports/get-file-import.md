---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/file-imports/get-file-import/"
title: "Get File Import \u2022 API Reference"
---
# Get File Import

## Endpoint

Get the FileImport with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-file-import-read`.

**operationId:** v2.getFileImport

**path:** /api/v2/connectivity/connections/{connectionRid}/fileImports/{fileImportRid}

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-file-import-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| fileImportRid | stringType | True | The Resource Identifier (RID) of a FileImport (also known as a batch sync). |

### Response

#### Body

**name:** FileImport

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My file import","connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","subfolder":"subfolder1/subfolder2","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","fileImportFilters":[{"type":"pathMatchesFilter","regex":"my-subfolder"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a FileImport (also known as a batch sync). |
| connectionRid | stringType | True | The RID of the Connection (also known as a source) that the File Import uses to import data. |
| datasetRid | stringType | True | The RID of the output dataset. Can not be modified after the file import is created. |
| branchName | stringType | False | The branch name in the output dataset that will contain the imported data. Defaults to `master` for most enrollments. Can not be modified after the file import is created. |
| displayName | stringType | True |  |
| fileImportFilters | listType | False | Use filters to limit which files should be imported. Filters are applied in the order they are defined. A different ordering of filters may lead to a more optimized import. [Learn more about optimizing file imports.](/docs/foundry/data-connection/file-based-syncs/#optimize-file-based-syncs) |
| importMode | enumType | True | Import mode governs how raw files are read from an external system, and written into a Foundry dataset.   SNAPSHOT: Defines a new dataset state consisting only of files from a particular import execution. APPEND: Purely additive and yields data from previous import executions in addition to newly added files. UPDATE: Replaces existing files from previous import executions based on file names. |
| subfolder | stringType | False | A subfolder in the external system that will be imported. If not specified, defaults to the root folder of the external system. |

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My file import","connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","subfolder":"subfolder1/subfolder2","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","fileImportFilters":[{"type":"pathMatchesFilter","regex":"my-subfolder"}]}

### Error Responses

| name | description |
| --- | --- |
| FileImportNotFound | The given FileImport could not be found. |
