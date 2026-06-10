---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/file-imports/create-file-import/"
title: "Create File Import \u2022 API Reference"
---
# Create File Import

## Endpoint

Creates a new FileImport.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-file-import-write`.

**operationId:** v2.createFileImport

**path:** /api/v2/connectivity/connections/{connectionRid}/fileImports

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-file-import-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Request

#### Body

**name:** CreateFileImportRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The RID of the output dataset. Can not be modified after the file import is created. |
| importMode | enumType | True | Import mode governs how raw files are read from an external system, and written into a Foundry dataset.   SNAPSHOT: Defines a new dataset state consisting only of files from a particular import execution. APPEND: Purely additive and yields data from previous import executions in addition to newly added files. UPDATE: Replaces existing files from previous import executions based on file names. |
| displayName | stringType | True |  |
| branchName | stringType | False | The branch name in the output dataset that will contain the imported data. Defaults to `master` for most enrollments. Can not be modified after the file import is created. |
| subfolder | stringType | False | A subfolder in the external system that will be imported. If not specified, defaults to the root folder of the external system. |
| fileImportFilters | listType | False | Use filters to limit which files should be imported. Filters are applied in the order they are defined. A different ordering of filters may lead to a more optimized import. [Learn more about optimizing file imports.](/docs/foundry/data-connection/file-based-syncs/#optimize-file-based-syncs) |

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My file import","branchName":"master","subfolder":"subfolder1/subfolder2","fileImportFilters":[{"type":"pathMatchesFilter","regex":"my-subfolder"}]}

### Response

#### Body

The created FileImport

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
| ConnectionDetailsNotDetermined | Details of the connection (such as which types of import it supports) could not be determined. |
| FileSizeFilterMissingGreaterThanAndLessThan | Both the `gt` and `lt` properties are missing from the FileSizeFilter. At least one of these properties must be present |
| FileSizeFilterGreaterThanCannotBeNegative | The `gt` property in the FileSizeFilter cannot be a negative number. |
| FileSizeFilterLessThanMustBeOneByteOrLarger | The `lt` property in the FileSizeFilter must be at least 1 byte. |
| FileSizeFilterInvalidGreaterThanAndLessThanRange | The provided `gt` and `lt` properties in the FileSizeFilter are invalid. No files will ever satisfy the provided range. The value specified for `gt` must be strictly less than `lt - 1`. |
| FileAtLeastCountFilterInvalidMinCount | The provided `minFilesCount` property in the FileAtLeastCountFilter must be strictly greater than 0. |
| FileImportCustomFilterCannotBeUsedToCreateOrUpdateFileImports | Custom file import filters can be fetched but cannot currently be used when creating or updating file imports. |
| FileImportNotSupportedForConnection | The specified connection does not support file imports. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| CreateFileImportPermissionDenied | Could not create the FileImport. |
| ConnectionNotFound | The given Connection could not be found. |
