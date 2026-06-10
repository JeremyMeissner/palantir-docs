---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/connections/get-configuration/"
parquet_url: "/foundry/api/v2/connectivity-v2-resources/connections/get-configuration/"
title: "Get Configuration"
fetched_at: "2026-05-12T19:34:37.676Z"
---
Get Configuration. Retrieves the ConnectionConfiguration of the Connection itself. This operation is intended for use when other Connection data is not required, providing a lighter-weight alternative to getConnection operation. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-connection-read. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). Response body. The configuration needed to connect to an AWS S3 external system (or any other S3-like external systems that implement the s3a protocol). The configuration needed to connect to a REST external system. The configuration needed to connect to a Snowflake database. The configuration needed to connect to a Databricks external system. Refer to the official Databricks documentation for more information on how to obtain connection details for your system. The configuration needed to connect to an external system using the JDBC protocol. Examples. Error responses.
