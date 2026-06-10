---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/connections/get-configuration/"
title: "Get Configuration \u2022 API Reference"
---
# Get Configuration

## Endpoint

Retrieves the ConnectionConfiguration of the [Connection](/docs/foundry/data-connection/set-up-source/) itself.
This operation is intended for use when other Connection data is not required, providing a lighter-weight alternative to `getConnection` operation.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-connection-read`.

**operationId:** v2.getConfiguration

**path:** /api/v2/connectivity/connections/{connectionRid}/getConfiguration

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-connection-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Response

#### Body

**name:** ConnectionConfiguration

**example:** {"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| s3 | objectType | False | The configuration needed to connect to an [AWS S3 external system (or any other S3-like external systems that implement the s3a protocol)](/docs/foundry/available-connectors/amazon-s3/#amazon-s3). |
| rest | objectType | False | The configuration needed to connect to a [REST external system](/docs/foundry/available-connectors/rest-apis). |
| snowflake | objectType | False | The configuration needed to connect to a Snowflake database. |
| databricks | objectType | False | The configuration needed to connect to a [Databricks external system](/docs/foundry/available-connectors/databricks). Refer to the [official Databricks documentation](https://docs.databricks.com/aws/en/integrations/compute-details)  for more information on how to obtain connection details for your system. |
| smb | objectType | False |  |
| jdbc | objectType | False | The configuration needed to connect to an external system using the JDBC protocol. |

**example:** {"type":"jdbc","url":"jdbc:postgresql://localhost:5432/test","driverClass":"org.postgresql.Driver"}

### Error Responses

| name | description |
| --- | --- |
| ConnectionTypeNotSupported | The specified connection is not yet supported in the Platform API. |
| GetConfigurationPermissionDenied | Could not getConfiguration the Connection. |
| ConnectionNotFound | The given Connection could not be found. |
